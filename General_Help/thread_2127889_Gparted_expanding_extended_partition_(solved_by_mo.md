---
title: "Gparted expanding extended partition (solved by moving home partition)"
date: 2013-03-21
forum: General Help
---

### Post by SergeantMajorME on 2013-03-21
Hello, I have a feeling this has been answered, but after a google search, all things I found said I should not be getting an error.

Here's my situation:
My laptop has 2 hard drives, OS and Data.  OS had windows.  I needed linux for a school thing, so I installed ubuntu on the Data drive. Because it wasn't meant to be a main OS, I only gave it like 20 gb total.  Well, for some reason, windows decided to not like this (it ends up freezing 5 minutes after boot, but that's another issue... if you have suggestions though, I'll take them), and so I'm using linux until the semester is out.  However... 20gb is way to little for all the programs I need to install now.  Here is my current setup:

[http://img716.imageshack.us/img716/9026/gpartedl.png](http://img716.imageshack.us/img716/9026/gpartedl.png)

I want to add the ~20gb of unallocated space to the extended drive.  When I try doing it though:

[http://img580.imageshack.us/img580/7430/errorcq.png](http://img580.imageshack.us/img580/7430/errorcq.png)

Everywhere I read said that as long as the swap partition wasn't locked, I was fine.  I even thought I may have needed a swap partition, that's why I did the 500 MiB tempSwap partition.  Didn't work.  

I really need to expand my linux partition, any idea's?

Thanks,

SgtMjrME

sfdisk (I've seen other threads require this type of thing)
```

   Device Boot    Start                                End                                  #cyls                             #blocks                                                  Id  System
/dev/sda1   *        0+                                84775-                             84776-                          680960000                                                 7  HPFS/NTFS/exFAT
/dev/sda2           84775+                         86050-                              1275-                            10240000                                                  7  HPFS/NTFS/exFAT
/dev/sda3           88651+                          91201-                             2550-                             20478976                                                 5  Extended
/dev/sda4           86050+                          86114-                              64-                               512000                                                     82  Linux swap / Solaris
/dev/sda5           88651+                          88906-                             255-                               2048000                                                   82  Linux swap / Solaris
/dev/sda6           88906+                          89926-                             1020-                             8192000                                                   83  Linux
/dev/sda7           89926+                          91201-                              1275-                            10235904                                                 83  Linux

```

---

### Post by TheFu on 2013-03-21
1) sfdisk is not safe on all new 4K HDDs, it is best to always use gparted or parted going forward.
2) I think to extend your sda3 partition, you might need to remove all the logical partitions inside first, but I could be wrong.
3) Did you boot off some other media like a flash drive or liveCD?  If sda is currently in-use, then you cannot modify the partitions.

You can delete both swap partitions - why do you have more than 1 anyway? Each can be shared between multiple linux installs, provided you don't hibernate 1, then attempt to boot another.

20G should be more than enough for every program available under Linux - it is the data that is eating all your space.  To solve that, move your /home to a different partition and be happy.  Heck, I've been running the same partition with 14G for the last 5 yrs, it is just my $HOME that needed more storage.  Keeping the OS/apps separate from /home and big data is a best practice. This applies to Linux, OSX AND to Windows.

Hint: for posting items where column lineup is helpful, check out the "code" tag in the advanced editing tools.

---

### Post by SergeantMajorME on 2013-03-21
1) I was only planning on using gparted, but a lot of topics I saw they asked for a list like that.

2) I don't want to remove my root/home drive... that's what I'm hoping to not do.  

3) Yeah, running a bootable USB atm (which is why the extended partition isn't locked)

I created the second swap partition because I thought it might be necessary, but it didn't help.  

and again, when I initially did this I didn't expect to put much on.  However, now that I need to run it as my main drive, I DO need that extra space (as you can see, my root is almost full, and there's more stuff that I could put on there but havn't yet).  The home drive is almost full because a certain program I'm working with in school, for every run, produces about 5 gb of data (I have no idea why).  

Is there a way to push my home partition to the unallocated space, and then expand my root to fill the home's space? And if so, can you give a detailed list of operations to do in gparted/etc to re-setup the ubuntu install?

---

### Post by TheFu on 2013-03-21
> **SergeantMajorME said:**
> Is there a way to push my home partition to the unallocated space, and then expand my root to fill the home's space? And if so, can you give a detailed list of operations to do in gparted/etc to re-setup the ubuntu install?

**parted -l **will dump partition information, FYI. It is safe for use on 4K and GPT formatted disks too, unlike fdisk and related tools.

Sure you can.
* Create a new partition in the unallocated space.
* make that partition ext4 (probably a good, average choice for file system) that is large enough to hold your $HOME
* boot into the normal Linux with your /home shared with the / partition.
* create a temporary mount for the new partition - /mnt/home would be my choice. (**mkdir -p /mnt/home**)
* Find the UUID for the new partition using **blkid**
* manually add the mount into the /etc/fstab, but keep everthing point to /mnt/home
* mount the new partition (**sudo mount -a**)
* verify the mount worked - **df -h** - do you see the new partition?
* drop into single user mode (**telinit 1**) - I think that's the command. This should drop you to a non-GUI environment, as root.
* Now **mv /home/* /mnt/home/**
* edit the /etc/fstab and change just the part that says /mnt/home into /home
* there are lots of ways to do the next step, but **rebooting** is probably the easiest.  You could telinit again to a different runlevel, perhaps 3, but you'd need to remember to umount /mnt/home then mount -a again first.

Good enough?

That's a bunch of steps for something conceptually easy.  I'd be remiss if I didn't say to run your backups before starting this process. I don't think I've forgotten anything, but I can't be certain. Heck, there might be an easier way using gparted that I don't know too.

Be careful about selecting the new partition for the new file system and to be mounted - if you get that wrong, you will be trashing something, right?  Those files will be 100% gone, so don't get those steps wrong.

In the end, as long as all the files from /home on the original partition appear to be under /home on any other partition, then everything will be just fine.  You can do all this from a different boot environment, but then you'd need to mount / first somewhere and I think the risks for a screw-up increases drastically.

There are hundreds of other ways to accomplish the same thing.  You could just backup and restore too after adding the new partition and moving the old one to a temporary out-of-the-way place.  If you don't "move" all the files under /home - then you'll leave that space on the HDD, but when you mount the new partition to /home, those files will be there, but inaccessible.  Does that make sense?

---

### Post by SergeantMajorME on 2013-03-21
Well, turned out to be much simpler than I thought.

Using gparted on liveCD, just did a "copy" of the home drive (EDIT: partition (man, way more used to windows)) to the unallocated space.
Booted into ubuntu, it automatically mounted the new, larger partition.  The old partition (in the extended part) was not mounted.
So I went back into the liveCD, deleted the old home partition, expanded the root, and when I re-booted ubuntu, it still uses the new home partition.  

Solved, thanks though :)

---

### Post by TheFu on 2013-03-22
Compare doing this do trying to move your c:/user directory under that other OS. Much easier, I think.

---

