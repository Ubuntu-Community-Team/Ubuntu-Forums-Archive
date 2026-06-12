---
title: "X11VNC Server on power-on...?"
date: 2013-09-16
forum: General Help
---

### Post by RallyDarkstrike on 2013-09-16
Hi all,

Just a quick question about X11VNC - most of my machines here at home are Windows machines, which I have set up to use VNC servers for remote desktop. They're all currently set so the VNC service starts before the user logs in.

Now....I have X11VNC Server set up on my netbook (running Linux Mint 14) and an older machine I have Xubuntu 12.04 installed on. It is working great on both, however, because of the way Linux works by default, I cannot connect to the VNC server unless the user is already logged in. This is an issue when I need to restart the machines remotely for whatever reason or if the power were to go out and the machines restarted...I can't log in remotely until I or somebody else was physically there to log on to the machine FROM the machine.

I've looked this up on Google and I've tried but found no methods that have worked exactly for me yet. Is there a way to set up X11VNC to start as a system service BEFORE User Login (and still use the password I have set for the VNC server...?)

Thanks for any help! :)

---

### Post by dcstar on 2013-09-17
[URL="http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/"]http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/
[/URL]
I also use the **xrdp** package so Windows Remote Desktop can be used to access Linux.

---

### Post by RallyDarkstrike on 2013-09-18
Thanks, those instructions seemingly did the trick! I had actually tried using them before, but noticed this time around that I had made one TINY mistake last time that must've prevented from working!

A humble thanks for your help :)

---

