---
title: "What does &quot;mount&quot; mean?"
date: 2013-02-21
forum: General Help
---

### Post by Geunor on 2013-02-21
Hi everybody.

Sorry for the silly question. 

I have turned on the laptop, which has been partitioned with Ubuntu and Windows 7 50/50, and it has come up with an error saying that it cannot load the Grub so I need to fix this some how. I have looked at a step-by-step on the link below and it is telling me to "Run: Mount". 

[http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)

I have no idea what that means. Can anyone explain what that means and give a step-by-step as to how to do it on Ubuntu please? 

I have another machine running Ubuntu so I will be placing the Super Grub2 Disk onto a USB so that I can boot up through that.

Thank you in advance.

---

### Post by PowerBarry43 on 2013-02-21
Hi

Ok basically mounting means telling your system where to put your storage device in your filesystem so if you mount /media/cdrom which is the path to your cd drive (this is a file that represents a device not a folder that you can open up and browse through) to a folder called /cddrive (this folder would be called the "mount point") you can then browse inside the folder and see whats on your cd. Mounting applies for all kinds of storage from cd drives to usb sticks to partitions on your hard drive.

With regard to your boot problems supergrub will help you and you probably don't need to mount anything unlike recovering from a livecd. just boot up run:

```
sudo grub-install /dev/sda
sudo update-grub
```

Hope this helps!

Barry

---

### Post by Drenriza on 2013-02-21
When looking at the title, i guess it depends how you look at it.

What are you mounting?

When mounting a HDD, SSD, USB e.c.t. You need to tell your filesystem where to make the resources on the device available. Aka you mount the device to make your files available to you.

---

### Post by Geunor on 2013-02-21
> **PowerBarry43 said:**
> Hi

Ok basically mounting means telling your system where to put your storage device in your filesystem so if you mount /media/cdrom which is the path to your cd drive (this is a file that represents a device not a folder that you can open up and browse through) to a folder called /cddrive (this folder would be called the "mount point") you can then browse inside the folder and see whats on your cd. Mounting applies for all kinds of storage from cd drives to usb sticks to partitions on your hard drive.

With regard to your boot problems supergrub will help you and you probably don't need to mount anything unlike recovering from a livecd. just boot up run:

```
sudo grub-install /dev/sda
sudo update-grub
```Hope this helps!

Barry

Hi Barry,

Thank you for your time and help. The explanation is good, so thank you for that. So when it asks me to "Run: mount" what do I do exactly? [http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)

I cannot run anything on the laptop which is broken. I end up getting the message:

      error: unknown filesystem
      grub rescue>

I also do not have the live CD at this house. It is at another family members house.

So I was thinking that this error could be fixed by putting the Super Grub2 Disk .iso onto a USB stick via another laptop using Ubuntu and then placing it into the broken laptop and boot using the USB stick?

Thank you for your time.

---

### Post by Geunor on 2013-02-21
> **Drenriza said:**
> When looking at the title, i guess it depends how you look at it.

What are you mounting?

When mounting a HDD, SSD, USB e.c.t. You need to tell your filesystem where to make the resources on the device available. Aka you mount the device to make your files available to you.

Thank you for your reply. 

With the first definition, how do I mount the device to make the files available? Does that mean just plug in the USB stick into the port or do I have to do something else as well?

Thank you for your help.

---

### Post by dino99 on 2013-02-21
if your ubuntu installation is made following the standard way, then the system itself is clever enough to set what you need, without scratching your hairs  :p

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: your issue means, either grub has not been installed (its the bootloader), or the root partition (/) where the system is installed is not set as bootable (flag you need to set while formatting)

---

### Post by Geunor on 2013-02-21
> **dino99 said:**
> if your ubuntu installation is made following the standard way, then the system itself is clever enough to set what you need, without scratching your hairs  :p

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: your issue means, either grub has not been installed (its the bootloader), or the root partition (/) where the system is installed is not set as bootable (flag you need to set while formatting)

Thank you for your response.

I am unable to actually get onto the Operating System on the broken laptop. I have tried pressing F8 while starting up the laptop to see if I can enter a recovery mode but it still goes onto the grub error screen on start-up so I cannot do the instructions that are in the link that you have sent. 

The bootloader was working fine before but has decided to not even load since yesterday. 

Do you think that I should start a new thread titled "How to install Super Grub2 Disk via USB stick from an Ubuntu machine step-by-step"?

I am such a noob so will need an actual step-by-step detailed description rather than getting stuck on the second step of this link [http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make) because I don't know what mount means.

Thank you for your help.

---

### Post by schragge on 2013-02-21
Wait a minute, the linked page describes how to make an SGD USB from inside a working Linux installation. That's where you run *mount* and other commands described there. If you don't have a working Linux system, then look further down the page. E.g., the instruction for Windows starts with the words> Download Unetbootin For Windows

---

### Post by Geunor on 2013-02-21
> **schragge said:**
> Wait a minute, the linked page describes how to make an SGD USB from inside a working Linux installation. That's where you run *mount* and other commands described there. If you don't have a working Linux system, then look further down the page. E.g., the instruction for Windows starts with the words

Boom! Genius. Thank you for your help. Have done this and managed to boot it up using SGD.

It comes up with an Error 15 though when trying to fix the GRUB. I have made a new thread as this new problem is off topic to this thread. 

Thank you to all who contributed. It is much appreciated.

---

