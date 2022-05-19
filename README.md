# Python - Django Blog


__Start the Django Project__

1. Run env virtualenv
2. py -m pip install Django
3. django-admin startproject __django_project__  #__django_project__ is the name of the project
4. cd __django_project__
5. python manage.py runserver   #Test the server
6. python manage.py startapp __app_name__  #__app_name__ is the name of the app

__Create a superuser__

1. python manage.py makemigrations #Detect changes and prepare migrations
2. python manage.py migrate
3. python manage.py createsuperuser

__Create a model__

1. define class Model
2. python manage.py makemigrations
3. python manage.py sqlmigrate __app_name__ __migration_number__
4. python manage.py migrate

__Register a model__
Register a model in the admin site
admin.site.register(__model_name__)

__Configure the Django Project__

1. add config file from apps.py of app to settings.py
     _blog.apps.BlogConfig_  => __BlogConfig__ is the _class_ in apps.py
2. add config file from urls.py of app to urls.py

__Create a template__

appname -> templates -> templates/appname -> HTML files

__User Authentication__
1. python manage.py startapp users
2.  add config file from apps.py of app to settings.py
     _users.apps.UsersConfig_  => __UsersConfig__ is the _class_ in apps.py

__Install the crispy form__

1. pip install django-crispy-forms
2. add crispy_forms to the INSTALLED_APPS in settings.py
3. add CRISPY_TEMPLATE_PACK = 'bootstrap3'
4. add  {% load crispy_forms_tags %} in the template
5. add format for form __{{ form|crispy }}__ in content form

__Set Login redirect__

LOGIN_REDIRECT_URL = 'blog-home'
LOGIN_URL = 'login'

__Install Pillow__

pip install Pillow

__Deploy the Django Blog__

1. pip install gunicorn
2. pip install django-heroku
3. touch Procfile -> _web: gunicorn __appname__.wsgi_ #django_blog
4. pip freeze > requirements.txt
5. add __import django_heroku to __settings.py__
6.  add __django_heroku.settings(locals())__ to __settings.py__
7.  Upload to github
8.  heroku login
9.  heroku create _appname_
10. heroku config:set DISABLE_COLLECTSTATIC=1
11. heroku config:set SECRET_KEY='key'
12. heroku config:set DEBUG_VALUE=True
13. heroku config:set EMAIL_USER='email'
14. heroku config:set EMAIL_PASS='pass'
15. heroku addons:create heroku-postgresql:hobby-dev
16. heroku pg 
17. git push heroku main(--your branch name)
18. heroku run python manage.py collectstatic
19. heroku run python manage.py migrate