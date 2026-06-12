---
title: "Hard Drive dying, freeware data recovery software?"
date: 2013-03-05
forum: General Help
---

### Post by Cool Javelin on 2013-03-05
Hi all:

I have a 250G internal Ubuntu 10.10. ext3 maybe ext4 drive that seems to have failed. It is not the boot drive. The computer is up and running.

I was having troubles accessing files, then when I rebooted, I get a lot of messages about bad super blocks, and unmountable.

Also, the drive makes some clunking noises during boot (it sounds like the head seek is reaching a hardware end of travel.)

I can not mount the drive.

Is there a freeware software that can get the data off the drive and put it somewhere else? Maybe a way to bypass mounting the drive and do infinite retrys.

I have a USB to IDE adapter and can remove the drive and attach externally if that helps.

Also, I can do that and plug into a WinXP computer if there is Windows freeware software that may work better.

Thanks, Mark.

---

### Post by kclark on 2013-03-05
You could try and use dd to make an image of the whole drive.  I've done something like this in the past to copy the image to my server
> 
dd if=/dev/sda of=/dev/stdout bs=1M | bzip2 | ssh USERNAME@remotehost "cat - > drive.img.bz2"

That command is just off the top of my head, you might want to read the man pages before doing this

Then to recover the data to the new drive do something like this
> 
ssh USERNAME@remotehost "cat drive.img.bz2" | bzip2 -dc | dd if=/dev/stdin of=/dev/sda bs=1M

Or you could try [dd_rescue]("http://manpages.ubuntu.com/manpages/lucid/man1/dd_rescue.1.html")

---

### Post by oldfred on 2013-03-05
Have you tried fsck?

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

