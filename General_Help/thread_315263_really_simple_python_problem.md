---
title: "really simple python problem"
date: 2006-12-08
forum: General Help
---

### Post by ryland22 on 2006-12-08
I can run a python script from this folder:
/home/username/Desktop/mjt_cron/email2.py

using the following command:
$ python2.4 /home/username/Desktop/mjt_cron/email2.py 

However, if I copy that exact file and put it in this folder:
/var/www/apache2-default/mjt_cron/email2.py

using the following command:
$ python2.4 /var/www/apache2-default/mjt_cron/email2.py 

then I get the following errors:

Traceback (most recent call last):
  File "/var/www/apache2-default/mjt_cron/email2.py", line 1, in ?
    import smtplib
  File "/usr/lib/python2.4/smtplib.py", line 49, in ?
    from email.base64MIME import encode as encode_base64
  File "/var/www/apache2-default/mjt_cron/email.py", line 2, in ?
    from email.MIMEMultipart import MIMEMultipart

I'm sure this is something really simple - can anyone advise???

---

### Post by jpkotta on 2006-12-09
I'll bet it's the permissions of the directory.  Maybe.

What's the difference between ```
ls -ld /var/www/apache2-default/mjt_cron/
```and```
ls -ld /home/username/Desktop/mjt_cron/
```

---

### Post by ryland22 on 2006-12-09
Both of the parent folders (mjt_cron) have been chmod 777 - to allow for all permissions.

However, one difference is that the file owner of the folder in my local directory is the user, and the file owner of the apache directory is root.  Would this make any difference?

---

### Post by ryland22 on 2006-12-09
I just changed the owner and group of the apache2-default/mjt_cron directory to match that of the directory in home.

Ran email2.py and still getting same errors, so it appears the problem is not related to the owner of the directory.

---

### Post by studiesrule on 2006-12-09
I think there should be more to the error message then what you posted. It hasn't specified the error type.

---

### Post by ryland22 on 2006-12-09
Hey studiesrule - I'm posting everything from my shell:

ryland22@ubuntu-desktop:~$ python2.4 /var/www/apache2-default/mjt_cron/email2.pyTraceback (most recent call last):
  File "/var/www/apache2-default/mjt_cron/email2.py", line 1, in ?
    import smtplib
  File "/usr/lib/python2.4/smtplib.py", line 49, in ?
    from email.base64MIME import encode as encode_base64
  File "/var/www/apache2-default/mjt_cron/email.py", line 2, in ?
    from email.MIMEMultipart import MIMEMultipart
ImportError: No module named MIMEMultipart
ryland22@ubuntu-desktop:~$

---

### Post by ryland22 on 2006-12-09
It seems that python is not finding the path to it's modules when I run it from that other directory.  Can anyone help me out with programming that into my python script?

---

### Post by ryland22 on 2006-12-09
Figured it out - I found that if I renamed the file to something other than "email.py" that it worked fine.  Apparently there was some sort of naming issue with using email.py.

Whooo -

---

