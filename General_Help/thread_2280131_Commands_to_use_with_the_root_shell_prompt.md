---
title: "Commands to use with the root shell prompt"
date: 2015-05-28
forum: General Help
---

### Post by aneblanc on 2015-05-28
My computer is only stable in Recovery Mode. I want to save the files on the HDD before I format the disk and do a fresh OS install. Are the commands for the root shell prompt the same as the ones used in the terminal? Are they similar to the ones used for DOS? Any pointers?

---

### Post by steeldriver on 2015-05-28
The root shell of recovery mode should just be the same (bash) shell as that of your regular user - the commands will be the same

However by default the filesystem will be mounted read-only: if you're just copying files **from **it, that might not be a problem - but for example if you need to mount a disk to copy stuff **to **you may need to remount

IIRC you can do that either by selecting the 'Enable networking' option from the recovery mode menu *before *dropping to the root shell, or manually from the root shell prompt using

```

mount -o remount,rw /

```

Alternatively, if you have already prepared a (regular desktop edition) USB or DVD from which to do the reinstall, you could boot from that and use the 'Try Ubuntu' option to get a live system from which you should be able to mount the HDD and copy your stuff

---

### Post by matt_symes on 2015-05-28
Hi

> Are they similar to the ones used for DOS?

No.

If you are at the root shell and not using some x fail safe mode then you will have to mount any external hard drive manually before copying files (assuming you are using an external hard drive not and another option such as a remote file system).  You will then have to unmount the hard drive.

But why make life difficult ? Have you considered using a LiveCD/USB to copy off the files from a live environment ?

Anyway, when you say "it's unstable", can you elaborate more please.

Also, could you detail the files you want to save and where you want to save them.

Kind regards

---

### Post by aneblanc on 2015-05-28
> **steeldriver said:**
> Alternatively, if you have already prepared a (regular desktop edition) USB or DVD from which to do the reinstall, you could boot from that and use the 'Try Ubuntu' option to get a live system from which you should be able to mount the HDD and copy your stuff

Unfortunately I have tried this. The computer is not stable under a live system and has shut down itself before finishing the copying.

---

### Post by aneblanc on 2015-05-28
> **matt_symes said:**
> Hi



No.

If you are at the root shell and not using some x fail safe mode then you will have to mount any external hard drive manually before copying files (assuming you are using an external hard drive not and another option such as a remote file system).  You will then have to unmount the hard drive.

But why make life difficult ? Have you considered using a LiveCD/USB to copy off the files from a live environment ?

Anyway, when you say "it's unstable", can you elaborate more please.

Also, could you detail the files you want to save and where you want to save them.

Kind regards

Hi Matt,

1) There is only about 6GB of data to save and I am going to try to use a USB key. Yes I would have to mount and unmount it from the root shell prompt.

2) See my answer to the first replier.

3) Unstable: the computer shuts itself down as soon as the OS has finished (or even before) its installation. 
I think what is happening is that the system is basing its automatic shut-down on the charging state of the battery recorded in its memory even if the battery is not physically present. 
The battery has no power left in it because it does not charge anymore and I don't have a similar computer that would accept it and charge it. 
I have ordered a new battery but it'll take a few weeks to arrive and might not arrive charged.
I found that the only configuration in which the computer does not switch off is in the Recovery Mode.

4) I would like to save photos, videos, music and any documents on the HDD (this is my son's computer).

Kind regards

---

### Post by matt_symes on 2015-05-28
Hi

So you would be looking at something like.

Boot into the root shell recovery mode.

As steel driver said, remount the root file system as read/write.

```
mount -o remount,rw /
```

Plug the external hard drive into the computer.

You then need to find out what the device node of the external hard drive is. If there is only one hard drive then hhis is easy as it will be /dev/sdb1.

```
mount /dev/sdb1 /mnt
```

Otherwise, find the device node using

```
blkid
```

Copy accross the files. I'm going to assume that the hard drive is formatted as NTFS as so won't bother with the files attributes.

```
cp -r /home/<your_sons_username>/* /mnt
```

Change <your_sons_username> as required. This will copy everything from your sons home folder and may allow him to retrieve application settings.

Then unmount the device.

```
umount /mnt
```

Then shutdown the laptop.

```
shutdown -h now
```

Post back any errors and check on another computer that the files have been copied correctly onto the external hard drive.

Kind regards

---

### Post by aneblanc on 2015-06-03
Hi Matt,

Thanks for the answer. I have more questions:

1) I used your commands to copy the home directory on to a USB 8GB memory stick. Unfortunately it was too small. 
I did not know how to measure the size of the home directory from the prompt. 
In the meantime I could start Ubuntu in normal mode for a brief period of time (maybe 20') before it shut down and I could see that there was 17GB (not 6GB as I had thought) of data in the home directory.
Consequently I made room in a 32GB SD card to copy the data. Now another problem comes up: command blkid doesn't show the SD card, it only shows sda1 to sda8 for the different partitions on the HDD.
If I knew how to display the different parts of the home directory and measure how much data they hold, I could copy piecemeal the different subdirectories on to USB memory sticks.
Alternately, if I could mount the SD card, I could copy all the home directory in one go.
Could you help me for this part?

2) Before I format the whole HDD and reinstall Ubuntu on the computer I would like to try to flash the BIOS to see if I get some improvement in the situation. 
I created a bootable USB stick formatted as FAT32 with the Unetbootin utility. 
I used the FreeDOS option and copied also the BIOS version 2.21 supplied by ACER as an .exe file. 
On the stick I now have the following files: ldlinux.sys, menu.c32, syslinux.cfg, ubninit, ubnkern and Q1VZC221.exe. 
The current BIOS version is 2.08.
My question is: will this set of files be enough to flash the BIOS? 
I couldn't find a clear answer online and I don't want to risk bricking the computer with a wrong method.

