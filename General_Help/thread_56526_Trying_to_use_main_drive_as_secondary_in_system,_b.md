---
title: "Trying to use main drive as secondary in system, but still main drive."
date: 2005-08-12
forum: General Help
---

### Post by Statik on 2005-08-12
I know the topic is a bit confusing looking, so here's the scoop.

My new ubuntu computer had a bad motherboard, so I had to send it out for repair. In the meantime I have a loaner board that I have installed. Now, my original install was on a 200gig SATA drive. The new board, while the same chipset and SATA enabled, only sets up the SATA drives as part of a RAID array. So, I grabbed an old 3GIg ATA drive and installed Ubuntu there. I can mount the SATA drive (/dev/sda1), but what I'd like to do is somehow mount the /home/<username> from /dev/sda1 as the /home/<username> on /dev/hda1 . Effectively I would be using the original home directory so that when I get the replacement motherboard I should be able to just plug the SATA drive back in and go from there. No hiccups or file transfers.

So, is this possible? If so, how do I go about it?

I tried reading the man for mount, and I think there was something there about it, but I didn't quite understand how to do it. Mount seems more concerned with mounting windows partitions, etc. I also got to the end of the man pages, and it said (END), but I didn't seem to be able to END the man . . . other than Ctrl-Z which leaves it running. How am I supposed to end MAN?

Statik

---

### Post by PeP on 2005-08-12
to end in man hit Q

you may mount a different partition as /home/oneuser, but it needs to have the oneuser directory at the root of the partition (ie the partition's root dir looks like
.bashrc
.gnome
Desktop
)

if it is your old root partition there is an easy trick:
mount the partition as /mnt/sda1
```

sudo mkdir /mnt/sda1
sudo mount -t ext3 /dev/sda1 /mnt/sda1

```
move or link your user dir to in the root of that partition

eg if your partition looks like (ls /mnt/sda1)
bin/
etc/
initrd/
...

just do in the same location :
```
sudo ln -s /mnt/sda1/home/oneuser /mnt/sda1/  
```(this will just add a shortcut, do not remove the original)
or 
```
mv  /mnt/sda1/home/oneuser /mnt/sda1/ 
```(this will move the directory)

to mount an ext3 partition (replace ext3 by reiserfs or any kind of filsystem) named /dec/sda1 (replace sd1 by what suits to you) in /home :
```
sudo mount -t ext3 /dev/sda1 /home
```

to have it mounted automatically at boot
```
sudo gedit /etc/fstab
```
and add a line like this
```
/dev/sda1       /home           ext3    defaults        0       2
```

---

### Post by Statik on 2005-08-12
I presently have the drive (/dev/sda1) being mounted in fstab as /mount/SATA_Drive . THis allows me to access it. Since I only have a 3 gig drive, I'd like to find a way to run the entire install from the SATA drive. Searching for the Kernel Panic thing hasn't helped much. I've also tried mounting /dev/sda1 as / instead of /dev/hda1 but that gives me the same results as booting without the ATA installed at all. The kernel panic mentions /bin/bash not being found or something.

The instructions you've given haven't fixed the problem, but they have given me more insight into how this works. Much Appreciated!

Any more ideas?

Statik

---

