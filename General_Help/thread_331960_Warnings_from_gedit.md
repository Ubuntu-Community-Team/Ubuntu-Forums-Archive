---
title: "Warnings from gedit"
date: 2007-01-05
forum: General Help
---

### Post by yuliang on 2007-01-05
yuliang@thinkpad:/etc$ sudo gedit

(gedit:9159): Gdk-WARNING **: locale not supported by Xlib

(gedit:9159): Gdk-WARNING **: cannot set locale modifiers
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4


(scim-panel-gtk:9165): Gdk-WARNING **: locale not supported by Xlib

(scim-panel-gtk:9165): Gdk-WARNING **: cannot set locale modifiers
:confused: :confused: :confused:

---

### Post by meng on 2007-01-05
Does it work though? or does it not start?
Anyway, you should use gksu instead of sudo for starting a graphical application.
e.g.
gksu gedit

---

### Post by yuliang on 2007-01-05
It works despite of the warnings. *gksu gedit* yields the same warnings.

---

### Post by meng on 2007-01-05
It may not be compatible with one of the language encodings you have specified for your system. Could you show us
cat /etc/locales.conf
EDIT: No I don't think that will work, hmmm, maybe:
sudo dpkg-reconfigure locales

---

### Post by yuliang on 2007-01-05
[I]yuliang@thinkpad:/$ cat etc/locales.conf
cat: etc/locales.conf: No such file or directory[/I]

and the command

*sudo dpkg-reconfigure locales*

went through but hadn't solve the problem.

---

### Post by meng on 2007-01-05
What languages have you got installed on this system? I'm not sure it IS a problem, it's just giving you a warning but it's still working.

---

### Post by yuliang on 2007-01-05
English and Chinese

---

### Post by meng on 2007-01-05
I suspect gedit is just telling you that it can't handle Chinese. So there's no problem!

---

