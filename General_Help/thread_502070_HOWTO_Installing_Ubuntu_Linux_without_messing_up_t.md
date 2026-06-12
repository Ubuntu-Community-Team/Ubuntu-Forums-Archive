---
title: "HOWTO: Installing Ubuntu Linux without messing up the mbr"
date: 2007-07-16
forum: General Help
---

### Post by t_tovenaar on 2007-07-16
In the process of finding out which Linux flavor is the right one for me I’ve tried several distros such as Mandrake (Mandriva), SuSe, Red Hat and Gentoo. Somehow I didn’t manage to get things up and running; there was always something I couldn’t get configured. After all of these attempts I always had to reinstall Windows because I couldn’t undo the installation of grub. :(

A few months ago I decided to give it another try and installed Ubuntu Linux. Mainly because I am starting to take a dislike to Windows… 
Some friends of mine are using Linux for quite a while and are all very enthusiastic about the operating system. Knowing it would take me some time to get used to Linux I was resolute to keep my Windows installation this time.

Before taking the big plunge into the marvelous world of Linux I did some searching on the web and found this great article from [Matthew Miller]("http://www.matthewjmiller.net"): [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) in his article Matt describes how to install Ubuntu Linux alongside a running installation of Windows XP but **without messing up the Windows master boot record** (mbr). 
Although he wrote the article for his type of laptop, I believe the major part the article is applicable for all types of computer systems.

The procedure to follow is really easy and can be executed by (almost ;)) anyone. Basically the steps he describes are:

[LIST=1]
[*]Defrag your harddisk so you can make a new partition for the Linux installation
[*]Use the QTParted tool (in fact a Partition Magic clone) to resize your Windows partition and create the new partition(s).
[*]Install Ubuntu Linux
[LIST]
[*]At the part about partitioning choose to edit the partitions manually and make syure you don't do anything to the Windows partition.
[*]At the part about GRUB make sure you choose NOT to install GRUB in the MBR!
[/LIST]
[*]Boot from the [Linux System Rescue CD]("http://www.sysresccd.org/") and create a boot image that can be included in the Windows boot.ini file.
[LIST]
[*]Execute the following command to create the image.
```
dd if=/dev/hda2 of=/mnt/<your windows partition>/_ubuntu.bin_ bs=512 count=1
``` 5.Reboot into Windows and modify the boot.ini file.
[*]Edit the boot.ini and add the following line to the end of the file:
```
C:\_ubuntu.bin_="Ubuntu Linux"
```
[/LIST]
[*]Reboot the computer. This time, you should see a screen during booting that asks you to choose between Windows and Ubuntu Linux. Choose Ubuntu Linux and let the Ubuntu install process finish.
[/LIST]

As you can see, the few words I have written down don't cover the entire process. This is done deliberately for I want you to check out the [full article]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") on  [Matt's site]("http://www.matthewjmiller.net") if you're really interested in how to get this installation going as expected. After all, I'm just a newb and I don't want to take the credits Matt deserves.

There's more in his article but I only needed the first two steps of it :)

---

### Post by frodon on 2007-07-16
> **t_tovenaar said:**
> In the process of finding out which Linux flavor is the right one for me I&#8217;ve tried several distros such as Mandrake (Mandriva), SuSe, Red Hat and Gentoo. Somehow I didn&#8217;t manage to get things up and running; there was always something I couldn&#8217;t get configured. After all of these attempts I always had to reinstall Windows because I couldn&#8217;t undo the installation of grub. :(You don't have to do so, just boot your windows CD then enter the DOS mode and use the fixmbr command that's all ;) :
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

So it's not a problem to write something on the MBR since you can easily fix it with the OS of your choice.

---

