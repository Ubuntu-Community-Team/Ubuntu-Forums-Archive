---
title: "USB extrenal HD (linux compatible) mounted?"
date: 2007-01-05
forum: General Help
---

### Post by bone2006 on 2007-01-05
I have a Bytecc BT-300, which allows me to read an IDE drive on via USB.  I have a 2 gig HD that was ext32 that I plugged in and I can't seem to view in ubuntu.  I'm not sure if drivers are required, because the CD only has windows drivers.  
Here's the device I'm referring to:

[http://www.3gplaza.com/estore/control/Computer3G/productdetails?id=53953](http://www.3gplaza.com/estore/control/Computer3G/productdetails?id=53953)


You'll see it says linux and mac

---

### Post by rowanparker on 2007-01-05
Can you post your result of *fdisk -l* please (might have to be root, can't remember).

---

### Post by bodhi.zazen on 2007-01-05
Yes,```
sudo fdisk -l
```

---

### Post by bone2006 on 2007-01-06
I really appreciate the help
I should have given more information.  Before posting I actually did do:

 sudo fdisk -l

and regardless if it was plugged in or not it showed the same.

I just received the device and I never tried it in windows either, so I tried it on two other machines that I have dual boot and windows will indicated that a USB storage device is connected, but nothing shows up for me to access and the location says 0. I tried changing the jumpers to each selection and even removing the jumpers from the IDE HD, but no luck with the exact same results.   All the drivers that came with the device were for windows 98..etc
From reading reviews windows XP didn't require a driver for it, but seems I'm having problems with both linux and windows reading it. 

I really appreciate the help though, but it's probably the device that's not working.  I tried two different IDE drivers and no luck. I was reading newegg.com reviews and some other people didn't have any luck using it either.

---

### Post by bone2006 on 2007-01-06
Here's what it returns though, couldn't post it earlier as I was in windows trying to get it to read there:



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       35853   211190490    f  W95 Ext'd (LBA)
/dev/sda3           35854       38913    24579450   83  Linux
/dev/sda5            9562       35719   210114103+   7  HPFS/NTFS
/dev/sda6           35720       35853     1076323+  82  Linux swap / Solaris

I should only have 2 NTFS and 1 Ext3 and of course the swap.  I'm really not sure what what  W95 Ext'd (LBA) is?  A friend has similar setup and his say extended only

---

### Post by rowanparker on 2007-01-06
And this is with it plugged in, as I don't see it listed?

---

### Post by bone2006 on 2007-01-07
yes, it's with it plugged in or not
seems as if I'm having hardware problem and not linux problem.  Thank for your help though

---

### Post by rowanparker on 2007-01-07
> **bone2006 said:**
> yes, it's with it plugged in or not
seems as if I'm having hardware problem and not linux problem.  Thank for your help though
No problem, good luck in sorting it.

---

