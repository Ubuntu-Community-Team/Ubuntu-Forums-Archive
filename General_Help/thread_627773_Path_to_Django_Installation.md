---
title: "Path to Django Installation"
date: 2007-11-30
forum: General Help
---

### Post by ichbindev on 2007-11-30
When one installs Django in Ubuntu using apt-get install python-django, where is the django bin directory? In other words, what is the location of Django on Ubuntu?

---

### Post by ichbindev on 2007-11-30
I was actually trying to run django-admin.py by doing the following:

```
django-admin.py startproject mynewprj
```

But got an error: command not found. I was looking for possible reasons.

1. Path to Django was not in the environment PATH
2. Django wasn't installed properly

This is why I asked the previous question. I thought I needed to enter the path for Django in the PATH. But the solution was to remove .py and instead do

```
django-admin startproject mynewproj
```

Result: Problem Solved.

---

### Post by ichbindev on 2008-03-17
It has taken a long time but finally I found an answer. When Django is installed in Ubuntu using aptitude or apt-get, it is installed in /var/lib/python-support/python2.5/django

---

