---
title: "Need Some Urgent Help."
date: 2006-07-12
forum: General Help
---

### Post by RajivNair on 2006-07-12
I just installed the latest graphics driver for intel ie intel i810 driver frm [http://dri.freedesktop.org](http://dri.freedesktop.org), but now im unable to login,as i enter my user name and password, the boot splash screen starts and bfore it has completely loaded i get back to the login screen.Can anyone help me get out of this mess.

---

### Post by Paerez on 2006-07-12
if you are given a text login screen, login and type this:
```
# sudo /etc/init.d/gdm restart
```
please post the output of that. Also type this:
```
# cat /var/log/Xorg.0.log | grep EE
```
and post that output.

---

