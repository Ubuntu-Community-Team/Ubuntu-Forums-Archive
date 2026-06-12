---
title: "Blank screen after laptop's lid was reopend. (Battery)"
date: 2015-07-20
forum: General Help
---

### Post by Ricial on 2015-07-20
The problem is, every time I reopen my laptop's lid after it was closed/flipped I always end up having a **Blank Screen**. It stays unresponsive and it leaves me no choice to press the power button to turn my laptop OFF. 

This issue is only present when I'm on **BATTERY**. Both the BATTERY and AC power settings have similar configuration. 

I really like Xubuntu and I don't want to switch to another distro again.

Here are the screen shots from my current power settings.
I'm using **Xubuntu 14.04.2 LTS 32bit**

[IMG]http://i.imgur.com/UNqSGYc.png[/IMG]

[IMG]http://i.imgur.com/Ah6VDJV.png[/IMG]

[IMG]http://i.imgur.com/zw451hZ.png[/IMG]

---

### Post by kerry_s on 2015-07-20
enable light-locker should be on. just turn the stuff to never. the reason being is it still needs to set the setting or defaults will be used.

there should be a setting for "handle display power management" make sure it's checked in xfce power manager.

---

### Post by Ricial on 2015-07-20
> enable light-locker should be on. just turn the stuff to never. the  reason being is it still needs to set the setting or defaults will be  used.

1. Switching Light Locker to **ON **does fine, except that it did **not Lock **the laptop and it goes right through the Desktop without asking for login.

2. I then toggled **Lock on Suspend **to **ON** and it did suspend and at the same time **Locked **the laptop. But right after I login, the screen flickers and it then goes blank again.

I followed the command from this [link]("http://ubuntuforums.org/showthread.php?t=2238547") which serves as a **temporary** solution for this problem.
```
sudo service lightdm restart
```

Based on my google searches this bug was present way back 14.04..01. The logs makes no sense to me because I have no prior experience in deciphering a bug's description/details. 
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736) 
[*][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1357090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1357090) 
[*][http://xubuntu.org/news/laptop-users-fix-available-for-the-black-screen-on-unlock-bug/](http://xubuntu.org/news/laptop-users-fix-available-for-the-black-screen-on-unlock-bug/) 
[*][http://askubuntu.com/questions/450706/have-to-restart-lightdm-when-opening-laptop-lid-after-14-04-upgrade](http://askubuntu.com/questions/450706/have-to-restart-lightdm-when-opening-laptop-lid-after-14-04-upgrade) 
[/LIST]

---

### Post by kerry_s on 2015-07-20
you should try 15.04, it's not long term, but a lot of new features & much more stable.

i'm not currently on xubuntu right now, i'm making a 64bit debian testing net installer with firmware for a friend of mine. the only way to test it was to install, so i'm on debian testing.

but the power manager in 15.04 looks the same.

---

