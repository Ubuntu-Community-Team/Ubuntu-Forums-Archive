---
title: "First logging always detects (incorrectly) battery power"
date: 2004-11-23
forum: General Help
---

### Post by carvalho on 2004-11-23
Hi, 

I installed ubuntu to an Inspiron 1000 laptop (and ended with a nice all catalan desktop for my mom, that does not speak english; thanks to all the translators!!). Everything seem to work sort of OK. I even managed with the modem (slmdm following a nice how-to).
 
The main problem is that when I start the computer (plugged) and login for the first time as a user, laptop mode is on and gnome thinks that its running with battery power. If I log out and in again through gdm, laptop mode is disabled and the applet recognizes correctly that we are plugged in. 

Any ideas?

Has this anything to do with a passwordless login? do we need the su to start some power monitoring daemon? (but acpi -V gives a correct output from the begining....)

I run Debian in my own laptop and use the laptop-mode-tools package, that interacts well with acpi or apm, but I don't find the package for ubuntu (and I don't know if that would help with part of the problem). 

Thanks a lot for any help!
Joan

---

### Post by carvalho on 2004-11-23
OK, I figured out that (re?)starting acpid (sudo /etc/init.d/acpid restart) does the trick. The computer figures out the power state correctly. 
So when I log in as the regular user acpid does not start? 

Anyway I can run the acpid script at boot time?  

thanks

---

