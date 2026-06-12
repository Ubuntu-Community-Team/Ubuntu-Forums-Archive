---
title: "installing ubuntu to an external usb hard drive"
date: 2006-07-26
forum: General Help
---

### Post by shoggoth on 2006-07-26
so i followed the directions from [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
and im now at step four. everything before this step has worked correctly and ive made a reply in that thread for help but i just now noticed its in a previous releases forum so i thought i would post and ask for help here where more people are prolly at. my orignal post is on the last page of that thread but please reply here.

I do not know what i should be booting from on step four. Im using dapper drake alternative install cd and booting from it does give me the option of rescuing an install on other drives. booting directly from the external drive doesnt seem to work.

thanks for any help.

---

### Post by shoggoth on 2006-07-26
bump

---

### Post by jimmygoon on 2006-07-26
> **shoggoth said:**
> so i followed the directions from [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
and im now at step four. everything before this step has worked correctly and ive made a reply in that thread for help but i just now noticed its in a previous releases forum so i thought i would post and ask for help here where more people are prolly at. my orignal post is on the last page of that thread but please reply here.

I do not know what i should be booting from on step four. Im using dapper drake alternative install cd and booting from it does give me the option of rescuing an install on other drives. booting directly from the external drive doesnt seem to work.

thanks for any help.
You gotta give it more than 10 minutes for a bump, anyways,

That step 4 says load rescue.... so go ahead and load the rescue stuff

---

### Post by b.treu on 2006-10-14
You don't need to go through all of this.[-X  You can do the install SIMPLY and completely through the GUI. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.\\:D/ 

Best to all!

---

### Post by jman6495 on 2007-06-04
Help me I Tryed 2 do it the normal way and i got ERROR LOADING OPERATING SYSTEM
please Help
Jman6495

Linux Rox :D

---

### Post by tedrogers on 2007-07-05
I'm getting the "Error loading operating system" message as well.

The first time I set it all up it worked fine. It booted from USB and I checked it out. Then I did an update in Dapper and it filled up my casper-rw partition! Oops.

So I thought I'd increase the partition size of casper-rw and try again..and ever since then, doing exactly the same as before (expect larger casper-rw partition), I get this annoying error.

Is my MBR knackered or something and if so how do I fix it?

Or is it something else entirely?

Thanks.

---

### Post by tigerjuju on 2007-09-05
I followed the instructions trying to install Ubuntu 7.04 onto my 2GB Sandisk Cruzer Micro. I also got the "Error loading operating system" trying to boot from the USB stick. Does any one know what may be the problem?

---

