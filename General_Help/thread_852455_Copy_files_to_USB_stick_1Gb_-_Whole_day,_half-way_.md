---
title: "Copy files to USB stick 1Gb - Whole day, half-way done..."
date: 2008-07-07
forum: General Help
---

### Post by Margus81 on 2008-07-07
I have 1Ghz single core, 1GB momory.. Ubuntu Hardy.

HDD Luks encrypted (with alternate CD)...Usb stick 4GB- Truecrypt encrypted in 2.7 GB file container...
After mounting the container, formatted it to ext3:
mkfs.ext3 /dev...and so on....

Task: Backup Home folder to USB.
rsync -avh --delete --progress --exclude=".*/" ...and so forth...

First files went really fast... But each next one progressivly slower...

I took a one hour nap... still not done...

Went to work, came back in 8 hours... it was still working..
hard disk was working as hell, Usb stick was flashing, indicating, that something is going on there too...

The system was EXTREEMELY slow.... I moved the mouse and in 10 sekunds the cursor responded...

still not complete! Still it had made some progress...

It took me 10 Minutes to close the terminal...

But the hard disc kept on working - HARD!

It took another 10 Minutes to get the system to shut down...
man, I had headaches!

Then during shut-down process, at some point the hard disk stopped...

still no shut-down....I saw the USB flashing...I waited another 10 minutes...nothing... I cut the power!


...
Is this sick or what! I was copying some 1 GB... no response from system, it works as HELL the WHOLE day! WHAT IS IT DOING???


I mean I had no other applications running...but to copy some files, I should be able to surf the web at least...

I did nothing... One day - still not complete...
system shut down - 30 Minutes - not complete...

HDD and USB had a though day... I heard and saw, they were intensively doing something..

WHAT!

---

### Post by Margus81 on 2008-07-08
It is an incompatibility with Truecrypt...

Copying files to unencrypted USB caused no problems.

---

### Post by Margus81 on 2008-07-08
Updating Linux kernel solved the problem

---

### Post by Margus81 on 2008-07-08
False!

It was ok after upgrading kernel to copy stuff to container on HDD.

Container on USB-stick caused still system not to respond.

Truecrypt creators say, it is a bug in linux kernel...

---

