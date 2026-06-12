---
title: "Ubuntu 20.04 LTS (Focal Fossa) System Tweaks"
date: 2021-08-23
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-23
What would be some good system tweaks?
My budget won't allow new hardware any time soon.

I have...

> Ubuntu 20.04 LTS (Normal Install)
wine-staging 6.15

128GB hard drive
6.1GB Swap Area
4GB RAM

---

### Post by T.J. on 2021-08-24
What is the IO error message?

---

### Post by wyattwhiteeagle on 2021-08-24
> **T.J. said:**
> What is the IO error message?

Thank you.

The I/O error has already been troubleshooted and the results summary came back with the following...

```
I/O Device Error
Internally marked as "dirty" due to bad sector's.
Replace the hard drive or repair it by resetting the internal markers.
```

The way I understand that to mean is that the hard drive has went beyond it's EOL term and can't be used anymore.

The part of my original post that I was hoping to bring attention to is...(I will edit to reduce confusion)

> What are the best settings Ubuntu 20.04 LTS (Focal Fossa) on 128GB hard Drive and 4GB Ram and 6.1GB Virtual Memory?

Small hard drive gets filled up very quickly and 4gb ram with 6.1g v-memory seems a bit small for a dual-core processor.

---

### Post by T.J. on 2021-08-26
Are you able to look at the SMART data for more information on what failed?

---

### Post by guiverc on 2021-08-26
I'm using a 2009 dell desktop, and whilst Ubuntu 20.04 LTS (with GNOME) runs perfectly okay on it; my preference is a *lighter* desktop (ie. *flavor*) as it performs faster and is better than I'd ever be able to achieve by tweaking GNOME.

If you have IO errors, I'd for sure explore the health of the drive (from *live* media, not the installed system)  Refer [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) though GUI tools can be used too (`gnome-disks`, KDE Partition Manager etc)

The lowest spec you gave was 4GB of RAM, so the best *tweak* you can do in my opinion, is ensure your chosen apps match your desktop perfectly, so as to avoid wasting RAM (ie. having one set of libraries for desktop or applications, rather than requiring multiple libs to co-exist because of poor application choice).

---

### Post by wyattwhiteeagle on 2021-08-30
> **guiverc said:**
> I'm using a 2009 dell desktop, and whilst Ubuntu 20.04 LTS (with GNOME) runs perfectly okay on it; my preference is a *lighter* desktop (ie. *flavor*) as it performs faster and is better than I'd ever be able to achieve by tweaking GNOME.

If you have IO errors, I'd for sure explore the health of the drive (from *live* media, not the installed system)  Refer [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) though GUI tools can be used too (`gnome-disks`, KDE Partition Manager etc)

The lowest spec you gave was 4GB of RAM, so the best *tweak* you can do in my opinion, is ensure your chosen apps match your desktop perfectly, so as to avoid wasting RAM (ie. having one set of libraries for desktop or applications, rather than requiring multiple libs to co-exist because of poor application choice).

Thank you for that info.

Nothing I've tried so far has corrected the issue.

 In my situation, I don't believe LiveUSB or the installed USB actually matters.

Using the Ubuntu LiveUSB, I chose the "Something Else" option to repartition and install Ubuntu onto a 128gb usb thumb drive.
I designated some of that 128gb as a swap area.
The 128gb USB flashdrive that has Ubuntu 20.04 LTS (Focal Fossa) installed onto.

The detail's..
> Model    SanDisk Cruzer Glide (1.00)
Size    128 GB (128,000,000,000 bytes)
Partitioning    GUID Partition Table
Serial Number    4C530000191202123483


Device        /dev/sdb1
Size        122 GB &#8212; 108 GB free (11.3% full)
UUID        0b2dfa7b-e56b-4aba-9440-de31ae7a9e4e
Partition Type    Linux Filesystem
Contents    Ext4 (version 1.0) &#8212; Mounted at Filesystem Root


Device        /dev/sdb2
Size        6.0 GB (5,999,951,872 bytes)
UUID        76318833-a77c-4a1d-89a9-1c9bd49fa60d
Partition Type    Linux Swap
Contents    Swap (version 1) &#8212; Active


The few error's it has are mainly caused by my own "trial and error".
That's why I'm asking about "system tweaks".


The Internal HDD is the device with the I/O errors. 
I can't install or uninstall anything on that hard drive.
However, Ubuntu is able to access the non-defective partition's as "usable storage space".
It had Windows 7 Home Premium (SP1) installed on it.
 25% or more of that hard drive is bad sectors.
That many sectors being marked as "Bad" is probably what triggered the "I/O Device Error".
It'll take some time, but it can be repaired with forensics technique's using SluethKit, etc.

Ubuntu's "Self Test" in Disk's see's the drive as "Old Age" and "Pre-fail"
Not even the Windows Installation media "basic fix" technique's can correct it.
Windows installation gave the message, "Cannot install to a partition on Disk 0...(Error Code: 0x80070057)"
I've tried using Windows "cmd (admin) at boot" in the installation media.
I've also tried as per this thread [https://ubuntuforums.org/showthread.php?t=2465826](https://ubuntuforums.org/showthread.php?t=2465826)

