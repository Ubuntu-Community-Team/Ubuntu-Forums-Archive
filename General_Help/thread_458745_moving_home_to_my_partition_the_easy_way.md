---
title: "moving home to my partition the easy way?"
date: 2007-05-29
forum: General Help
---

### Post by bone2006 on 2007-05-29
I wanted to move my home partition to another partition and saw a bunch of ways of doing it and I saw somebody say it was easier to do it via the liveCD.  So I booted up the livecd, in the command changed to root user and browsed to the main partition that had the home directory, then I cut and pasted the folder into the second partition.

I went and edited etc/fstab and put this line here at the end:
/dev/sda3 /home ext3 nodev,nosuid 0 2

When I rebooted I had errors, which I'm on a television screen that I can't read too well until I'm logged in, but I wasn't able to login and I had to go back to the liveCD, move the home back and remove the line in fstab.

What did I do wrong?

---

### Post by merlinus on 2007-05-30
I believe you need to create a mount point for your new /home partition, e.g. /media/sda3.  Simply adding a line to /etc/fstab will not do it, as you found out.

A good source of info is at:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck!

-merlin

---

### Post by bone2006 on 2007-05-30
I'm not sure that makes since to me and looked at the link, it gives instructions on mounting the partition, which is already done.
The partition was already created, mounted and working.  Just wanted to move the home there, which seems like most of the steps aren't required as in creating a partition and mounting the partition.  

Therefore seems like I should be able to just move the directory to the new partition, then let ubuntu know that home is now in this new place?

---

### Post by merlinus on 2007-05-30
Don't know if this will help, but here are the applicable lines from my /etc/fstab:
> 
# Entry for /dev/hda7 :
UUID=a961b624-ed15-4878-b66f-bb2d007b74a4 /home ext3 defaults,errors=remount-ro 0 1


You can get the UUID for the partition you are wanting to mount as /home by entering
```

blkid

```
in a terminal.

hth....

-merlin

---

### Post by bone2006 on 2007-05-30
maybe I am confused.  I only put the last line /dev/sda3 /home ext3 nodev,nosuid 0 2 in the fstab.

Before this line I already had sda3 mounted and was using it, so I just wrote that line above to mount the home directory.  

When I look at the line below it seems you have to mount home separately from my other mounts?
UUID=a961b624-ed15-4878-b66f-bb2d007b74a4 /home ext3 defaults,errors=remount-ro 0 1

What I mean is that at the end I want two partitions, so the second partition I already have folders/files there.  I was moving everything into this directory.  So I'm guessing that the instructions I got before won't work out.  I'll try to add the UUID at the end of the fstab as you have indicated.

---

### Post by bone2006 on 2007-05-31
somethings just aren't making sense.  I've tried a lot of things without success.   The instructions on the website just don't seem to work for me, for maybe two reasons.  One is I already have a partition and two it seems the new ubuntu will automount the devices when you use nautilus, therefore I've been skipping the steps, because it seems silly to mount something that's already been mounted. I tried calling the commands and I just copied and paste them and it doesn't work even when I edit out with my new system.  

I basically have a partition that's named BACK and I'd like home to be there.  It's an ext3 partition and I've tried copying and pasting, which honestly seems to work. I think copying it works, because I've screwed up after a cut and paste and when I paste it back it's default place and get fstab back up, it seems to work. Which seems to indicate that copying my home works just fine while in liveCD.

here is a copy of my fstab, which I'm just confused.  I know my UUID it's below, it's being mounted for BACK.  I just want to use my partition as Home.  Not sure if that means nothing else can be there?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=d39c3868-f893-41bb-9961-6c081e038930 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=544C0EB54C0E91C2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
LABEL=Backup /media/Backup     ext3    defaults        0       2
# /dev/sda5
UUID=3C68A27068A2291A /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=a3961771-b2c0-4c24-9c6e-f2a366a54909 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bone2006 on 2007-06-01
finally got it working.  The problem was the link and all the instructions change the privledge when moving home to root, so it was one problem I was having.  The link that was posted took it's directions from this blog anyway, which I followed and got it to work while not in a livecd mode.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

the only difference was that this $cd /home/
$find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/ has actually two - - characters, but the way you copy and paste it while in firefox it comes with an error.  Once I changed this and did everything else I was able to move it perfectly.

---

### Post by loathsome on 2007-06-01
This is a good link ;)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by loathsome on 2007-06-01
Oh snaps :lolflag:

I need to read through the whole thread the next time I'm posting. Heh, sorry.

---

### Post by bone2006 on 2007-06-01
On two systems I tried the comand and it didn't work I replaced it with

find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome

instead of this one:

find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome

Wish the instructions would be updated.  I found the new instructions, which has two -- and a sudo infront of the second part.  I tried putting sudo in the beggining of everything and no go

---

