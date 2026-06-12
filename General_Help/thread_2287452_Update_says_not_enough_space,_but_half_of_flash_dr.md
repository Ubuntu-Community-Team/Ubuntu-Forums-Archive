---
title: "Update says not enough space, but half of flash drive's capacity is unused."
date: 2015-07-19
forum: General Help
---

### Post by steve169 on 2015-07-19
1. Ran Software Updater. Updated software available: 69.8 MiB.

2. Started download and received this error message:
[INDENT]**Not enough disk space**
The upgrade needs a total of 513 M free space on disk '/'. Please free at least an additional 135 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/INDENT]

3. Trash was already empty. I ran the clean command.

4. Rebooted Lubuntu and ran Software Updater. Received error message identical to above. No change in free space.

5. File Manager shows 360.8 MiB free space but shows "total" as only 3.3 GiB. The flash drive, however, has an 8 GiB capacity (Kingston DTSE9 G2 USB 3.0).

6. How can I make Lubuntu and Software Update use the entire flash drive capacity?

---

### Post by Bashing-om on 2015-07-19
steve169; Hello;

The advisory :
> 
Not enough disk space

Is some what misleading. Often times the space consumption is in respect to the space available on a partition.
Most times the /boot partition.
let's check the space usages:
```

df -h
df -i

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2015-07-19
Flash drive? Are you running a live usb with persistence? BTW if it is formatted to FAT (as live usb's are) it can't access more than 4 Gs.

---

### Post by steve169 on 2015-07-20
Here's the result of df -h:[INDENT]**Filesystem         Size  Used Avail Use% Mounted on**
udev                   1.9G     0  1.9G   0% /dev
tmpfs                  383M  6.0M  377M   2% /run
/dev/sdc1              3.4G  2.8G  373M  89% /
tmpfs                  1.9G  4.0K  1.9G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs                  383M  4.0K  383M   1% /run/user/116
tmpfs                  383M  8.0K  383M   1% /run/user/1000
/home/stevie/.Private  3.4G  2.8G  373M  89% /home/stevie
[/INDENT]

Here's the result of d -i:[INDENT]Filesystem             Size  Used Avail Use% Mounted on
udev                   1.9G     0  1.9G   0% /dev
tmpfs                  383M  6.0M  377M   2% /run
/dev/sdc1              3.4G  2.8G  373M  89% /
tmpfs                  1.9G  4.0K  1.9G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs                  383M  4.0K  383M   1% /run/user/116
tmpfs                  383M  8.0K  383M   1% /run/user/1000
/home/stevie/.Private  3.4G  2.8G  373M  89% /home/stevie
[/INDENT]

Attached is a screenshot from Gparted.

---

### Post by steve169 on 2015-07-20
Yes, it is a live USB with persistence. It is formatted ext4. A screenshot from Gparted is attached.

---

### Post by Bashing-om on 2015-07-20
steve169; Sheesshhh;

Not much room to work in, huh ?

Let's look closer at what we can do:
```

cd /
sudo du -sx * | sort -n
cd /home/stevie/.Private
sudo du -sx * | sort -n
cd

```
The 'du' command will take a while to complete - a lot to do - ; patience.

And a closer look at /boot's kernels:
```

dpkg -l | grep linux-

``` and we see what we can do to add to that " 373M  " of available space.

[INDENT][INDENT]6 pounds of sugar
[INDENT][INDENT][INDENT][INDENT]a 5 pound sack
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2015-07-20
It is a USB drive with an installed system. And the swap partition is way too big. I suggest that you boot from another drive, for example the Lubuntu install drive, and use gparted to ***shrink the swap partition to 400 MB.*** After that you can grow (expand) the root partition. See the following link

[http://phillw.net/isos/linux-tools/9w/GrowIt.pdf](http://phillw.net/isos/linux-tools/9w/GrowIt.pdf)

You will not do exactly the same thing as in the link, but similar enough, that the link should help you. Good luck :-)

Edit: First shrink the swap partition, then shrink the extended partition (the container around the swap partition), And finally you can grow the root partition into the unallocated space between the small swap partition and the root partition.

---

### Post by Bashing-om on 2015-07-20
steve169; Hey

^^ Now that is the voice of experience ! :)

[INDENT][INDENT]there is no substitute
[/INDENT][/INDENT]

---

### Post by steve169 on 2015-08-01
It's done. Many thanks for all the help.

I struggled some more, then wound up using RMPrepUSB to create a bootable flashdrive. It allows you to use all the drive space, so I created two partitions to the proper sizes and formats, then installed Lubuntu Mini 15.04 from a disk. It worked.

---

### Post by Bashing-om on 2015-08-01
steve169; Outstanding !

You do good work.

As this situation is now under control;

Please mark this thread 'solved'
( 1st post -> thread tools )

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

