---
title: "USB drive - why can't it behave like Windows?"
date: 2013-02-05
forum: General Help
---

### Post by luckylee on 2013-02-05
Why do I have to eject/unmount a USB drive? Unlike in Windows, which is very easy - you don't need to remember mount/unmount. Can anyone explain?

---

### Post by TOMBSTONEV2 on 2013-02-05
Ideally you are supposed to unmount the drive in windows as well. Windows just has settings (I think its called quick removal and better performance) The quick removal method in windows actually slows down the functioning of the device to some degree. In windows I always used "safely remove hardware" which is the same as unmount or sudo umount because I have had data corruption in windows with quick removal.

I also believe the whole mounting and unmounting a volume give you more control, thus more security. If you have a volume plugged in and you decide you do not wish to have the system recognise the volume you can just unmount it. If someone hacks your system whilst it is not mounted they will not likely get your data. (Mind you this is just my speculation)

As to why can't it behave like windows? Well ubuntu is linux, not windows.. Why can't dogs behave like cats? They are not the same thankfully. Really ultimately unmounting it ensures the data remains safe, and is that not what we all want in the end? Safe data? I sure do. :p

---

### Post by Cheesemill on 2013-02-05
You do have to unmount a USB drive in Windows or you will risk using data.

This is done by right-clicking in Windows Explorer and selecting 'safely remove hardware'.

---

### Post by haqking on 2013-02-05
> **luckylee said:**
> Why do I have to eject/unmount a USB drive? Unlike in Windows, which is very easy - you don't need to remember mount/unmount. Can anyone explain?

because a) Linux is not windows and b) you do need to or should unmount in windows too

---

### Post by MorrisMonkey on 2013-02-05
In Windows, I always go to My Computer, find the icon for the USB drive, right click and select eject, I wait until the information about the file system has disappeared from the information panel on the left.
I think Windows and Linux work exactly the same with USB, you have to wait until the computer has finished reading or writing data before removing the drive, hope this helps.

---

### Post by TOMBSTONEV2 on 2013-02-05
Technically in windows if quick removal is selected, you don't have to unmount the volume first. Though you still should anyway.

---

### Post by collisionystm on 2013-02-05
> **luckylee said:**
> Why do I have to eject/unmount a USB drive? Unlike in Windows, which is very easy - you don't need to remember mount/unmount. Can anyone explain?

As stated, your *supposed to *do this in Windows too. What the Eject/umount does it tells the operating system to finish writing any data to the drive that it has buffered. 
So lets say you are copying a large file to your thumb drive, the progress bar says it finished but the light on the drive is still flashing with read/writes. That is because the system has buffered data it is still sending. If you eject the drive during this process you MIGHT corrupt a portion of the file.

Personally I never use the Eject or unmount. I just wait till the light is finished blinking and then pull the drive. Never had issues. Ever.

---

### Post by Habitual on 2013-02-06
> **luckylee said:**
> Why do I have to eject/unmount a USB drive? Unlike in Windows, which is very easy - you don't need to remember mount/unmount. Can anyone explain?

That's the trouble "***you*** don't need to remember mount/unmount".

Windows is not Linux.
Linux is not Windows.

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Stonecold1995 on 2013-02-07
Pretty much what everyone else said, Linux simply isn't Windows.

But I think mounting with the "sync" option may simulate what Windows does (although I'm not sure, just a guess based on viewing the manual for "mount").

---

### Post by luckylee on 2013-02-07
Thanks for the response.

First of all - Windows disable write caching on all removeable drive. How can I set this option in /etc/fstab for all removeable drives (including USB drive) ?

> **Cheesemill said:**
> You do have to unmount a USB drive in Windows or you will risk using data.

This is done by right-clicking in Windows Explorer and selecting 'safely remove hardware'.

---

### Post by luckylee on 2013-02-07
How do I set this option as the default for all removable drive (i.e. sync instead of async)?

> **Stonecold1995 said:**
> Pretty much what everyone else said, Linux simply isn't Windows.

But I think mounting with the "sync" option may simulate what Windows does (although I'm not sure, just a guess based on viewing the manual for "mount").

---

### Post by travalon on 2013-02-07
> **luckylee said:**
> Why do I have to eject/unmount a USB drive? Unlike in Windows, which is very easy - you don't need to remember mount/unmount. Can anyone explain?
If you want less control use windows. Remember "delayed write failed"?
Linux is for people who want more control of their machine. So you will have to do some mundane things your self. Besides it's good practice for attention to detail.

---

### Post by luckylee on 2013-02-07
>Linux is for people who want more control of their machine.

Then I want to control how the mounting option behaves. Is it in /etc/sysconfig ... /etc/fstab ... ? Is there the option to do this? If not then this is considered as a system defect.

How do I set this option as the default for all removable drive (i.e. sync instead of async)? 

By the way, Windows disables write caching for all removable drives and I can take the USB stick out after it finishes copying without me having to mount/unmount and there has never been a corruption (unless if I take the usb stick out during write).

> **travalon said:**
> If you want less control use windows. Remember "delayed write failed"?
Linux is for people who want more control of their machine. So you will have to do some mundane things your self. Besides it's good practice for attention to detail.

---

