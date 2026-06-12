---
title: "Windowds boot messed up after ubuntu install on flash"
date: 2020-04-08
forum: General Help
---

### Post by thatoneuser2 on 2020-04-08
I am not well versed at linux but can understand at least basic stuff.  Having an issue with booting into windows after installing ubuntu on to a flash drive on a chromebook.
I will try to keep this as concise as possible.

Issue:  Booting the computer normally dumps me on to grub (command line) after installing ubuntu on to a flash drive.  I can get into windows but only with the ubuntu flash drive plugged in. How do I fix it so I can boot into windows with no user inputs and no flash drive needed (back to stock).
  
Extra info?:  
[LIST]
[*]starting the pc and trying to load the boot menu (f12) with the flash drive plugged the options are 1.ubuntu 2.eMMC Card: (this is the windows drive)
[*]starting the pc without the flash drive plugged in and selecting the "eMMC" dumps me into grub command line.  typing "exit" tries to start windows again but again, dumps me back to grub command line.
[*]starting the pc with the flash drive plugged in default loads grub with the options 1.ubuntu 2.advanced options 3.windows boot manager (on /dev/mmcblk0p2) 4.system setup
[*]Starting windows from grub (opt 3) with flash drive plugged in works as normal and am able use the OS as normal.
[*]I do not have access to the BIOS
[*]I installed ubuntu to the flash drive not the hard drive.  This was not a dual boot setup.  I wanted to be able to load ubuntu manually via boot menu when the flash drive was plugged in and have windows load normally otherwise.
[/LIST]

I have tried to find a fix but haven't found anything yet.  I ran lilo but that did nothing.  I tried "sudo lilo -M /dev/sda1 mbr" (assuming sda1 would be the hdd) and the "/dev/mmcblk0" dir which came back with it is not a master device with primary partition table.

If I need to share any more information just ask.  Any help would be amazing, thanks.

---

### Post by yancek on 2020-04-08
You indicate that you have both windows and Ubuntu installed but neglected to indicate which version/release of each you have and that is significant and needed info. The best option for you is to go to the site at the link below and download and run the boot repair script.  On that page you will see 2nd option which explains how to get boot repair while booted into Ubuntu.  This will give a more current version of boot repair so use that.  When you run boot repair make certain you ONLY select the option to Create BootInfo Summary and do not try to make and repairs.  You will get a link when it finishes which you can post here and it will likely provide enough information for someone to explain how to fix the problem.  Without this info there will just be guessing and there are a lot of possibilities.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Frogs Hair on 2020-04-08
> Having an issue with booting into windows after installing ubuntu on to a flash drive on a chromebook  Did you use a workaround to get windows installed on the chrome book since it's not officially supported?

---

### Post by thatoneuser2 on 2020-04-08
> Did you use a workaround to get windows installed on the chrome book since it's not officially supported?
Nope, started with a live usb version just to test if it would run and it worked fine.  Figured I would try to install on to a flash drive so I had the option of running ubuntu as well as windows.


> You indicate that you have both windows and Ubuntu installed but  neglected to indicate which version/release of each you have and that is  significant and needed info.
I'm sorry, it is Ubuntu 18.04.4 LTS and Windows 8 (i assume 8.1).  This is on a lenovo 100e ver 1 chromebook.


> The best option for you is to go to the site at the link below and download and run the boot repair script.... You will get a link when it finishes which you can post here and it will  likely provide enough information for someone to explain how to fix the  problem.

I ran the script on ubuntu installed on the flash drive and not from another live usb if that matters. 
[http://paste.ubuntu.com/p/xNTz6HbJvZ/](http://paste.ubuntu.com/p/xNTz6HbJvZ/)

---