---

### Post by wyattwhiteeagle on 2021-08-30
Here are attached screenshots of the internal HDD.

My Ubuntu install is on a USB thumb drive.

---

### Post by wyattwhiteeagle on 2021-08-31
> **guiverc said:**
> ...ensure your chosen apps match your desktop perfectly, so as to avoid wasting RAM (ie. having one set of libraries for desktop or applications...).


I'm a bit lost here.
Can you elaborate a bit more because...


The system was manufactured and shipped with Windows 7 Home Premium.
Apps matching my desktop perfectly sounds like you are meaning to choose no other apps unless they are specifically for Win7 HP.


As far as Ubuntu 20.04 LTS Focal Fossa, it's actually being strict about installing apps for an earlier version (ie, Bionic Beaver, etc).

To sum it up, it seems like you are saying...
So, if it ain't compatible for Focal Fossa, go find a Windows equivalent and use PlayOnLinux, Wine, or something.
If that don't work, tough...you ain't gonna use that app.

---

### Post by ajgreeny on 2021-08-31
Now we know that your Ubuntu install is actually a full install on a 128G USB flash drive, I think a lot of your problems are explainable more simply and quickly.

A USB flash drive is never going to be a completely reliable way to run the full OS. It will never run as fast as an installation on a normal internal drive, particularly if using USB2, and trying to use gnome will undoubtedly be too resource hungry for running a fully usable OS.

Your options are limited by that limiting hardware, particularly the USB flash drive, and don't forget that flash memory is extremely time limited in terms of the number of writes to it, so be prepared for it to possibly just suddenly stop working at all, not just run slowly.

BACKUP, BACKUP, BACKUP.
Always essential but even more so in your situation!

---

### Post by wyattwhiteeagle on 2021-08-31
> **ajgreeny said:**
> Now we know that your Ubuntu install is actually a full install on a 128G USB flash drive, I think a lot of your problems are explainable more simply and quickly.

A USB flash drive is never going to be a completely reliable way to run the full OS. It will never run as fast as an installation on a normal internal drive, particularly if using USB2, and trying to use gnome will undoubtedly be too resource hungry for running a fully usable OS.

Your options are limited by that limiting hardware, particularly the USB flash drive, and don't forget that flash memory is extremely time limited in terms of the number of writes to it, so be prepared for it to possibly just suddenly stop working at all, not just run slowly.

BACKUP, BACKUP, BACKUP.
Always essential but even more so in your situation!

Thank you

That other laptop (I'm guessing it's gonna turn out to be only for parts) is supposed to be arriving within the next week.

I'm considering switching to Lubuntu.
Even with switching, it has no value in terms of the number of writes to the 128gb.

Not my personal files like fav songs, pics of family and friends...not those because I have those stored on another usb drive.

So, backup...backup...backup.
Even now is extremely critical for me to always backup

Before and after making the switch...

What would be the best strategies for backing up the system data so as to not have to go through trying to recover data from a otherwise non-working thumbstick?

I'm also wanting to backup the apps and packages I installed...some of these may be only for gnome which probably won't be needed for Lubuntu...
ubuntu-restricted-extras
gnome-tweak-tool
Bleachbit
PlayOnLinux
Wine
Winetricks

---

### Post by dragonfly41 on 2021-08-31
> [COLOR=#000000]My budget won't allow new hardware any time soon.[/COLOR]

Taking from this that you are strapped for cash, have you explored
the option of visiting a PC/ hard drive / USB container recycling store?

I resorted to this option in earlier years to configure a new build PC from scrap parts.
I used a LiveUSB to partition several recycled disks in containers and install Ubuntu.

---

### Post by wyattwhiteeagle on 2021-08-31
> **dragonfly41 said:**
> Taking from this that you are strapped for cash, have you explored
the option of visiting a PC/ hard drive / USB container recycling store?

I resorted to this option in earlier years to configure a new build PC from scrap parts.
I used a LiveUSB to partition several recycled disks in containers and install Ubuntu.

Yes that is a venue I have considered.

If this other laptop or it's internal HD fails to work, that is one step closer to the recycle container store.

For some, I'm certain the recycle container store would be the first thing.

I "pep-talk" myself a lot.
Everyone live's according to what life throws at them.
Each individual has to learn how to make lemonade with the lemon's of life.
I'm just going through that process.
It can be a real pain sometime's, but it isn't a good reason for giving up.

---

### Post by wyattwhiteeagle on 2021-08-31
[https://www.addictivetips.com/ubuntu-linux-tips/back-up-the-linux-bootloader-to-usb-for-emergencies/](https://www.addictivetips.com/ubuntu-linux-tips/back-up-the-linux-bootloader-to-usb-for-emergencies/)

Here is one guide I found on the internet.
It mentions saving the GRUB Bootloader files to a text file and using clonezilla to restore the bootloader data.

Are there better ways for my current situation?

---

