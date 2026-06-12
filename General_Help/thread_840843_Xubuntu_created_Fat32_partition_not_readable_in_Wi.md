---
title: "Xubuntu created Fat32 partition not readable in WinXP"
date: 2008-06-25
forum: General Help
---

### Post by nerver on 2008-06-25
Hey all,

I'm still fairly new to linux, so if theres a really obvious answer to this I apologize. Here is the problem I am facing:

I bought an 8G USB flash drive that I wanted to put a Live Xubuntu copy on. I followed the instructions here:

[http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/")

but instead of using the rest of the entire drive for the casper partition I capped it at 4G and made a 3rd partition (4G Fat32) to use for storing various files on so they would be accessible through XP, OSX etc.

Now, the install of a Xubuntu live went through fine, and Xubuntu can see and write/read the Fat32 partition just fine, but when i boot into WinXP, it does not show up as a drive. It shows up in the Disk Manager, but I cannot format, delete, change drive letter or anything with it, I just get an error saying that the partition is not active and I need to restart the computer to make it active. Rebooting the computer does nothing though, I boot into windows again and get the same error.

Does anyone have any idea what could be causing this?

Thanks for the help :)
Cheers,
-Sean

---

### Post by nerver on 2008-06-26
Ok, figured out what the problem is. It has nothing to do with the partitions themselves, apparently Windows XP detects USB flash drives as removable media (like a cd or dvd) and as such doesn't allow you to partition them and also, even though it may recognize that the drive has more than one partition, it will only allow one to be accessible. Seems kind of dumbt to me, but then again it is Windows.

Cheers,
-Sean

---

