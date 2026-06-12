---
title: "Ubuntu desktop freezing after login"
date: 2015-07-04
forum: General Help
---

### Post by dani-valverde on 2015-07-04
Hello,
I've just installed Ubuntu 14.04 LTS server. I have installed its desktop as well, but it freezes just after login. I've tried the procedure described here [http://sourcedigit.com/13322-fix-unity-freezes-login-ubuntu-14-10-utopic-unicorn/](http://sourcedigit.com/13322-fix-unity-freezes-login-ubuntu-14-10-utopic-unicorn/) but it hasn't solved the problem. Can anyone help?
Thanks!

Dani

---

### Post by cariboo on 2015-07-04
If you remove Unity, does it still freeze up?

---

### Post by dani-valverde on 2015-07-05
Thanks for replying cariboo. It seems there is some bug in Ubuntu 14.04 that causes freezing in some systems. Now I am updating to 15 to see if it's gone. 
Cheers! 

Dani

Hello Cariboo,
I've just upgraded to 15 and I still have the same problem. I will remove unity and see what happens.

Dani

I've run out of ideas. I've removed Unity and updated my Nvidia card drivers using ```
sudo apt-get install nvidia-current
```. Can anyone help?

---

### Post by howefield on 2015-07-05
Have you browsed the logs for clues, eg dmesg, syslog ect ?

```
tail -f /var/log/syslog
```

---

### Post by dani-valverde on 2015-07-05
Thanks howefiled, I'm not that wise! Here's the output of the suggested command:
```
Jul  5 14:04:12 acroserver gnome-session[1378]: (nm-applet:1550): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Jul  5 14:06:22 acroserver acpid: client 982[0:0] has disconnected
Jul  5 14:06:35 acroserver systemd[1]: Started Session c3 of user acrocephalus.
Jul  5 14:06:35 acroserver systemd[1]: Starting Session c3 of user acrocephalus.
Jul  5 14:09:04 acroserver acpid: client connected from 982[0:0]
Jul  5 14:09:04 acroserver acpid: 1 client rule loaded
Jul  5 14:09:10 acroserver acpid: client 982[0:0] has disconnected
Jul  5 14:10:11 acroserver acpid: client connected from 982[0:0]
Jul  5 14:10:11 acroserver acpid: 1 client rule loaded
Jul  5 14:10:32 acroserver acpid: client 982[0:0] has disconnected
```
Does it give you any clue on where the problem is?

---

