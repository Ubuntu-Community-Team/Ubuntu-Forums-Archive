---
title: "[lubuntu 14.10] Remote Desktop Connection issues"
date: 2014-12-13
forum: General Help
---

### Post by jim1944 on 2014-12-13
I have things set up so that I can remote desktop from my Windows 7 Pro machine to my Lubuntu 14.10 machine using either Real VNC or the Remote Desktop Connection that come with Windows 7 Pro but there are a couple of issues:

1. I have to start vino-server manually in order to use Real VNC. Everything I can find that explains how to get it to automatically start at boot up or login refers to menu items that don't exist (or I can't find) in Lubuntu 14.10. How do you get it to start automatically in Lubuntu 14.10?

2. I have to apply the work around to bug 1281250 (turn off encryption) to get Real VNC (using Real VNC Viewer 5.2.2 that I got here: [http://www.realvnc.com/download/viewer/](http://www.realvnc.com/download/viewer/)) to work. This is now Gnome/Vino bug 728267. First, how can I get myself notified when the bug is fixed? Second, is this considered a bug in Vino or a bug in all the viewers that haven't upgraded to the latest encryption?

3. In order to get a desktop to come up in Windows' Remote Desktop Connection I had to get/install lxde-common. The result is that, in Remote Desktop Connection, I get an LXDE desktop rather than the "normal" Lubuntu desktop. Is there a way to get the normal Lubuntu desktop?

Thanks
Jim

---

### Post by john364 on 2015-02-14
I don&#8217;t use remote desktop. But VNC and Lubuntu 14.10
You need you Lubuntu machine to autologin.
 
Install x11vnc.
Run it x11vnc (not as root)  create a password file by: -  x11vnc &#8211;storepasswd ( there are other password options)
Then I prefer to use the gui to do the next bit.

By gksudo pcmanfm
Then goto your home directory
Unhide hidden files CLTR+H go to .config
Make a new new autostart
In the new dir make a file myvncserver.desktop needs to be executed by everyone.

Or do it in the terminal 
sudo pico ~/.config/autostart/myvncserver.desktop [Desktop Entry]

Encoding=UTF-8

Version=0.9.4

Type=Application

Name=VNC server name what ever the hell you want to call it

Comment=

Exec=**x11vnc -xkb -usepw -display :0 -forever -shared** 

StartupNotify=false

Terminal=false

Hidden=false 
The options in **Bold** can be changed need to look at the x11vnc documentation 
Reboot and VNC should work and ask for a password.

---

