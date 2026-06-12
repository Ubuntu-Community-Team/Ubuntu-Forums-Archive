---
title: "I can't get into the GUI !!!"
date: 2006-11-14
forum: General Help
---

### Post by TheMatt on 2006-11-14
For some reason, I can't get into the GUI now. All it will do is boot into recovery mode and the terminal. I tried every kernel I have installed, and the same thing happens with all of them. 
 
I have no idea what to do. All I was doing was switching the video card driver with a different one, since I suspect I had the wrong one. I didn't stop x.org though, because I couldn't figgure out how, and I did it wothout doing so before. Then it sort of logged me out, and just went to this screen where there was a propmt, but nothing was there, and it wasn't doing anything, so I shut it down by pushing the power button. 
 
It showed the shuting down screen like it usually does when I shut down. When I booted back up, I selected the K7 Kernel like I usually did, but after the normal loading screen, it went into the terminal like it does in recovery mode. So I rebooted, thinking I pressed recovery mode by accident. But I noticed that it used the progress bar durring the loading screen. When I booted back up, I made sure to select the normal kernel, and it did the same thing. I rebooted again, and tried the recovery mode, but that did the same thing, except that it didn't show the progress bar. I tried the 386 kernel, but that did the same thing. I have no idea what to do, so I am asking for help. Is this a bug in Edgy mabye?
 
I would really appreciate any help on this. Thanks a lot!
 
:confused: :-k ](*,)

---

### Post by aysiu on 2006-11-14
Does this help at all?
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by igknighted on 2006-11-14
What kind of video card do you have, and did you backup xorg.conf before you did it?  This is not a bug, just 'somethin done broke', but if you tell us what you did we should be able to undo it.

---

### Post by TheMatt on 2006-11-14
Thanks for the quick response. I tried to run the GUI with
```
sudo /etc/init.d/gdm start
```
But got "command not found". Perhaps this is why I couldn't stop the X?
 
I was not modifying xorg.conf, I was swapping the driver /usr/lib/xorg/modules/drivers/sis_drv.so. I was swapping the 7.1 version with the 6.9 version because I was experiencing troubles with it.
[http://www.ubuntuforums.org/showthread.php?t=299278](http://www.ubuntuforums.org/showthread.php?t=299278)
EDIT: I tried
```
sudo /etc/init.d/kdm start
```
for KDE, but I got a message saying that the K Desktop is already running. I also tried reconfiguring the xorg, but that didn't do anything. I tried the step before starting the k Desktop enviornment, but I got errors since my disk is Kubuntu 6.06 and I have 6.10 installed. I also can't access the internet untill I get into the GUI.
 
I notice that I see "safeboot" after I select the K7 Kernel. Mabye it is going into recovery mode?

---

### Post by TheMatt on 2006-11-15
I also tried ctrl + alt + F7 to get into the GUI, but that just brought me to a blank screen with a cusror where I could type, but it wasn't a command prompt, so I couldn't do anything. I also tried reconfiguring the XServer, but that didn't do anything.

---

### Post by TheMatt on 2006-11-15
When I try to add the alternate CD as a repository, it does that, but when I do "sudo aptitude update" it still looks online for some reason.

---

### Post by igknighted on 2006-11-15
Does the network not work either?  If you don't want it to look online, just comment out all the internet sources, leaving just the CD.  That should stop it from doing that.  As for the GUI, what video card driver did you try to install?  And can you post your xorg.conf?  If you want to visit the forums from the terminal, you can try installing a text based browser such as lynx.

---

### Post by strabes on 2006-11-15
sorry for the randomness but nice penrose triangle. Have you heard of M.C. Escher? Check him out....

---

### Post by TheMatt on 2006-11-16
OK, I finally fixed it. Thanks for the replies.

I had the wrong driver, I was using one for xorg 6.9 when I had xorg 7.1. I had the correct driver in an archive, so I unzipped it from the command line and coppied it into the drivers folder.

---

