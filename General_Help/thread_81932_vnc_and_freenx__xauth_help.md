---
title: "vnc and freenx  xauth help"
date: 2005-10-25
forum: General Help
---

### Post by elj4176 on 2005-10-25
Hello all! I'm a noob so please take it easy ;)


I installed Ubuntu about 6 months ago and have since upgraded the distro using aptitude. So does that mean I'm running the newest version (Badger?)? Any way to tell?

Here's my problem right now: I was able to use VNC to log into my Ubuntu box from work. I can use Putty too. I was trying to setup freenx and couldn't get it working. It would connect and authenticate and give me a blank xwindows screen if I used the default script or console. If I used the custom and had it execute blackbox (my wm of choice) the !M would come up and then it would exit. I tried a variety of commands I found online here and there but nothing seems to have worked.
Now I cannot even get vnc to work. I get an error that says xauth is not found in the path. I did echo $PATH and it looks like the dir for xauth is in there.
Kinda a rambling but it seems I have messed someting up that a far more experience Ubuntu'er could fix in a snap.
Any help is appreciated!
Thanks!

---

### Post by elj4176 on 2005-10-26
Ok - maybe this will get a reply? Here is a snippit of my ssh session that shows what I'm seeing:
---------------------------
Linux ubuntu 2.6.10-5-386 #1 Tue Jun 7 08:26:42 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Wed Oct 26 11:16:23 2005
ejohnson@ubuntu:~$ echo $PATH
/usr/bin/X11R6:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
ejohnson@ubuntu:~$ sudo vncserver
Password:
vncserver: couldn't find "xauth" on your PATH.
ejohnson@ubuntu:~$ whereis xauth
xauth: /usr/bin/xauth /usr/X11R6/bin/xauth /usr/bin/X11/xauth /usr/local/bin/xauth
ejohnson@ubuntu:~$ whereis vncserver
vncserver: /usr/bin/vncserver /usr/share/vncserver /usr/share/man/man1/vncserver.1.gz
ejohnson@ubuntu:~$
-------------------------------------
What do I need to do here? I edited my PATH in /etc/profile  and this is what I get. If I can get freenx working then I don't need VNC but I would like to have the option of using either one. My freenx problem seems ot be version related. Version 1.5 trying to connect to nxproxy 1.4 or something along those lines.
Anybody? Bueller? Bueller?
Thanks!

---

### Post by bugmenot on 2005-10-30
i think xauth issues were aused by the transition from xfree86 to x.org.
and there's a solution for it with respect to freenx on the wiki.

---

### Post by malaprohibita on 2006-03-06
[QUOTE=bugmenot]i think xauth issues were aused by the transition from xfree86 to x.org.
and there's a solution for it with respect to freenx on the wiki.[/QUOTE]

Adding a link to the wiki, as well as referencing exactly which wiki, would be extremely beneficial.  ;)

---