Your help is very much appreciated.

Kind regards

---

### Post by matt_symes on 2015-06-04
Hi

> **aneblanc said:**
> Hi Matt,

Thanks for the answer. I have more questions:

1) I used your commands to copy the home directory on to a USB 8GB memory stick. Unfortunately it was too small. 
I did not know how to measure the size of the home directory from the prompt. 
In the meantime I could start Ubuntu in normal mode for a brief period of time (maybe 20') before it shut down and I could see that there was 17GB (not 6GB as I had thought) of data in the home directory.
Consequently I made room in a 32GB SD card to copy the data. Now another problem comes up: command blkid doesn't show the SD card, it only shows sda1 to sda8 for the different partitions on the HDD.
If I knew how to display the different parts of the home directory and measure how much data they hold, I could copy piecemeal the different subdirectories on to USB memory sticks.
Alternately, if I could mount the SD card, I could copy all the home directory in one go.
Could you help me for this part?


I assume the sd card is formatted correctly (usually vfat) ? If so then i believe blkid should see it.

Can you put the SD card in, wait 5 seconds can post the output of

```
dmesg | tail -n 15
```

That should give us more information from the kernel ring buffer as to what is going on.

> 
2) Before I format the whole HDD and reinstall Ubuntu on the computer I would like to try to flash the BIOS to see if I get some improvement in the situation. 
I created a bootable USB stick formatted as FAT32 with the Unetbootin utility. 
I used the FreeDOS option and copied also the BIOS version 2.21 supplied by ACER as an .exe file. 
On the stick I now have the following files: ldlinux.sys, menu.c32, syslinux.cfg, ubninit, ubnkern and Q1VZC221.exe. 
The current BIOS version is 2.08.
My question is: will this set of files be enough to flash the BIOS? 
I couldn't find a clear answer online and I don't want to risk bricking the computer with a wrong method.

I have a feeling that the .exe file may only run from inside windows and not from DOS but i may be wrong.

Can you post the link to the page that you got the BIOS from. Can you also post the make and model of you PC.

I'll take a look for you if you can do that.

Kind regards

---

### Post by aneblanc on 2015-06-04
> **matt_symes said:**
> I assume the sd card is formatted correctly (usually vfat) ? If so then i believe blkid should see it.

The card is formatted as FAT32.


> Can you put the SD card in, wait 5 seconds can post the output of

```
dmesg | tail -n 15
```

That should give us more information from the kernel ring buffer as to what is going on.

This is the result (hand copied):

[    13.597752] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    13.597755] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    13.597752] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    13.597752] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    13.765979] ieee80211 phy0: Selected rate control algorithm 'iwl-an-rs'
[    92.185926] mmc0: Timeout waiting for hardware interrupt.
[   102.201653] mmc0: Timeout waiting for hardware interrupt.
[   112.217398] mmc0: Timeout waiting for hardware interrupt.
[   122.233131] mmc0: Timeout waiting for hardware interrupt.
[   132.248871] mmc0: Timeout waiting for hardware interrupt.
[   142.264597] mmc0: Timeout waiting for hardware interrupt.
[   152.280359] mmc0: Timeout waiting for hardware interrupt.
[   162.296078] mmc0: Timeout waiting for hardware interrupt.
[   172.311816] mmc0: Timeout waiting for hardware interrupt.
[   182.327550] mmc0: Timeout waiting for hardware interrupt.


I did it again a few times and every time I get different numbers in brackets, mmc0: and "Timeout waiting for hardware interrupt".


> Can you post the link to the page that you got the BIOS from. Can you also post the make and model of you PC.

[http://us.acer.com/ac/en/US/content/drivers](http://us.acer.com/ac/en/US/content/drivers) 
This is the link where I found the BIOS. The computer is an ACER Aspire One AO756. 
As you can see there are two versions of the BIOS listed but the current one is already 2.08 so I thought there is no point reverting to 1.09, or is there?

Kind regards

---

### Post by matt_symes on 2015-06-04
Hi

> **aneblanc said:**
> The card is formatted as FAT32.

[    92.185926] mmc0: Timeout waiting for hardware interrupt.
[   102.201653] mmc0: Timeout waiting for hardware interrupt.
[   112.217398] mmc0: Timeout waiting for hardware interrupt.
[   122.233131] mmc0: Timeout waiting for hardware interrupt.
[   132.248871] mmc0: Timeout waiting for hardware interrupt.
[   142.264597] mmc0: Timeout waiting for hardware interrupt.
[   152.280359] mmc0: Timeout waiting for hardware interrupt.
[   162.296078] mmc0: Timeout waiting for hardware interrupt.
[   172.311816] mmc0: Timeout waiting for hardware interrupt.
[   182.327550] mmc0: Timeout waiting for hardware interrupt.

I did it again a few times and every time I get different numbers in brackets, mmc0: and "Timeout waiting for hardware interrupt".

The numbers in the brackets are just time stamps. 

That looks serious. It does not look to be reading anything from the card as it is not getting an interrupt from the card reader. That may be a hardware problem or some misconfiguration in the BIOS or a kernel bug. Too time consuming to fix.

Can't you buy another usb stick ? I picked up a 32G USB2 stick for £15 and that was pricey but it's a known good make.

> 
[http://us.acer.com/ac/en/US/content/drivers](http://us.acer.com/ac/en/US/content/drivers) 
This is the link where I found the BIOS. The computer is an ACER Aspire One AO756. 
As you can see there are two versions of the BIOS listed but the current one is already 2.08 so I thought there is no point reverting to 1.09, or is there?

Kind regards

I'll take a look at the link in the morning as it's very late here.

Kind regards

---

