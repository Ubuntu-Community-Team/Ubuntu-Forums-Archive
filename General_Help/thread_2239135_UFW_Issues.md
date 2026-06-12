---
title: "UFW Issues"
date: 2014-08-12
forum: General Help
---

### Post by iGavB on 2014-08-12
Hi all

I have a VPS which was started from scratch with just SSH installed. I have since updated, installed webmin, PHPMyadmin and LAMP.

I then installed UFW (apt-get install ufw)

Enabled port 22 (ufw enable 22)

Then tried to enable ufw, I get the below output and cannot start. Not only that but it crashed my entire VPS and I have to reboot it, then its fine, but UFW doesnt enable.

~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
ERROR: problem running ufw-init
iptables-restore: line 4 failed
iptables-restore: line 77 failed
iptables-restore: line 39 failed

Problem running '/etc/ufw/before.rules'
Problem running '/lib/ufw/user.rules'



Could someone please help :(

---

### Post by JetStorm on 2014-08-12
Have a look at this topic and try the offered solutions (especially the post about OpenVZ if your VPS is based on that):
[http://ubuntuforums.org/showthread.php?t=1660916](http://ubuntuforums.org/showthread.php?t=1660916)

---

### Post by iGavB on 2014-08-12
Ironically i had already gone through all of that, but none of it fixed this partciular issue (I did have other errors when enabling which the OpenVZ guide did fix)

---

### Post by JetStorm on 2014-08-12
It might be helpful if you paste the lines where the errors occur

---

### Post by iGavB on 2014-08-12
How do I get that for you (sorry I am really new to Linux servers, used to Windows personally)

---

### Post by JetStorm on 2014-08-12
They're mentioned in the error message:
/etc/ufw/before.rules
/lib/ufw/user.rules

btw, you might want to check for any sensitive data inside (like the public ip address of your server for example) before posting them here.

---

