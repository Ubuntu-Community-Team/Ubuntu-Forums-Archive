---
title: "I might be screwed"
date: 2008-02-24
forum: General Help
---

### Post by jd8001 on 2008-02-24
Okay, I was getting a very slow refresh rate with some games, so decided to play around a little with which driver I was using. I changed drivers and rebooted. Now, I can't get the splash screen to come up when I reboot. This is the text I see at bootup:

Starting up...
Loading, please wait
usplash: Setting mode 1280x1024 failed
usplash Setting mode 1152x864 failed
usplash: setting mode 1024x768 
kinit: name_to_dev_t(/dev/disk/by-uuid/12320235-8243-4e7d-acc3-45ad7ebefb45) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/12320235-8243-4e7d-acc3-45ad7ebefb45
kinit: no resume image, doing normal boot....

Ubuntu 7.10 hector tty1

hector login: 

any thoughts? 

JD

---

### Post by lswest on 2008-02-24
well, you can log in, then run "sudo nano /etc/X11/xorg.conf" and change the "Driver: " line to "vesa" instead of whatever driver is listed there atm, which would get you a GUI again. in nano, when you're done editing <ctrl>+<x> will exit, type y to save, and enter to submit the filename (since you're editing a file, the filename is already present)  Other than that...what driver did you change it to?

---

### Post by jd8001 on 2008-02-24
I chose select by device type (or something to that effect) and told it that I had an intel 815

---

### Post by jd8001 on 2008-02-24
did what you said with the xorg.conf file. Here's what the section looks like now:

Section "Device"
     Identifier              "Intel Corporation Mobile 915GM/GMS/910GML Express Graph$
     Boardname          "Intel 915"
     Busid                     "PCI:0:2:0"
     Driver                   "vesa"
     Screen   0
     Vendorname         "intel"
EndSection



thoughts?

---

### Post by jd8001 on 2008-02-24
oh I forgot, what I have there has not produced a gui for me


JD

---

### Post by lswest on 2008-02-25
can you start a GUI by running the "startx" command in the terminal view?  sorry about the late response, i just woke up :P

---

### Post by jd8001 on 2008-02-25
No, the startx command does not start a gui. I get two error messages:

(EE) VESA(0): No valid Modes
(EE) Screen(s) found, but none have a usable configuration

Fatal Server error:
no screens found
XI0:     fatal IO error 104 (Connection Reset by peer) on X server ":0.0"
           after 0 requests (0 known proscessed) with 0 events remaining


...anyway. I'm completely lost here. I could probably get all my needed data to an external harddrive, so I'm considering just reloading the os. Any thoughts?

JD

---

### Post by bodhi.zazen on 2008-02-25
reonfigure X with :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart GDM :

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by jd8001 on 2008-02-25
Hey,
    Thanks for your help. I went and googled my problem and found an answer (oddly enough the exact same answer you provided at least in spirit). I ran Xconfig and was rather easily able to get the driver back up and going. hope no one else has this problem. Thanks for your help though. BTW do you live on this forum! Hot dog man, an 11 minute response time!!!

JD 
P.S I'm keeping my fingers crossed, I have yet to reboot.

---

