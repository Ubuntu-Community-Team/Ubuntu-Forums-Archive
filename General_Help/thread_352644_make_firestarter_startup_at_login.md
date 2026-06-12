---
title: "make firestarter startup at login"
date: 2007-02-03
forum: General Help
---

### Post by fouadk on 2007-02-03
i want to start firestarter when i log in so i added it in System\Preferences\Sessions under the startup programs tab but the problem is that firestarter needs administration privileges but sudo and gksudo doesnt resolve the problem....

please help....
Thanks in advance

---

### Post by r4ik on 2007-02-03
You can put a reference to it from within your startup sessions tab. Go here: System > Preferences > Sessions, click Startup Programs, Add, type in gksu firestarter, click OK, close Sessions. Log out, log back in.

Good luck !

---

### Post by yabbadabbadont on 2007-02-03
If you are just worried about having an active firewall when you login, then you don't need to start the firestarter GUI.  Once firestarter is installed and configured, a startup script is run automatically at boot that configures iptables (the real linux firewall) appropriately.  The GUI is just for viewing events/logs and making changes to the configuration.

---

### Post by fouadk on 2007-02-03
Thanks alot for the quick reply and help

about the gksu thing...that didnt work coz it asks for a password

about when firestarter start it automatically protects me...thanks alot for the info, its all what i needed coz i wanted to start firestarter for protection but it seems that it does that automaticaly

thnaks alot

---

### Post by r4ik on 2007-02-03
> **fouadk said:**
> Thanks alot for the quick reply and help

about the gksu thing...that didnt work coz it asks for a password

about when firestarter start it automatically protects me...thanks alot for the info, its all what i needed coz i wanted to start firestarter for protection but it seems that it does that automaticaly

thnaks alot

Have you entered you're passwrd ?

---

### Post by laychie on 2007-02-24
hi i have the same problems and everytime i tried to edit the sudoers file it tells me that i dont have permission and that file i was trying to edit has a read only attribute... i mean, i am completely lost because i am the root and still it wont let me! :confused: help pls....

---

### Post by Maestro23 on 2007-02-24
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

