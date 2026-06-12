---
title: "Problem with file/folder permissions"
date: 2007-10-02
forum: General Help
---

### Post by Masiv on 2007-10-02
I have searched and looked and dug and did everything I could, but I cannot find a way to modify my folders permissions, and I am close to the end of my rope.

Here is the situation: I want to set up an FTP directory so my family can share pictures. Simple enough. The drive upon which I would like to create this directory never shows up in fstab, so that is weird thing #1. In addition, I cannot change the default permissions of this drive. The drive is formatted in fat32, and no amount of chmodding or chowning or right clicking is letting me change the permissions.

I tried to create a folder and just change those permissions, but again, I am present with the same error: You do not have the permissions necessary to change the group of "Pictures". This is when I am logged in as Root, which I know I should NEVER do.

I cannot seem to figure out what the problem is. I would understand if I weren't following directions or installed something wrong, but I have tried pretty much everything that I could find on this topic. I read talk that vfat partitions need to be modified in the fstab entry for anything to be changed on them, but when I mount my drives, nothing about them enters into the fstab entry. They mount and work fine (I have SAMBA set up and so I know they mount correctly) but fstab has neither hide nor hair of them. Mtab has some info, but from what I can glean it is just information and not actual configurable data.

I would really appreciate some help. I am VERY interested in learning more about *Unix systems and I don't get discouraged easily, but this has been , no joke, 20+ manhours of banging my head against a wall. Thanks for your time, and let me know if you need any info from me.

---

### Post by prince_niceguy on 2007-10-03
can you let the following information before we do something.

the drive you are trying to mount is it local drive or on some other server or computer?

if it is local drive then you can make an entry in fstab and it will be mounted when you start ubuntu.

---

### Post by bodhi.zazen on 2007-10-03
The permissions of a fat partition are set at the time of mounting.

so you need to either remount the device place an entry in fstab.

See this thread : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

In a nut shell,

sudo umount /dev/sdxy

sudo mkdir /media/foo
sudo mount -t vfat /dev/sdxy /media/foo -o uid=1000,gid=100,umask=007

Or in fstab

/dev/sdxy /media/foo vfat uid=1000,gid=100,umask=007 0 2

If you have no entry in fstab, I assume you are using a removable device and it is being auto mounted ...

---

### Post by Masiv on 2007-10-03
That assistance did the trick! I really have no idea why that wasn't listed anywhere else. I promise that I checked and checked and searched and searched and could not find that information anywhere. Thanks bodhi.zazen for your help. I really appreciate it.

Suprisingly, bodhi.zazen, it is an internal drive that does NOT automount when I start ubuntu. I have four drives and they are all internal. Each one of them is listed as /media/* when checking their volume labels. I've been told this means they are removable media, but they are internal! I am looking at them right now (open case)!

The rather frustrating part of this endeavor is that I tried pretty much every suggestion on every Ubuntu forum I could find. I trolled Debian forums for solutions, and that didn't help. Do you folks have a concrete documentation staff? I would very much like to be a part of it. Let me know how I can help out, as I am a fan of Ubuntu and Debian in general, but I find that there really is no one-stop-shop when it comes to ubuntu docs. [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) is ok, but its too convoluted and I couldn't find what I wanted there. Please let me know how I can help. Thanks!

---

### Post by bodhi.zazen on 2007-10-03
:lolflag: 

Welcome to Ubutnu. Next time, feel free to ask sooner. The information is "there" , it is written in geek is all :twisted:

You can always look at man mount :

[man mount](http://linux.die.net/man/8/mountl)

It will cure your insomnia, but look under the FAT (vfat) section ...

---

