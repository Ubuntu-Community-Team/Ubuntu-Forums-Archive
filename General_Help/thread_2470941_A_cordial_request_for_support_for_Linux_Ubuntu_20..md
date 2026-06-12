---
title: "A cordial request for support for Linux Ubuntu 20.04 LTS - no tools needed in Gparted"
date: 2022-01-17
forum: General Help
---

### Post by luke1608 on 2022-01-17
Hello, please send me information on how do I get these tools installed for GParted?

---

### Post by &amp;KyT$0P# on 2022-01-17
Just install it the normal way from the standard Ubuntu repositories -
```
sudo apt-get install ntfs-3g
```

---

### Post by luke1608 on 2022-01-17
There is only one command for this tool to work?

I have Linux Ubuntu as Live on USB.

I have Linux Ubuntu on USB. Can I go further or do I need to install to an internal SSD?

---

### Post by CharlesA on 2022-01-17
Yes. Based on the error you see in gparted, it sounds like the drive or file system is damaged. Since it's NTFS, you can try using ntfsfix (assuming it's still in Ubuntu 20.04), or boot into Windows and run chkdsk on it and then try again.

What are you trying to accomplish?

---

### Post by luke1608 on 2022-01-17
Ok done, how can I check if it will continue to work?

I'm trying to create a bootable PenDrive with Win 7.

By this method on YouTube> [https://www.youtube.com/watch?v=rJQk9KVekFI](https://www.youtube.com/watch?v=rJQk9KVekFI)

---

### Post by CharlesA on 2022-01-17
It looks like you were trying to create a new vfat file system, not repair the existing ntfs file system.

What are you trying to do? Create a new partition on this drive or access the existing one?

EDIT: This will probably be easier to do:
[https://superuser.com/questions/1214227/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](https://superuser.com/questions/1214227/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)
[http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html](http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html)

You can use the same method for Windows 7, 8 and 10.

---

### Post by luke1608 on 2022-01-17
> **CharlesA said:**
> It looks like you were trying to create a new vfat file system, not repair the existing ntfs file system.

What are you trying to do? Create a new partition on this drive or access the existing one?

EDIT: This will probably be easier to do:
[https://superuser.com/questions/1214227/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](https://superuser.com/questions/1214227/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)
[http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html](http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html)

You can use the same method for Windows 7, 8 and 10.

The following packages have unmet dependencies:
  woeusb: Requires: p7zip-full but cannot be installed
           Depends: libwxbase3.0-0v5 (> = 3.0.4 + dfsg) but cannot be installed
           Depends: libwxgtk3.0-0v5 (> = 3.0.4 + dfsg) but cannot be installed
E: Could not fix problems, corrupt packages stopped.

---

### Post by CharlesA on 2022-01-17
Try adding the universe repo and see if it'll install p4zip-full.

See here:
[https://www.how2shout.com/linux/how-to-install-p7zip-gui-on-ubuntu-20-04-lts/](https://www.how2shout.com/linux/how-to-install-p7zip-gui-on-ubuntu-20-04-lts/)

---

### Post by dragonfly41 on 2022-01-17
You might try running Rufus on Windows to create a bootable flash for Ubuntu installation.

---

### Post by luke1608 on 2022-01-18
Hello, I installed a Linux Ubuntu 20.04 LTS laptop on the hard drive. The system is after the commands: 1 - sudo apt-get upgrade, and sudo apt-get update, and after sudo apt-get autoremove. I inform you that after performing the above steps, I completely removed the Gparted applications.

Hello, I wanted to send you a video on the forum. I have installed OBS Studio but cannot save the Video image. By default, I cannot save the Video image. OBS Studio - only saves Audio tracks for me.

So that I can get further support on Gparted - I need to record a Video. OBS Studio is not working for me. I am creating a new thread on the forum.

Please Support Me this Topic > [https://ubuntuforums.org/showthread.php?t=2470968&p=14076134#post14076134](https://ubuntuforums.org/showthread.php?t=2470968&p=14076134#post14076134)

> **CharlesA said:**
> Try adding the universe repo and see if it'll install p4zip-full.

See here:
[https://www.how2shout.com/linux/how-to-install-p7zip-gui-on-ubuntu-20-04-lts/](https://www.how2shout.com/linux/how-to-install-p7zip-gui-on-ubuntu-20-04-lts/)

I'm confirm step by step install > [https://linuxways.net/centos/how-to-install-gparted-on-ubuntu-20-04/](https://linuxways.net/centos/how-to-install-gparted-on-ubuntu-20-04/)

He presents me, I can't go any further.

I have no way to send info from the CMD Console. Downloading Video by OBS Studio does not work for me.

---

### Post by oldfred on 2022-01-18
You cannot use gparted on mounted partitions, or the system you have just installed. so gparted uninstalled.
I have multiple drives, so do re-install gparted, but can only use it for my second drive or external drives when not mounted.
Otherwise you need to use gparted from Ubuntu live installer in live mode.

I have found since I leave unallocated space on gpt drive, I can create a new partition as long as I am not changing any mounted partitions. 
Since old MBR(msdos) had 4 primary partition limit and extended partition was always mounted if any logical partition was mounted, you usually could not use gparted with MBR at all. One more minor advantage of gpt over old MBR.

---

### Post by luke1608 on 2022-01-18
> **oldfred said:**
> You cannot use gparted on mounted partitions, or the system you have just installed. so gparted uninstalled.
I have multiple drives, so do re-install gparted, but can only use it for my second drive or external drives when not mounted.
Otherwise you need to use gparted from Ubuntu live installer in live mode.

I have found since I leave unallocated space on gpt drive, I can create a new partition as long as I am not changing any mounted partitions. 
Since old MBR(msdos) had 4 primary partition limit and extended partition was always mounted if any logical partition was mounted, you usually could not use gparted with MBR at all. One more minor advantage of gpt over old MBR.


I have no way to send info from the CMD Console. Downloading Video by OBS Studio does not work for me.

Could you please send me the commands to be typed into the Konsole. To update OBS Studio yourself? Why is he not recording the Image for me?

I do not understand this. I have everything Ok according to Gparted on partitions in Linux Ubuntu, but still I cannot create an install with an ISO image of Windows 7. Can you help me further? Take a look at the screenshot.

Please help me in this thread about OBS Studio.

Because according to Gparted booting with PenDrvie USB from Linux Ubuntu it's OK.

Please Give me Support Update Tools [UNetbootin]("https://unetbootin.github.io/").

I'm Confirm You Run [UNetbootin  S]("https://unetbootin.github.io/")ucces Today.

Please Next Support Me.

---

### Post by oldfred on 2022-01-18
I know nothing about OBS Studio.

Windows 7 is very obsolete. Better to use current version of Windows.
New systems are UEFI with gpt partitioning.

Windows 7 was usually BIOS with MBR partitioning, but could be installed in UEFI mode either modifying USB drive to have UEFI boot files or having the updated Windows 7 ISO that included those files.

You cannot install a BIOS version of Windows to gpt drive without totally erasing drive. 
And Windows in UEFI mode needs lots of partitions, generally best to just let Windows create partitions it wants into unallocated space on gpt drive.

---

