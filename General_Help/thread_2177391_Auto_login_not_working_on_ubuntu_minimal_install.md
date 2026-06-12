---
title: "Auto login not working on ubuntu minimal install"
date: 2013-09-28
forum: General Help
---

### Post by Spacedementia87 on 2013-09-28
My second problem is auto login.
I have installed ubuntu precise using the minimal iso and then installed lightdm.
I then created a file /etc/lightdm/lightdm.conf and added this:
```
[SeatDefaults]
autologin-user=xbmc
autologin-user-timeout=0
user-session=XBMC
default-user=xbmc
default-user-timeout=0
pam-service=lightdm-autologin
greeter-session=lightdm-gtk-greeter
```
However on booting the machine I am still prompted for a password. Everything I read online tells me to tick the auto login box in the users menu. I can't though as I have no users menu or desktop to do that on. How can I make this stop asking me for a password?

---

### Post by ankspo71 on 2013-09-28
Hi, here is my unmodified /etc/lightdm/lightdm.conf that is set for autologin on Lubuntu 12.04

```

[SeatDefaults]
autologin-guest=false
autologin-user=james
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu

```

autologin-session=lightdm-autologin might be an important line missing from your config.

---

### Post by Spacedementia87 on 2013-09-28
Thanks for the response.

I have tried adding this line and still don't get any luck.

Could this be to do with the fact that "xbmc" is my only user and so is the "root" user?

---

### Post by ankspo71 on 2013-09-29
I found a few links that might help.

"Auto Login and start XBMC on startup"
[https://www.ghanima.net/doku.php?id=wiki:xbmcmacmini:autologin](https://www.ghanima.net/doku.php?id=wiki:xbmcmacmini:autologin)
Edit: It looks like the link is broken. To find the same link go to [https://www.ghanima.net/doku.php](https://www.ghanima.net/doku.php) and search for "xbmcmacmini"
OR Google cache of the above link:
[http://webcache.googleusercontent.com/search?q=cache:MYwW1ThhSzcJ:https://www.ghanima.net/doku.php%3Fid%3Dwiki:xbmcmacmini:autologin+&cd=8&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:MYwW1ThhSzcJ:https://www.ghanima.net/doku.php%3Fid%3Dwiki:xbmcmacmini:autologin+&cd=8&hl=en&ct=clnk&gl=us)

Other links:
[http://forums.fedoraforum.org/showthread.php?t=282987](http://forums.fedoraforum.org/showthread.php?t=282987)
[http://ben-tech.blogspot.com/2013/08/fedora-19-xbmc-autologin-in-xfce.html](http://ben-tech.blogspot.com/2013/08/fedora-19-xbmc-autologin-in-xfce.html) 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1036077](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1036077) (Ubuntu bug report)

---

### Post by Spacedementia87 on 2013-09-30
Hmm, didn't seem to be able to get any luck from there.

Here is my lightdm.log for this boot.  Anything in there look useful?

[http://pastebin.com/D2MxsFGe](http://pastebin.com/D2MxsFGe)

---

### Post by ankspo71 on 2013-10-02
Have you tried XBMCbuntu (an Xbmc live-cd based on Ubuntu), and have you tried enabling automatic login in the XBMCbuntu intstaller? If autologin works there, you could borrow the lightdm.conf file from it. That might also be a better alternative to building your own lightweight XBMC custom distro. Here is the info and download link [http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu) . On the download page, be sure to click on the XBMCbuntu icon and not the Linux icon. 

I'm not sure what is happening with your lightdm autologin problem, to be honest. I looked over alot of information on the internet and haven't come up with anything much different. I do have some info that might help though:

> Could this be to do with the fact that "xbmc" is my only user and so is the "root" user? 
I don't think that would be a problem. I'm pretty sure any type of account should be able to login when autologin is enabled.

> Everything I read online tells me to tick the auto login box in the users menu. 
I just found command to enable autologin in lightdm:
sudo /usr/lib/lightdm/lightdm-set-defaults --autologin username
source: [http://askubuntu.com/questions/51086/how-do-i-enable-auto-login-in-lightdm](http://askubuntu.com/questions/51086/how-do-i-enable-auto-login-in-lightdm)

> Here is my lightdm.log for this boot. Anything in there look useful?
The closest report I could find is this link [http://ubuntuforums.org/showthread.php?t=2061845](http://ubuntuforums.org/showthread.php?t=2061845) , but that person couldn't log in at all into the user account which was caused by a permission problems with the .Xauthority file, so I don't think it would help. Your lightdm.log doesn't appear to say anything very useful except that it tried to login to the desktop, but it stoped and returned to the login window.

Some people switch display managers when they can't get autologin to work. To do that they would install another display manager then run the command 'sudo dpkg-reconfigure lightdm' and choose the default display manager to use like it says here: [http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by Spacedementia87 on 2013-10-03
Thank you for the response. Unfortunately xbmcbuntu won't install. I have tried in the past and it always gets stuck. Not sure why. Besides I get very stuttery video unless I install the xvba version of xbmc.

I will try installing another dm. What would you recommend? Gdm?

---

### Post by ibjsb4 on 2013-10-03
What about not using a DM?  Just use startx if your going for minimal.

---

### Post by steeldriver on 2013-10-03
I wonder if it's a regression of this --> [http://forum.xbmc.org/showthread.php?tid=128861](http://forum.xbmc.org/showthread.php?tid=128861)

> this is a bug in lightdm. log out once manually and select the xbmc  session at the login screen. After that it should store it as default. 			

---

### Post by Spacedementia87 on 2013-10-04
Ok, I will give that a go. Never used it before so will have to do some research. 


Last night I tried installing gdm and using that. However after installing and doing dpkg-reconfigure gdm I rebooted and the guy never loaded. Just stayed on a screen saying checking battery state.
Why is this?

EDIT: I have looked into startx think it is was beyond me. No idea how to set it up.

---

### Post by Spacedementia87 on 2013-10-05
Right I think I have had a breakthrough.

I have managed to get it so that lightdm no longer asks for my password.

However there is still an issue.

After booting up the computer the login screen is still displayed.  If I click log in then the screen flashes black and I am returned to the login screen.

However tying ```
sudo service lightdm restart
``` causes xbmc to auto login.  So progress.  However this means I need to restart lightdm every time i boot up which is not ideal.

I have tried the fixes listed here already:
[http://askubuntu.com/questions/129246/after-12-04-upgrade-cant-log-in-although-password-is-correct](http://askubuntu.com/questions/129246/after-12-04-upgrade-cant-log-in-although-password-is-correct)

---

### Post by jewisharific on 2013-10-27
I recommend using **nodm** for autologin, instead of **lightdm**.

---

