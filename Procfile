import sys
import os

# Add your project directory to the sys.path
# Replace 'yourusername' with your actual PythonAnywhere username
# Replace 'YIT_Moodibidri_Deploy_FlaskApp_2025' with your actual project folder name
project_home = '/home/yourusername/YIT_Moodibidri_Deploy_FlaskApp_2025'
if project_home not in sys.path:
    sys.path = [project_home] + sys.path

# Set environment variables if needed
os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'  # Remove this line if not using Django
os.environ.setdefault('FLASK_ENV', 'production')

# Option 1: If your main Flask app is in app.py
try:
    from app import app as application
except ImportError:
    # Option 2: If your main Flask app is in run.py
    try:
        from run import app as application
    except ImportError:
        # Option 3: If your Flask app is in main.py
        try:
            from main import app as application
        except ImportError:
            # Option 4: If your Flask app is in a package structure
            try:
                from myapp import create_app
                application = create_app()
            except ImportError:
                # Option 5: If your Flask app variable is named differently
                try:
                    from app import create_app
                    application = create_app()
                except ImportError:
                    # Option 6: Generic Flask app import
                    from flask import Flask
                    application = Flask(__name__)

                    @application.route('/')
                    def hello_world():
                        return '<h1>Hello from PythonAnywhere!</h1><p>Please check your Flask app import in wsgi.py</p>'

# Debugging: uncomment the following lines if you're having import issues
# print("Python path:", sys.path, file=sys.stderr)
# print("Current working directory:", os.getcwd(), file=sys.stderr)
# print("Files in project directory:", os.listdir(project_home), file=sys.stderr)

if __name__ == "__main__":
    application.run()
