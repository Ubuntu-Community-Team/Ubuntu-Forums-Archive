---
title: "Ubuntu on USB"
date: 2020-12-23
forum: General Help
---

### Post by llama99 on 2020-12-23
I'm trying to create a Ubuntu bootable flashdrive so that I can use it on my HP Stream laptop as the operating system (without installing it).  I went to this website for the downloading: [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I downloaded "something" on the USB, not sure if I downloaded the right thing.  I chose the option that doesn't retain any settings etc. to the flashdrive.  At first I got an error message saying, "UUI couldn't find a configuration file.  Ubuntu cannot be installed using this option."

But then something was installed.  I have these files on the USB: uui, license, Uni-USB-Installer-Copying, and Uni-USB-Installer-Readme. None of these seem to allow for using Ubuntu on the flashdrive.  Am I missing something? If not, how do I use these files?

I'm new to Ubuntu and have a second thread pertaining to creating a bootable USB stick for use on a Mac.

Thanks for any assistance.

---

### Post by CelticWarrior on 2020-12-23
The software you mention is for Windows only. Meaning: It is intended to be run from Windows, not OSX.
[B]And obviously it isn't to be downloaded or run from the USB stick you want to use for the Ubuntu installer or Ubuntu installer with persistence.
[/B]
If you actually follow the instructions in the link you provided it should work.

---

### Post by tea for one on 2020-12-23
Here is another site for perusal:-

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

You will need 4GB RAM to use Ubuntu in a [COLOR="#0000FF"]live[/COLOR] session.

If you have only 2GB, then have a look at Xubuntu or Lubuntu.

---

### Post by llama99 on 2020-12-23
Thanks, I'll try that last link if I can't get the original one to work.  I went back to:  [https://www.pendrivelinux.com/univer...easy-as-1-2-3/]("https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and gave it another shot.  I wasn't able to provide an ISO file which stopped the whole process.  How do I come up with one of those?

I'll quote what someone wrote elsewhere which shows what I'm trying to do:  "T[COLOR=#282828][FONT=helvetica]he [/FONT][/COLOR]**hdd **[COLOR=#282828][FONT=helvetica]can be bypassed by[/FONT][/COLOR][COLOR=#282828][FONT=helvetica]creating a Linux Ubuntu bootable flash drive and use Ubuntu without installing it. It will use all[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]of the computer's hardware except the **hdd**.  It would be best to use[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]an 8 GB flash drive. Here is one website that tells you how to do that and will create the bootable[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]flash drive: [Universal USB Installer - Easy as 1 2 3 | USB Pen Drive Linux]("https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]
[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]"With Ubuntu you have two choices....one will not retain anything to the flash drive and the other is[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]to create one that retains settings and other things such as bookmarks and passwords on your browser. . .[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]
[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]"I am using Ubuntu as my main OS. I only boot up Windows 10 once a month or so to keep it updated."[/FONT][/COLOR]

---

### Post by coffeecat on 2020-12-23
> **llama99 said:**
> I wasn't able to provide an ISO file which stopped the whole process.  How do I come up with one of those?

It's the self same ISO that you downloaded for your other thread. 

By the way. You probably don't need to make one bootable USB for a Mac and one for a Windows PC. With one or two exceptions, bootable Ubuntu USBs made from ISOs will boot up on most machines. 

Why not simply follow the Mac tutorial, but this time **read the instructions right through to the end** without making assumptions?

---

### Post by crip720 on 2020-12-23
Do you want a full install of Ubuntu on a USB stick or just the Ubuntu live install with persistance?  A full install requires two USB sticks, one for the installer and another bigger one to install to.

---

### Post by llama99 on 2020-12-24
I'm looking for a full install of Ubuntu on a USB drive.  I do have two USB drives, both of then 16 GB.  I'm going to go ahead and follow these steps from the Mac tutorial:  [https://ubuntu.com/tutorials/create-...cos#1-overview]("https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview") after I iron out the proper steps.

---

### Post by CelticWarrior on 2020-12-24
It's really really not that difficult.

Download Ubuntu 20.04 LTS from [here]("https://ubuntu.com/download/desktop/thank-you?version=20.04.1&architecture=amd64").
-or-
Download Ubuntu 20.10 from [here]("https://ubuntu.com/download/desktop/thank-you?version=20.10&architecture=amd64").

Make sure the ISO file is saved in known, easy to find location (Downloads, ...)

Connect the pen you want to use for the installer and follow the remaining instructions [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)

If you describe exactly which part you don't understand we may be able to clarify:
Download the ISO file > Launch Disk Utility > insert USB stick (for the installer), select it and Erase (msdos format / GUID) with Disk Utility > Download and run [Balena Etcher]("https://www.balena.io/etcher/") for Mac > Select the ISO file (select image) and confirm or change the destination USB drive > Flash

---

### Post by llama99 on 2020-12-24
Thanks, I did figure out what had confused me.  Anyhow I ran into a snag which I described in the other thread:  [https://ubuntuforums.org/showthread.php?t=2455611&page=2](https://ubuntuforums.org/showthread.php?t=2455611&page=2)

---

