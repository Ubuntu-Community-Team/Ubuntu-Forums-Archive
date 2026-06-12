---
title: "Disable Stupid Hard Drive Check"
date: 2013-01-20
forum: General Help
---

### Post by Spirrwell on 2013-01-20
Sorry if I go off on a rant or I sound really pissed off, but because of this stupid little popup that keeps saying my hard drive is bad, it crashed my game of TF2.

I know one of my hard drives is bad, I've examined it, cancelled it, okayed it, but the stupid popup keeps bugging me and I want it OFF. I can't replace the drive right now, I have no replacement for it, and it's got my boot sector on it so if I have to replace it I have to go through a bunch of crap to get my Windows loader working and reinstalling GRUB as I'm dualbooting.

It keeps forcing itself forward and so when I was playing my game of TF2 it kept minimizing my game until it crashed it, it's driving me insane. And maybe it wouldn't be so bad except that when the popup starts it either creates like 10 instances on top of each other or it's designed for me to have to hit cancel that many times before it will leave me alone for a little while.

Just AGH, how do I disable it?

---

### Post by coldcritter64 on 2013-01-20
The inconvenience of losing your TF2 game is actually designed to save your Ubuntu and Windows installations and your data, it really is not a "stupid" check. I am aware of your frustration, and also note because of it you haven't supplied much information. You don't tell us what OS flavour (eg. Kubuntu, Ubuntu or Xubuntu) or release of such you are using eg 10.04, 12.04 etc.

[s]I'll assume 12.04 unity DE as is the "standard" release. Go to the power button on the top unity panel, select "Startup Applications". Look for an entry there like "Disk Notifications", if you see it ticked, detick it. After a logout / login the disk notifications daemon should no longer be running and give those (IMPORTANT) warnings. Turn it off at your own risk, it is possible to lose the complete drive and both Ubuntu and Windows and all your saved data.[/s] 

I hope you have very good off drive data backups doing this. Good Luck.

Edit: on rereading, if you are getting a heap of notifications at once, the S.M.A.R.T data on your hardware must be reporting a serious failure situation. Backup urgently by the sounds of it. That indicates a failing drive.

Edit 2: Seems there is no startup applications entry in 12.04, just booted into it here OP, **the above info appears wrong now** further checking here required.

Edit 3: /etc/xdg/autostart/gdu-notification-daemon.desktop now controls the gnome disk utility notification daemon process. I just moved it to the desktop here (sudo mv command) logged out/logged in, and the daemon was not running anymore. Reversed the move command, logged out / logged in, and the daemon was back working. You may be able to use this as a means of  turning off the alerts.

---

### Post by Spirrwell on 2013-01-20
I knew somebody was going to say something about not supplying information after I posted this :p. Anyway thank you, it appears to be working as in not showing up anymore. I did actually use Ubuntu as the thread prefix, and I figured it'd be obvious that I was using either 12.04 or 12.10 since I'm up with the recent port of Steam\TF2 to Linux. Oh well, my problem is solved, thank you.

I know it's a "serious" failure, I have everything backed up, I'm just going to use it until it completely dies, because all of my boot information is on it and I don't feel like going through all the steps to get the Windows Loader with GRUB working on another hard drive, let alone the fact I don't have a replacement now.

---

### Post by The Spectre on 2013-01-20
> **Spirrwell said:**
> I know it's a "serious" failure, I have everything backed up, I'm just going to use it until it completely dies, because all of my boot information is on it and I don't feel like going through all the steps to get the Windows Loader with GRUB working on another hard drive, let alone the fact I don't have a replacement now.

It could save you a tremendous amount of time if you get your replacement Hard Drive now and just Clone your old Hard Drive to the new Hard Drive before it fails.

Redo Backup & Recovery
[http://redobackup.org/](http://redobackup.org/)

Clonezilla
[http://clonezilla.org/](http://clonezilla.org/)

---

