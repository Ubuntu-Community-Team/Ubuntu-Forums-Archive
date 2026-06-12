---
title: "Failed to start X server?"
date: 2007-01-10
forum: General Help
---

### Post by xkookooman on 2007-01-10
I was in the process of installing Beryl when I read that my graphics card had to be able to support 3D acceleration.  I put in the command and waited for a response to say yes. Instead my computer rebooted.  So I went and installed the xorg drivers and configured them. Another thing is I got all the files for beryl and emerald installed except for xserver-xgl.  Could this be the problem? 

So now everytime I reboot it goes to a blue screen that sayd "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem? " So then it gives me a report and then says that the Xserver is now disabled, and to restart GDM when it is configured correctly.  When I press ok it sends me to the terminal. 

How do I fix this? I can't even log into my account because it first boots into the error screen.

---

### Post by zerhacke on 2007-01-10
Please post the contents of your /etc/X11/Xorg.conf file.

---

### Post by pissedoffdude on 2007-01-10
when you get to the terminal type: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xkookooman on 2007-01-10
Alrite thx. Then is there a solution on how to install the xserver-xgl? I get an error every time saying that I can't install it.

---

### Post by r4ik on 2007-01-10
> **xkookooman said:**
> Alrite thx. Then is there a solution on how to install the xserver-xgl? I get an error every time saying that I can't install it.

This might help,

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

From,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper).

Good luck !

---

### Post by xkookooman on 2007-01-13
so i tried to reconfigure but it ends up giving me the failed message again.  Is there any way to get by this? Also, after install beryl, I try to log in with the XGL session, but all it gives me is a grey screen with a bunch of Xs and it says it couldnt load..

---

