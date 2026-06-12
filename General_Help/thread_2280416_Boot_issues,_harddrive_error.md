---
title: "Boot issues, harddrive error?"
date: 2015-05-30
forum: General Help
---

### Post by golgafrincham on 2015-05-30
Hey!

I got some problems with booting. I tried to install Ubuntu from a live version on a USB memory. It failed and the reason was some error with accessing my hard drive. I managed to fix it with fdisk and reformated the drive and tried again with the Ubuntu live install and it worked.

I then ran Ubuntu from the harddrive, installed some drivers and applications, for example Filezilla (trying to set up a server on a remote computer). While playing around in Filezilla the computer froze totally, you couldn't do anything at all. After a hard reset, now it fails to boot. 

After running boot-repair I got the following result: [Boot-Repair Result]("http://paste.ubuntu.com/11455425/"). And when trying to access the disk from GParted now I get an "Error fsyncing/closing /dev/sda1: input/output error".

I have been running the disk in AHCI-mode (activated from bios) both during install and regular boot.

Do anyone know what can be the reason behind this and how can I fix it? I have been searching bit on the internet but all answers are very specific to that error and no real help unfortunately.

Regards
Robert

---

### Post by tgalati4 on 2015-05-30
Well, /dev/sda (the first disk detected by your system) is having serious problems.  Normally one would look at the SMART parameters to see what is wrong with the disk.

Boot a LiveUSB, install *smartmontools* and examine the SMART status.  Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

---

### Post by golgafrincham on 2015-05-31
Hmm, doesn't look to good. It can't even find vendor and product ID . Running the same test on my other drive gives a good results. Seems I'm going to get myself a new drive...

Thanks for the answer, I will try some more tests and see if it makes any changes.

```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               /0:0:0:0
Product:              
Compliance:           SPC-5
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
Physical block size:  2534866944 bytes
Lowest aligned LBA:   16128
Formatted with unknown protection type [7]
32768 protection information intervals per logical block
Logical block provisioning enabled, LBPRZ=1
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

---

