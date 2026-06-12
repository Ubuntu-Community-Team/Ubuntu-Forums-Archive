---
title: "unbuntu on usb"
date: 2024-03-12
forum: General Help
---

### Post by jkimble62 on 2024-03-12
i have been able to write install to ISO but cant seem to "Install" on a usb drive. i want to boot to the usb and run unbuntu and SAVE my session just like it was on a ssd in my laptop
is this possible???
i am a newbie and more gui than command line


can anyone recommend a book for me to learn linux... im a windows person (sorry)

---

### Post by tea for one on 2024-03-12
You have two choices:-
(a) A USB device containing Ubuntu with persistent storage (no user account and login not required)
(b) A USB device where Ubuntu has a user account and login is required 

Are you using Windows OS to prepare your Ubuntu usb?
> can anyone recommend a book for me to learn linux... im a windows person (sorry) 
The best introduction to Ubuntu is via a "Try Ubuntu" live session where you can explore ad infinitum (without changing anything on your Windows internal disk)

---

### Post by oldfred on 2024-03-12
You need two USB drives.
One with extracted ISO to boot as installer to install to another drive.
You can instlal to external drives, flash drives, SSDs, or HDDs. But depending on version you are installing may have issues & have to partition in advance to be sure to have an ESP on external drive.

Also flash drives are relatively slow, so a lightweight flavor often works better.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by yancek on 2024-03-12
> i have been able to write install to ISO but cant seem to "Install" on a usb drive. 

What you want to do is not that difficult but you haven't really explained what, if anything you have done so we can't tell you what the next step is.  What does 'write install to ISO' mean?  Generally, one would write the ISO to a DVD or USB/flash drive.  Have you done that?  Have you been able to boot it?  Do you get the option to Try or Install?  Do you have a second USB drive if you are booting from a USB drive?  Do you understand anything about Linux drive/partition naming conventions so you can identify the drives?  If you are a windows user, do you have free space on the drive with windows on it?  You could use Disk Management in windows to shrink the largest windows partition and install there.  If you are planning to install from a DVD or USB to another USB flash drive, just be aware that flash drives will be slow.

---

### Post by C.S.Cameron on 2024-03-12
You can make a full install of Ubuntu to USB drive the same as to internal drive.
[https://askubuntu.com/q/1403792/43926](https://askubuntu.com/q/1403792/43926)

---

