---
title: "Python and scripts in /usr/local/bin"
date: 2007-10-09
forum: General Help
---

### Post by aek82 on 2007-10-09
Whenever I try to execute a python script that is located in the /usr/local/bin, python gives me the error 'python: can't open file 'django-admin.py': [Errno 2] No such file or directory'. 

I've set the permissions on the file to a+x and i've sent the owner:group to my user. I also know the '/usr/local/bin' directory is in my $PATH variable. 

Any ideas why this is happening?

Thanks,

Alex

---

### Post by cwaldbieser on 2007-10-10
> **aek82 said:**
> Whenever I try to execute a python script that is located in the /usr/local/bin, python gives me the error 'python: can't open file 'django-admin.py': [Errno 2] No such file or directory'. 

I've set the permissions on the file to a+x and i've sent the owner:group to my user. I also know the '/usr/local/bin' directory is in my $PATH variable. 

Any ideas why this is happening?

Thanks,

Alex

How are you trying to invoke the script?  What does the shebang line look like?

---

### Post by aek82 on 2007-10-12
I am invoking the script by typing:

python django-admin.py <args>

---

### Post by cwaldbieser on 2007-10-13
> **aek82 said:**
> I am invoking the script by typing:

python django-admin.py <args>

Well, the problem is likely that "django-admin.py" is not in your current directory.  The python interpreter is not going to search your shell PATH looking for that file.  Also, it doesn't search the PYTHONPATH (that is only used for importing modules).  You need to give it the full path to the script:
```

$ python /usr/local/bin/django-admin.py

```

Alternatively, if the first line of the script is
```

#! /usr/bin/python

```
and the script is exectable and in your command PATH, then you can just type in the script name.  Your shell will find the file in the command PATH, and it looks at the first line and runs the python interpreter for you.

Does that make sense?

---

### Post by aek82 on 2007-10-19
yea, that makes sense. Thanks for your help.

---

