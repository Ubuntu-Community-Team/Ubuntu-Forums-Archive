---
title: "Using Partimage tutorial at Psychocats"
date: 2008-04-30
forum: General Help
---

### Post by weedwacker on 2008-04-30
Hi, Everyone....

I am trying to backup one of my partitions (Ubuntu Feisty) and I am following the very nice tutorial (one of many) at [http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage").

However, I have tried this on two computers running Ubuntu and I can't install partimage per the tutorial.

I find that using the Live CD I cannot install partimage. The message I get after inputting: **sudo apt-get update && sudo apt-get install partimage** tells me:

    [COLOR="Blue"]Fetched 1606 kb in 5s (314 kd/s
    Reading package lists...done
    Reading package lists...done
    Building dependency tree
    Reading state information...done
    Package partimage is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
    E: Package partimage has no installation candidate.
    ubuntu@ubuntu:~$[/COLOR]

I have attempted this on two computers, each running Ubuntu Fiesty, but no soap.

I did get the SystemRescueCD and have attempted to use it, but I must still be somewhat dense about the commands. However, I finally got it working only to get messages that my .tmp is full.

I want to save the backup to my external Seagate HD which is 250G. I have 188G free and my partition that I want to backup is 79G, but only 21G is being used.

I'm flummoxed. I know I am speaking about two problems here, but any suggestions about either would be helpful.

Thanks.

---

### Post by bodhi.zazen on 2008-04-30
You have to enable your repositories on the live CD, then run those commands.

---

### Post by weedwacker on 2008-04-30
Per the tutorial, I thought that was what I was doing:

**sudo apt-get update** && sudo apt-get install partimage

Thanks for the quick response.

---

### Post by bodhi.zazen on 2008-04-30
no, apt-get update updates the list of available packages. Basically, you need to enable the repositories and then refresh the list of available packages.

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by weedwacker on 2008-04-30
Thanks for the clarification!  Will check this out!!

---

### Post by aysiu on 2008-04-30
Did *partimage* move to the Universe repositories already? I'll update my tutorial to mention that.

---

### Post by bodhi.zazen on 2008-04-30
> **aysiu said:**
> Did *partimage* move to the Universe repositories already? I'll update my tutorial to mention that.

It appears so :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=partimage&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=partimage&searchon=name&subword=1&version=all&release=all)

---

### Post by weedwacker on 2008-04-30
> **weedwacker said:**
> Thanks for the clarification!  Will check this out!!

EDIT:  OK! I was reviewing an older psychocats tutorial which did not have the "Update Repositories" link.  This information is very literal! 

While in the live CD environment you go to System>Software Sources and click on the Universe check box and in the next window click on Update.  Then start the rest.  Great!  That part worked for me.

Now I've got to figure out why I'm getting that message about the .tmp being full and it asks for another path when I've directed it to back up there.

I'm thinking I need to clean out my external and reformat it!?

---

### Post by bodhi.zazen on 2008-04-30
Well, my guess is you are running out of RAM (the live CD uses ram for /tmp).

You should be restoring to a partition like /dev/sda1 or some such, the same partition where you made the image.

---

### Post by weedwacker on 2008-05-02
Solved!:)

I found the final piece of information that finally made it click for me so that I could make a copy of my Ubuntu partition and save it to my external Seagate hard drive.

The article named **"Imaging and Restoring your PC with SystemRescueCD"** at [http://alexle.net/archives/229](http://alexle.net/archives/229) in combination with **aysiu's Partimage tutorial** put it all together for me.

In this instance I did use the SystemRescueCD to partimage my Ubuntu partition, but I could just as well have used the Ubuntu **LiveCD partimage method** per aysiu's tutorial.

This is what worked for me:

[LIST=1]
[*]I inserted my SystemRescueCd and shut down the computer.
[*]I plugged in my usb external Seagate hard drive and booted up.
[*]While booting up I hit  the "Delete" key to enter my BIOS and I set the boot option to "boot from CDROM." Then I saved and rebooted.
[*]The SystemRescueCD boots up and then you answer the keyboard question - my keyboard is **"us"**.
[*]Then, at the cursor, I typed in: **mkdir /seagate** and then hit the "Enter" key. It doesn't have to be seagate, it can be **poodle** if you want.
[*]Again, at the cursor, I typed in **fdisk -l** and hit "Enter" to get info about my mounted Seagate external drive - it is **sdd1**.
[*]Next, I typed in: **mount -t ntfs-3g /dev/sdd1 /seagate** and hit "Enter". The **ntfs-3g** is because the Seagate is formatted as ntfs.
[*]Next, I typed in the word: **partimage** and hit "Enter". This fired up the partimage program and I was able to successfully create an image of my partition and save it to my external hard drive. 
[/LIST]
So thank you all for your help.  If anyone has questions, please PM me.

---

### Post by sjmacko on 2008-05-02
I like Ubuntu as much as the next guy, and install it quite a bit for friends and family when it fits their needs.

When I make backups, however, I still reach for my trusty Knoppix CD or DVD. Partimage is included on the live CD by default and works perfectly... I carry the CD and DVD versions in my computer bag whenever I work on anyone's machine. 

Steve

---

### Post by Frank Golden on 2008-05-02
> **weedwacker said:**
> Solved!:)

I found the final piece of information that finally made it click for me so that I could make a copy of my Ubuntu partition and save it to my external Seagate hard drive.

The article named **"Imaging and Restoring your PC with SystemRescueCD"** at [http://alexle.net/archives/229](http://alexle.net/archives/229) in combination with **aysiu's Partimage tutorial** put it all together for me.

In this instance I did use the SystemRescueCD to partimage my Ubuntu partition, but I could just as well have used the Ubuntu **LiveCD partimage method** per aysiu's tutorial.

This is what worked for me:

[LIST=1]
[*]I inserted my SystemRescueCd and shut down the computer.
[*]I plugged in my usb external Seagate hard drive and booted up.
[*]While booting up I hit  the "Delete" key to enter my BIOS and I set the boot option to "boot from CDROM." Then I saved and rebooted.
[*]The SystemRescueCD boots up and then you answer the keyboard question - my keyboard is **"us"**.
[*]Then, at the cursor, I typed in: **mkdir /seagate** and then hit the "Enter" key. It doesn't have to be seagate, it can be **poodle** if you want.
[*]Again, at the cursor, I typed in **fdisk -l** and hit "Enter" to get info about my mounted Seagate external drive - it is **sdd1**.
[*]Next, I typed in: **mount -t ntfs-3g /dev/sdd1 /seagate** and hit "Enter". The **ntfs-3g** is because the Seagate is formatted as ntfs.
[*]Next, I typed in the word: **partimage** and hit "Enter". This fired up the partimage program and I was able to successfully create an image of my partition and save it to my external hard drive. 
[/LIST]
So thank you all for your help.  If anyone has questions, please PM me.I use partimage a lot to backup all of my Linux distros.
I too run it from SystemRescueCD. I usually create an image after an update has proven itself. Use one of the compression schemes, gzip to reduce the size of the resultant image. It takes a little longer to create but the file size is much smaller. Of course if you have a lot of space it doesn't matter.
I have found it isn't required to have your external drive plugged in when you start SystemRescueCD. You can plug it in before you startup partimage and click enter after SystemRescueCD detects the drive.

Partimage has been a lifesaver. It allows me to make risky changes and recover from them if they go bad.

I store my created images on a shared Fat32 partition of the same drive as my Linux install.
It is created much quicker. I can then save the image to any place I want by simply copy and pasting it. I usually save at least on copy to an external drive. Restoring from this Fat32 partition is much quicker also.

---

