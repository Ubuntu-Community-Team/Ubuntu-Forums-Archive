---
title: "Android to PC &gt; Isssues transferring files &gt;"
date: 2024-06-23
forum: General Help
---

### Post by noobtechninja on 2024-06-23
Hi there guys.

I was hoping that you could help me with a couple of issues that I've been experiencing.

Background:
I'm wanting an easy way to transfer files between my Linux PC and my Android phone (Samsung S21 Ultra).

Mainly music and image files.

I've tried a few different ways, (particularly via USB cable) and had some limited success.
However although USB cable "should" be the easiest I'm finding it akward and prone to not mount the handset or drop out after a short amount of time.



Issues:
1. Via USB = The H/S (Hand Set) often won't mount properly
The H/S is shown in KDE (Dolphin) gives me the option to mount the H/S
transfer images or mount as MTP storage. However when selecting the H/S and 

Error: No storage media found. Make sure your device is unlocked and has MTP enabled in its USB connection settings.

However my H/S -
Was unlocked
Has MTP enabled in its settings

When the pop-op notification shows (to request permission to allow file transfers).
I allow it.

Despite this, I cannot get my H/S to link to my PC and transfer files (consistently). As said, I've gotten it to work "sometimes" previously
which seems more to do with luck.

2. I've briefly tried KDE connect, however neither the PC app or the Andriod app appears to be able to see each other.
Despite both being on the same network (PC via Ethernet, H/S via Wi-Fi).


Steps taken / Troubleshooting:

1. I have all the relevant MPT drivers and files to allow file transfer between my phone and PC

2. I've been able to transfer files between my H/S and PC successfully in the past.

3. I've set my H/S up correctly E.G. -
Was unlocked
Has MTP enabled in its settings

When the pop-op notification shows (to request permission to allow file transfers).
I allow it.



Questions:

1. Is there an easy way to transfer files wirelessly (via Wi-Fi) on the same network ?

1.1. If so - what are the best options or apps to allow this ?

2. I could also try FTP / SFTP, however I don't really want to upload my files to an
external source, just to download them to myself again.

3. Is there any reason that USB cable is so flaky ?
(As this was a specific USB cable bought for data transfer for my phone and PC).

4. Do you have any other recommendations to allow me to easily transfer files between my H/S and my PC ?

**Useful information:**
Phone: Samsung S21 Ultra
Android: 13
Kernel version: 5.4.226-27099861
One UI version: 5.1

PC OS: Ubuntu 22.04.  LTS
Kernel: 6.5.0-35 generic (64 bit)
KDE Plasma: 5.24.7

TIA for any help or advice.

---

### Post by currentshaft on 2024-06-23
The way it works well for me is using USB debugging in developer settings and using "adb pull" on my Linux workstation to copy the Android filesystem.

Are you using a quality USB 3.0 cable from a reputable brand? Do you see any messages/errors in "sudo dmesg" output?

---

### Post by noobtechninja on 2024-06-30
Thanks for the advice.

I manged to get this working by using an Android app called Airdroid

Setup was a piece of cake, really nice an easy.
Excellent web interface, and it "just worked" (via Wi-Fi on my internal network).

I'm a very happy bunny, as I've been able to move over the music files that I'd been trying
to before but was previously unable to.

---

