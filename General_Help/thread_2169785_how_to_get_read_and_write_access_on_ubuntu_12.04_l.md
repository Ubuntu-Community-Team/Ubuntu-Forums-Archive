---
title: "how to get read and write access on ubuntu 12.04 lts directory to another user(ubilli"
date: 2013-08-23
forum: General Help
---

### Post by ubilli on 2013-08-23
please i am using ubuntu 12.04lts but the problem is that i just installed django but while working on a new project....
...........
settings.py
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# Django settings for firstblog project.


DEBUG = True
TEMPLATE_DEBUG = DEBUG


ADMINS = (
    # ('Your Name', 'your_email@example.com'),
)


MANAGERS = ADMINS


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.', # Add 'postgresql_psycopg2', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': '',                      # Or path to database file if using sqlite3.
        # The following settings are not used with sqlite3:
        'USER': '',
        'PASSWORD': '',
        'HOST': '',                      # Empty for localhost through domain sockets or '127.0.0.1' for localhost through TCP.
        'PORT': '',                      # Set to empty string for default.
    }
}
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


to this 


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# Django settings for firstblog project.


DEBUG = True
TEMPLATE_DEBUG = DEBUG


ADMINS = (
    # ('Your Name', 'your_email@example.com'),
)


MANAGERS = ADMINS


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.', # Add 'postgresql_psycopg2', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': 'firstblog',                      # Or path to database file if using sqlite3.
        # The following settings are not used with sqlite3:
        'USER': 'root',
        'PASSWORD': 'gooogle9',
        'HOST': 'localhost',                      # Empty for localhost through domain sockets or '127.0.0.1' for localhost through TCP.
        'PORT': '',                      # Set to empty string for default.
    }
}




****************************
it would not save i later found out that the problem is that it can not save for other users except root user.....so my question is that is there any software or how can i do it on the terminal that can make me give access to this folder


/first-blog on my system

---

### Post by ekhaat on 2013-08-23
I'm not sure, but from the top of my head I would say:

sudo gedit settings.py

Cheers

---

### Post by deadflowr on 2013-08-23
Is it absolutely paramount that the USER be root?

As your file states.

Is the file still usable if you change that ('USER':'root') to your username.

---

### Post by ubilli on 2013-08-24
please let me check guys on this thanks for the help i will look on it...

---

### Post by ubilli on 2013-08-24
Thanks for the help @ekhaat it worked the data saved like intended... and every hacker for helping me out....fanks a lot...

---

