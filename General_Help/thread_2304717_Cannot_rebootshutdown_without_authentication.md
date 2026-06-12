---
title: "Cannot reboot/shutdown without authentication"
date: 2015-11-29
forum: General Help
---

### Post by danzax69 on 2015-11-29
I have installed ubudu minimal 15.10 and I'm using XFCE as desktop enviroment(I've installed xfce and xfce-goodies packages). The problem is that I have problems with permissions. I cannot reboot or shutdown the machine without authentication. Also I cannot add or edit connections from "Network connections", all input texts and buttons are inactive(this is a different problem but maybe is related). 
I can reboot via "systemctl reboot" from tty without authentication, but not from terminal inside X. I tried to add this file :
/etc/polkit-1/localauthority/50-local.d/allow_all_users_to_shutdown_reboot_suspend.pkla
as suggested here:
[http://askubuntu.com/questions/1190/how-can-i-make-shutdown-not-require-admin-password](http://askubuntu.com/questions/1190/how-can-i-make-shutdown-not-require-admin-password)
but it seems that is ignored because I still get the polkit authorisation message when try to reboot/shutdown.
Please help me to fix this problem.
thanks

---

### Post by Bucky Ball on 2015-11-29
*Thread moved to **General Help**.*

Welcome. Did you install a display manager? Lightdm, gdm, xdm? Have you got xfwm4 installed? xfce4-goodies is just desktop enhancements. Doesn't do anything much for the system so probably not part of this.

As you've done a minimal install, before hacking code and tweaking which may cause unrelated issues, it would be good to know what you included in your initial install line at the first boot. You may just be missing something (and what you're describing suggests this). Presumably, you did:

```
sudo apt-get install xfce4 xfce4-goodies
```

What else?

I only use minimal installs and sometimes they can take a little bit to get running smoothly and it is often the addition of a missing bit or piece which fixes things.

PS: I use network-manager-gnome for network. You might check you have that installed. Bear in mind that you only have the kernel and xfce4. xfce4 is just a desktop environment and won't drag in a lot of things you'd probably consider essential. A file manager and a few of other things is about it. You need to install pretty much anything else you want to use. The minimal is a steep learning curve if you're new to Ubuntu, but a worthwhile one if you have the time and inclination. ;)

---

### Post by danzax69 on 2015-11-29
I installed only the base system from minimal install and after that I installed mc, xorg xfce4 and xfce4 goodies. After that I tried to run xfce and I get an error about authentication. I couldn't login as normal user, so I run it as root via "sudo startxfce4". This worked but it changed some of my user's folders owner to root. After I change them all again to my user' s name I've managed to login as normal user via "startxfce4'. But now I have this problem I described. I did the same before some months with arch and after with manjaro from basic system and also before some days with debian minimal, but I never had these problems with xfce there. I know that I must install everything I need but this is why I chose the minimal install.

---

### Post by Bucky Ball on 2015-11-29
Okay. You need to install a desktop manager and the window manager in case xfce4 didn't drag that in (but I think it would).

There are a few desktop managers to choose from. I use lightdm. As mentioned, there are others (gdm, xdm are ones I've used). This should give you a log in screen that works. Hopefully.

```
sudo apt-get install lightdm xfwm4
```

You can change the DM later. xfwm4 is the windows manager. You may get a 'newest version already installed' for that. Ignore.

---

### Post by danzax69 on 2015-11-30
Thanks, but I don't want a desktop manager. This is one of the reasons I chose the minimal install. I installed xdm though and seems that it takes care of authorization. But xdm doesn't support autologin and I don't want to install a desktop manager which need a lot of unnecessary(for me) dependencies. In fact this is the main reason I don't like ubuntu. For example I don't want the xfce-volumed package and so I removed it. But ubuntu now wants to autoremove all other packages from xfce-goodies because thinks that don't needed any more. Also, I wanted to install a more recent version of nvidia driver but it was impossible to do it from apt without to install a lot of unnecessary other packages included gnome-desktop. Why I have to install another desktop enviroment to install a driver? And the last time I used ubuntu and tried to remove plymouth it removed almost everything! 
So the problem isn't solved yet. How to correct these problems without the need to install a desktop manager?

---

### Post by danzax69 on 2015-11-30
I found a fix in xfce forums. 
I used the xinitrc from /etc/xdg/xfce4  directory and I disabled the olkit-gnome-authentication-agent from  autostart and I had to comment out the "AutostartCondition" line in  /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop file.  Then using startx to run xfce to problem solved. It doesn't work if I  start xfce with startxfce4 command though.

---

### Post by Bucky Ball on 2015-11-30
Sounds good. Please see the first link in my thread and enjoy. :)

---

