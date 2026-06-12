---
title: "Can someone help me resolve these error messages I get?"
date: 2007-02-27
forum: General Help
---

### Post by maddbaron on 2007-02-27
Error 1:
> X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I get this whenever I open an application via konsole.

Eroor 2:
> sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  audacity bmp-mp4 k3b libk3b2
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

I've gotten this error when I try to upgrade these programs  for the past month. everything else upgrades but these don't and whenever I try to install them one by one I am told they are missing something that is not installable.

Last question, Is there a way to have the output in terminal save automatically? Sometimes my laptop will go crazy and become unstable, firefox will scroll to different tabs by itself scroll down and up by itself. and when I hover over an application it will open it by itself and switch workstations also. I am often forced to hard shutdown the pc just to restart. I would like to record the firefox output and see what is going on.

Thank you in advance.

---

### Post by disturbedite on 2007-02-27
as for the first error, try opening your xorg.conf (located in /etc/X11/xorg.conf) and comment out all the lines in the wacom sections.

as for the second error, i'd check your /etc/apt/sources.list and make sure you have the other sections (multiverse, universe, etc) uncommented.

i don't know about the terminal question, but i would like that feature in konsole too, but i don't see it.  i can however manually save the console output/history by clicking Edit --> Save History As...

---

### Post by maddbaron on 2007-02-27
> **disturbedite said:**
> as for the first error, try opening your xorg.conf (located in /etc/X11/xorg.conf) and comment out all the lines in the wacom sections.

as for the second error, i'd check your /etc/apt/sources.list and make sure you have the other sections (multiverse, universe, etc) uncommented.

i don't know about the terminal question, but i would like that feature in konsole too, but i don't see it.  i can however manually save the console output/history by clicking Edit --> Save History As...

Is the Command for the 1st
sudo kate xorg.conf ?  I use kubuntu *when i tried that it opened in kate but was blank*
and to comment out do I put "#" in front of the wacom sections?

Can i check the sourcelist via adept?

---

### Post by IcemanV9 on 2007-02-27
1st error - the app was looking for some kind of device (it wasn't plugged in or enabled). What app are you trying to start?

2nd error - simply type sudo apt-get dist-upgrade and those packages will be installed/upgraded.

3rd question - touchpad could be the problem since it could be very sensitive to a barely "touch" from your palm or hand by accident. Try to turn it off and see if it does resolve the problem.

---

### Post by maddbaron on 2007-02-27
> **IcemanV9 said:**
> 1st error - the app was looking for some kind of device (it wasn't plugged in or enabled). What app are you trying to start?

2nd error - simply type sudo apt-get dist-upgrade and those packages will be installed/upgraded.

3rd question - touchpad could be the problem since it could be very sensitive to a barely "touch" from your palm or hand by accident. Try to turn it off and see if it does resolve the problem.

for the 1st, I try to open  gaim  usually sometimes when I open other smaller programs but mostly when I open gaim. so I can see if it has any error messages b/c my gaim keeps dying b/c of segmentation fault but i never see a message explaining why. And I have no plugins enabled. 

2nd:
> sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  audacity bmp-mp4 k3b libk3b2
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


I assume it is touchpad I followed the wiki and disabled many things and dont even touch it and it just goes off at random times.

---

### Post by IcemanV9 on 2007-02-27
1st error - type gaim -d in the terminal; hopefully you see some errors being spewed.

2nd error - hmm. odd. Update your box via update-manager (or type gksudo update-manager) then.

3rd question - oy. I don't know what else to say. You can start Firefox in the terminal. You should be able to see all kinds of message spewed from Firefox in the terminal.

---

### Post by maddbaron on 2007-02-27
> **IcemanV9 said:**
> 1st error - type gaim -d in the terminal; hopefully you see some errors being spewed.

2nd error - hmm. odd. Update your box via update-manager (or type gksudo update-manager) then.

3rd question - oy. I don't know what else to say. You can start Firefox in the terminal. You should be able to see all kinds of message spewed from Firefox in the terminal.

for the gaim it doesn't say any errors it just closes. The last time it updated a buddy status then said segmentation fault.

tried updating via adept and it says broken. I have no idea what to do.

do you know how to comment out in xorg?
I want to comment out
> #Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

#Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

#Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection




Do i put # in front of it? or do I just delete it?

---

### Post by ~LoKe on 2007-02-27
Are you running Feisty?  It's possible the packages haven't fully hit the repos.

Try manually installing them.

```
sudo apt-get install k3b
```

---

### Post by maddbaron on 2007-02-27
well i fixed the original error two. I found an old sourcelist that I had saved and replaced the current one and it fixed the issue.

now to fix error one and try to fix gaim.

is reinstalling gaim a away to fix the segmentation erros I get?

---

### Post by IcemanV9 on 2007-02-27
Try to compare the old & new sources.list. There might be misspelled or missing word. Anyway, glad you fixed it. Yay! :)

You could try to reinstall gaim; it wouldn't hurt. And check the bug list @ launchpad.net. Hopefully, there is a solution there.

Save xorg.conf in your home directory. I have two files (xorg.conf & xorg.conf.orig). Delete those "wacom" & remove three lines (stylus, cursor, eraser) under "ServerLayout" section. Then sudo cp xorg.conf /etc/X11/xorg.conf. If X fails to load, then just copy the original (xorg.conf.orig) back to /etc/X11/xorg.conf. If X runs, then check the log (/var/log/Xlog.0.log) to see any errors (EE).

---

