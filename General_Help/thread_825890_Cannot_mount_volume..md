---
title: "Cannot mount volume."
date: 2008-06-11
forum: General Help
---

### Post by ninja senses on 2008-06-11
I have an external hard drive I use to backup all my files.  Well it used to work with ubuntu and sometimes still does.  But for the past month I havent been able to get it to work.  I can see it under computer as 'sense"(thats what I named it).  But When I try to view the files it says cannot mount volume.  I have tried hooking it up through SATA and USB and it still doesnt work.  Any ideas?

---

### Post by Mark_in_Hollywood on 2008-06-11
Please post the output of 

sudo lsusb

---

### Post by ninja senses on 2008-06-11
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
Bus 001 Device 001: ID 0000:0000

---

### Post by hal8000 on 2008-06-11
The output from lsusb does not show your drive.

When plugged into the usb port type
dmesg

are any new kernel messages generated?
Also, I would suggest trying a dfferent USB port if you have one, and also
try a known good USB cable (if you have a spare).

---

### Post by ninja senses on 2008-06-11
> **hal8000 said:**
> The output from lsusb does not show your drive.

When plugged into the usb port type
dmesg

are any new kernel messages generated?
Also, I would suggest trying a dfferent USB port if you have one, and also
try a known good USB cable (if you have a spare).

 I didnt have it plugged in when I ran this.
here it is with it plugged in the the USB.

Bus 003 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
Bus 001 Device 001: ID 0000:0000

EDIT:  I have tried it in all my USB ports

---

### Post by Mark_in_Hollywood on 2008-06-12
I cannot know the name of every peripheral, but looking at the Sunplus Technology co., ltd. website I don't see that they make external USB cradles, so if that is the name of your usb drive bay maker, let us know.

Meanwhile, assuming that Sunplus is not the cradle/bay for the external harddrive, then the output shows the device isn't found and that **may** mean it isn't getting mounted or maybe something else is wrong. In any case, please let us know what devices are what. That is: what is the Sunplus device on your USB bus.

---

### Post by ninja senses on 2008-06-13
> **Mark_in_Hollywood said:**
> I cannot know the name of every peripheral, but looking at the Sunplus Technology co., ltd. website I don't see that they make external USB cradles, so if that is the name of your usb drive bay maker, let us know.

Meanwhile, assuming that Sunplus is not the cradle/bay for the external harddrive, then the output shows the device isn't found and that **may** mean it isn't getting mounted or maybe something else is wrong. In any case, please let us know what devices are what. That is: what is the Sunplus device on your USB bus.

Yea thats the error im getting, it said unnable to mount volume.  It has worked before, I dont understand why it isnt now.

---

### Post by Mark_in_Hollywood on 2008-06-14
Your USB isn't being mounted, if I'm understanding the limited response above this post.

Please check the usb device on a separate computer. Say Starbucks, or any internet cafe with usb ports available.

If it works on another computer, you need to change some code in fstab, make a directory in /media, too, maybe.

---

### Post by tech0007 on 2008-06-14
1st usb drives usually use /dev/sdb.  what's the output of 'dmesg | grep sdb'

---

### Post by ninja senses on 2008-06-18
> **Mark_in_Hollywood said:**
> Your USB isn't being mounted, if I'm understanding the limited response above this post.

Please check the usb device on a separate computer. Say Starbucks, or any internet cafe with usb ports available.

If it works on another computer, you need to change some code in fstab, make a directory in /media, too, maybe.

Yea it works on my windows partition and on my laptop with vista.

ps. - starbucks = teh :twisted:

---

### Post by ninja senses on 2008-06-19
i wanna upgrade really bad but im not going to til i backup all my files!!

---

### Post by Mark_in_Hollywood on 2008-06-19
please post the output of:

dmesg | grep sdb

---

### Post by ninja senses on 2008-06-19
> **Mark_in_Hollywood said:**
> please post the output of:

dmesg | grep sdb

[45369.477009] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[45369.479251] sd 2:0:0:0: [sdb] Write Protect is off
[45369.479255] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[45369.479258] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[45369.500361] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[45369.502611] sd 2:0:0:0: [sdb] Write Protect is off
[45369.502615] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[45369.502617] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[45369.502620]  sdb: sdb1
[45369.526574] sd 2:0:0:0: [sdb] Attached SCSI disk

---

### Post by ninja senses on 2008-06-21
still havent been able to figure this out

---

### Post by ninja senses on 2008-06-23
anyone.................anyone?

</ferrisbueller quote>

---

### Post by Mark_in_Hollywood on 2008-06-24
> **ninja senses said:**
> [45369.477009] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[45369.479251] sd 2:0:0:0: [sdb] Write Protect is off
[45369.479255] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[45369.479258] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[45369.500361] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[45369.502611] sd 2:0:0:0: [sdb] Write Protect is off
[45369.502615] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[45369.502617] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[45369.502620]  sdb: sdb1
[45369.526574] sd 2:0:0:0: [sdb] Attached SCSI disk

Can someone suggest some help for the original POSTER. I'm lost.

---

