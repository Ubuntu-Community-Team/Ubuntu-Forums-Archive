---
title: "implications of grub and separate boot partition on upgrading"
date: 2006-12-19
forum: General Help
---

### Post by backdoc on 2006-12-19
I upgraded from Breezy to Edgy by installing Edgy on disk 2, getting it working and then copying Edgy from disk 2 to disk 1 (keeping Edgy on disk 2).  Then, because my bios is so old, I couldn't boot Edgy on disk 1.  So, I squeezed in a new partition in the front to hold the kernel.  I configured /etc/fstab to mount it to /boot.  It's up and running, but I'm concerned about what will happen when a new kernel is released.  I guess the kernel will install OK, but will it configure Grub properly?  Also, I had to change the /etc/fstab file and do away with the UUID numbers, too.  I'm wondering if this will screw things up if I do a dist-upgrade later to Fiesty-Fawn.  I've never seen these UUID numbers before.  I would have left them in if I knew how to recreate them from a rescue disk.  Any ideas or suggestions?  Note the comments in the snippets below.

snippet of Grub entry:

title           Edgy on first hard disk, kernel 2.6.17-10-server
root            (hd0,2) #note this is the 3rd partition and gets mounted as /boot
# note: I removed "/boot" from the kernel and initrd lines below
kernel          /vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash 
initrd          /initrd.img-2.6.17-10-server
quiet
savedefault
boot

/etc/fstab:

/dev/hda1  /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3  /boot        ext3    defaults        0       2
/dev/hdb1  /media/edgy     ext3    defaults         3       2
/dev/hda2  none            swap    sw              0       0

In case you are wondering, here's how it ended up this way.  I've been running an Breezy on an old server for some time (on hda1).  And, I needed to upgrade.  I chose to do a new install.  Long story short, I left Breezy on /dev/hda and installed Edgy to /dev/hdb.  After getting getting what I needed off of the old install, I cleaned off the first hard drive and used Acronis Disk Director to just copy Edgy from my second drive to my first drive.  This went OK, except for the fact that my bios was too old couldn't boot a partition that large.  To satisfy the requirements of my old bios, I moved the /hda1 partition over and squeezed in a partition in front of it for my kernel.  Believe it or not, this all worked and I can boot to Edgy on disk 1.  It screwed up the partition numbering, which doesn't hurt anything, it just looks odd.  The first partition on my drive is /dev/hda3 (which holds my boot partition).

---

### Post by bodhi.zazen on 2006-12-19
> **backdoc said:**
> I upgraded from Breezy to Edgy by installing Edgy on disk 2, getting it working and then copying Edgy from disk 2 to disk 1  .... 

Cool.

I do not foresee any problems. Just watch the space on that boot partition 8)

To list  your partitions by uuid:

```
ls /dev/disk/by-uuid -lh
```

---

### Post by backdoc on 2006-12-19
> **bodhi.zazen said:**
> Cool.

I do not foresee any problems. Just watch the space on that boot partition 8)


I made it around 100 megs or so.  I can always resize it if I need to without having to change anything in fstab or grub.

> 

To list  your partitions by uuid:

```
ls /dev/disk/by-uuid -lh
```

I saw this.  But, I had two installations (and still do) with the same UUID.  So, do the UUID's change when you move partitions?  Or, do you have to generate new ones?  I know I would have had a problem if I had left two entries in fstab with the same UUID.

_*Edited moments later:*_  OK.  I just tried ls -l /dev/disk/by-uuid.  I got a different UUID for every partition.  Now, I could go back and edit my fstab.  But, there would have been no way to do that without rebooting and since my fstab was messed up, I had to do something.  I don't know.  UUID's seem like an unneccessary layer of complexity.  I guess I'll just have to go back and read up on them some more.

---

### Post by bodhi.zazen on 2006-12-19
You do not NEED to change back to uuid.

If you WANT to I would advise doing it from the Live CD.

---

### Post by backdoc on 2006-12-19
> **bodhi.zazen said:**
> You do not NEED to change back to uuid.

If you WANT to I would advise doing it from the Live CD.

I won't worry about the UUID's.  I don't understand them though.  And, that's bugs me.  

What I'm more concerned about is that in order for GRUB to find my kernel, I had to remove "/boot/" from the path to the kernel and initrd (check out the Grub snippet above).  Essentially, it gives me a path that looks like (hd0,2)/vmlinuz-2.6.17-10-server.  I'm afraid the upgrade will not respect that.

Of course, if it doesn't, I can use my rescue CD and fix it.  But, it's just one more thing looming on the back of my mind that I know I'll have to watch out for.

---

### Post by bodhi.zazen on 2006-12-19
LOL :lol:

Check it out: [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

I do not think the upgrade process is any different just because you have a /boot partition as long as the partition is indeed mounted at /boot :)

---

### Post by backdoc on 2006-12-19
Thanks for the link.  That was pretty informative.  I still don't get how Ubuntu creates them and how they are useful in the fstab.

Last night, I read that it made things more reliable because if Ubuntu ever decided to change the way they named disks, your fstab wouldn't be affected.  If that is true, is the UUID a hash of /dev/hda1, for example?  It can't be based on the data in the partition because that is a moving target.  In that case, I guess UUID's are created early in the boot process based upon the physical location on disk and then fstab uses this to mount.  I'm guessing.

If this is true, then how would you know how to configure fstab before the system was up and running?  And, I guess if you were replacing an existing OS, you could just reuse the old UUID, since it doesn't appear to be generated based on data.  

Finally, I'm wondering if there is any random seed?  The more I think about it, the more confused I get.  If the only thing that a UUID was based on was its location on disk, then there would be a ton of people all using the same UUID.  That would defeat the purpose.  If it has a random component, then how could I ever predict one, like in my case where I needed to know it before I ever booted Ubuntu????

---

### Post by bodhi.zazen on 2006-12-19
It all works automagically of course !

---

