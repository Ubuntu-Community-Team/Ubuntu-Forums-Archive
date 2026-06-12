---
title: "How Install System Rescue CD to USB on 16.04"
date: 2016-12-27
forum: General Help
---

### Post by 7-webmaster on 2016-12-27
I have tried to install the System Rescue CD ISO to a USB using the procedure described on the System Rescue CD web site but nothing happens.

[LIST=1]
[*]I downloaded the ISO to  my Downloads directory 
[*]mkdir -p /tmp/cdrom 
[*]sudo mount -o loop,exec Downloads/systemrescuecd-x86-4.9.0.iso /tmp/cdrom 
[*]plug in the USB 
[*]umount the USB by clicking on the up-arrow on the icon for the USB 
[*]sudo bash /tmp/cdrom/usb_inst.sh.  I also tried cd /tmp/cdrom and sudo bash usb_inst.sh 
[*]The script displays /dev/sdb as the only USB device 
[*]I select OK and click enter 
[*]the script terminates without writing anything to the USB 
[*]I cannot see the log file if one is written by the script because everything in /var/tmp is hidden inside gibberish directories which I do not have the authority to look inside 
[/LIST]

I also tried the alternative method:

dd if=Downloads/systemrescuecd-x86-4.9.0.iso of=/dev/sdb
dd: failed to open '/dev/sdb': Permission denied
jcobban@jcobban-laptop:~$ sudo dd if=Downloads/systemrescuecd-x86-4.9.0.iso of=/dev/sdb
dd: failed to open '/dev/sdb': No medium found

So how do I install System Rescue CD to a USB on Ubuntu 16.04?

---

### Post by sudodus on 2016-12-28
It would make it easier for to help, if you tell us a few things:-)

- Which version of System Rescue are you trying to install?

- Did you check with md5sum, that the download was good?

- How is your target USB drive seen by the current opertating system? Please run the following command lines and post the output (within CODE tags).

```
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Otherwise we can only guess.

These [instructions](https://www.system-rescue-cd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick#A.29_Recommended_USB_installation_method_from_Linux_using_isohybrid) work for me:

> A) Recommended USB installation method from Linux using isohybrid.

If you are running Linux on your computer and have isohybrid installed it's very easy to install SystemRescueCD on a USB stick. You just have to download the ISO image of SystemRescueCD, and then run isohybrid to prepare the iso image for booting from an USB stick. The prepared iso image can then be written to an USB stick using dd. Writing to the USB stick with dd will remove all its content, so make sure you don't need the data or make a backup first.

    Download the latest SystemRescueCd ISO image from the Download page
    **Run isohybrid /path/to/systemrescuecd-x86-x.y.z.iso. This will modify the iso in place.**
    Plug in your USB stick and wait 5 seconds to allow enough time for the system to detect it
    Unmount the USB stick if auto-mount is enabled or if it was already mounted
    Run dd if=/path/to/systemrescuecd-x86-x.y.z.iso of=/dev/sdx in a shell where sdx is the USB stick


***This is what I guess: You forgot to treat the downloaded file with isohybrid***, or ***you did not identify the target drive correctly***.

I would also take the opportunity to warn you, that ***dd*** is very powerful but also very dangerous. It does what you tell it to do without questions. If you tell it to wipe the family pictures ... and it is only a minor typing error away. For this reason I made mkusb in order to wrap a safety belt around dd. ***mkusb*** will help you select the correct target drive. See this link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by 7-webmaster on 2017-02-01
> **sudodus said:**
> It would make it easier for to help, if you tell us a few things:-)

- Which version of System Rescue are you trying to install?

- Did you check with md5sum, that the download was good?

- How is your target USB drive seen by the current opertating system? Please run the following command lines and post the output (within CODE tags).

```
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Otherwise we can only guess.


I simply downloaded the most recent version of the System Rescue CD from the site.

I do not currently have access to the computer on which I was attempting the install, so I cannot run the commands.  I gave up on trying to make the USB image, when out bought some DVDs and wrote the image to one of them.

How could I have incorrectly identified the USB drive when the SCRIPT chose the identification.  I only confirmed the SCRIPT's choice.  

My concern is that the documentation on how to create the USB image is flawed.  There is no mention of isohybrid in that documentation so how am I supposed to know about it?

---

### Post by sudodus on 2017-02-02
I'm glad that you found a way to boot your computer with System Rescue CD (even if we could not help you to boot from USB) :-)

-o-

I do not know if or how you could have incorrectly identified the USB drive. I was only suggesting a possible cause to your problem.

The internet has no master editor. There are good documents and not so good documents. There are even alternative facts ;-) It helps to ask for and search for help at many web sites, and search deeper, when you find contradicting information.

---

