---
title: "dd help with clone"
date: 2006-11-22
forum: General Help
---

### Post by artinla on 2006-11-22
Is there a faster way to use dd to clone a drive?

I use:

sudo dd if=/dev/hda of=/dev/hdb

to clone hda to hdb.  It seems to take way too long, and I assume that is because it is actually cloning all the free space.

I seem to remember a way use NUL to somehow get dd to ignore free space.  Am I just going crazy or does someone know what I am talking about?

Thanks for any suggestions other than RTFM.

---

### Post by CatKiller on 2006-11-22
I think you're right that **dd** copies the free space too - as I understand it, it's a bit-for-bit copy, a true clone. You could use **tar** instead if you only want to copy the files. I've used ```
( cd /mnt/source && tar clf - . ) | ( cd /mnt/dest && tar xvpf - )
``` from a live cd to do migrations and the like. Perhaps you could adapt that to your needs?

---

### Post by artinla on 2006-11-22
Hmmm, I will think about that.  The only thing about tar is that it won't create a bootable copy.  This is something that should really be easier and faster to do in Linux.  The present "Ghostlike" programs for cloning in linux leave plenty to be desired.  

I hope someone, somewhere finds the time to write a decent cloning app for Linux.

Thanks for the reply

---

### Post by CatKiller on 2006-11-22
I'm fairly sure that it's [partimage]("http://www.partimage.org/Main_Page") that **aysiu** recommends, but I've never used it.

EDIT: not only that, but he's gone so far as to write [a tutorial]("http://www.psychocats.net/ubuntu/partimage") about how to use it.

---

### Post by pixelpusher on 2006-11-23
I was about to ask the same question ... if it helps added a larger block size helps...

if=/dev/sda of=/dev/sdb bs=128M

that cloned a 250GB Sata2 drive in 2.5 hours (without setting the larger blocksize it looked like it was going to be an allnighter)

but the issue still remains .. I was cloning an newly created XP disc .. so only a GB or so was actually data.. the rest empty space .. I tried using partimage but could not seem to create a bootable drive with it without a spare disk to save the image to and then restore from ... perhaps I am missing something ?

Also, I did wonder (but did not have the time on this occasion to try it) lets say I can see that dd has copied 2GB (`kill -USR1 $PID; sleep 1` shows you whats done so far) , if I killed dd at that point .. is it possible that I would then have a bootable image that perhaps just needed a simple chkdsk or fsck to `fix` ? that would assume that dd starts from the begging of the drive and copies bit by bit from there ... whatcha think ?

---

### Post by squidward_tentacels on 2006-11-23
The way I do is is to use gparted. After I get my install configed to my tastes, I shrink the partiton to smallest possible size, copy it over to hdb,(or at the end of the drive somewhere, as sort of a "recovery" partition, for when I break it again, lol) and then "grow" the partiton back to previous size. I fit the entire install plus additional packages and updates into somewhere around 2 gigs. This copy is fully bootable. If you are unfamilar with the live gparted iso, I have also written up a "how-to" here;
[http://ubuntuforums.org/showthread.php?t=302717&highlight=copy+clone+disk+image](http://ubuntuforums.org/showthread.php?t=302717&highlight=copy+clone+disk+image)

That doesnt cover shrinking the partiton you want to copy to eliminate free space, But its pretty straight forward. Then you get a bootable copy, with no empty blocks being copied. And your right, the "ghosting" apps currently available......just ewww.[-( 

I dont know if thats what your looking for, but it does the trick for me;)

---

### Post by petteriIII on 2006-12-09
Command is: dd if=/dev/<from> of=/dev/<to> bs=1MB count=<go to gparted and select 'to' partition. Select: Resize/Move. In the window that opens shrink the partition until gparted refuses to shrink more and look the MB:s. This is the needed count. Add 20 to be sure>.

---

