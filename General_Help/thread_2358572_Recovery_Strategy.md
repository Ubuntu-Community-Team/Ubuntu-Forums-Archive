---
title: "Recovery Strategy?"
date: 2017-04-14
forum: General Help
---

### Post by von Corax on 2017-04-14
How do I go about copying the contents of a partition from one drive to another?

A few years ago, I created a bootable USB drive so I could run Cilk++ and CUDA on a borrowed machine. Since that course ended, I have been running it on one of my own machines, with the intention of eventually migrating it to an internal drive.

A few weeks ago my external HD crashed, and of course I have no backup. I was able to fsck with it until it will now mount (grudgingly) and I can access the contents, but it will no longer boot and I am faced with what is essentially a bare-metal recovery.

After installing the new spindle, my first attempt was to ```
dd -if=/dev/sdc -of=/dev/sda
``` but that stopped halfway through when it hit the damaged sectors and left half the spindle unallocated (specifically the part where **/home** should have been.)

My next move was to manually partition the new spindle to approximately match the old drive, run ```
dd -if=/dev/sdc1 -of=/dev/sda1
``` to copy the root partition, use Gparted's **Partition/Check** function to correct a size mismatch, and check that sda1 fscks cleanly.

So that's where I am right now; I still need to repair the MBR, correct the entries in **/etc/fstab**, and copy the other partitions. I'm having a mental block on this last step, though. I want to copy an entire filesystem, but I don't think I want to use **dd** because of the size mismatches between old and new partitions, nor do I want to use **cp** because I want to preserve the file attributes. How should I go about this? I'm running 14.04 LTS, currently from the installation DVD.

Thanks,
Darwin

---

### Post by TheFu on 2017-04-14
There are 50 solutions.
ddrescue - bit-for-bit, handles bad sectors better than plain dd.
fsarchiver - bit-for-bit, but can restore to smaller partitions.
partimage - bit-for-bit
clonezilla - bit-for-bit
rsync (if run as root, ownership and permissions can be retained).
cp (permissions/ownership are retained if root runs the command with the -p option)
tar (I feel dirty suggesting this)
....

BTW, I think your dd commands shouldn't have - and are missing a bs= option. Must be really slow.
```
sudo dd if=/dev/sdc1 of=/dev/sda1 bs=4m
```

Wouldn't having a backup that you could restore be much easier? Please test the restore process to be certain it actually works. It is common for restores to fail the first few attempts because the backup didn't include everything they needed.

BTW, support for 12.04 ends in about 2 weeks.

---

### Post by von Corax on 2017-04-14
> **TheFu said:**
> There are 50 solutions.
ddrescue - bit-for-bit, handles bad sectors better than plain dd.
fsarchiver - bit-for-bit, but can restore to smaller partitions.
partimage - bit-for-bit
clonezilla - bit-for-bit
rsync (if run as root, ownership and permissions can be retained).
cp (permissions/ownership are retained if root runs the command with the -p option)
tar (I feel dirty suggesting this)
....

As I said, I'm running from DVD right now, so I'm limited in my ability to install additional stuff. I need to do this using what I already have, and I want to preserve the ctime and mtime of the files as well as the permissions and ownership.


> **TheFu said:**
>  BTW, I think your dd commands shouldn't have - and are missing a bs= option. Must be really slow.
```
sudo dd if=/dev/sdc1 of=/dev/sda1 bs=4m
```

It seems to have worked without the **bs**. ;)

> **TheFu said:**
> Wouldn't having a backup that you could restore be much easier? Please test the restore process to be certain it actually works. It is common for restores to fail the first few attempts because the backup didn't include everything they needed.

It would have been much easier with a backup; unfortunately, as I said, I don't have one.

> **TheFu said:**
> BTW, support for 12.04 ends in about 2 weeks.
I'm actually running 14.04; I just forgot to update my profile.

---

### Post by dragonfly41 on 2017-04-15
> [COLOR=#000000]I'm running 14.04 LTS, currently from the installation DVD.[/COLOR]> [COLOR=#000000]I still need to repair the MBR[/COLOR][COLOR=#000000]

I believe that** [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")** is in 14.04 repo so I suggest applying testdisk to your disk to try to repair MBR for a start.
If testdisk is not in repo it is a small download.  But if your DVD is not setup as **persistent** you will lose it and any recovered data when you reboot.
And if you attempt file recovery you will need some other drive into which you save recovered files.
I would try first creating a persistent live 14.04 USB/DVD if you wish to try this idea.   
And perhaps invest in another external drive which you can use to save testdisk recovered files and later use the drive for backup.[/COLOR]

---

### Post by TheFu on 2017-04-15
You can install programs on a live-boot system.  Just use whatever package manager front-end you like. If you stay away from GUI programs, it won't be an issue.

The bs= parameter will vastly increase the performance, nothing more.  Sometimes adding a little bs is good. ;)  Regardless, I'd use ddrescue to mirror the entire source to a new target disk, but the target must be larger.  If that isn't possible, use fsarchiver.

You are correct to make a mirror copy first. Never touch/modify the source disk until you have the best mirror possible.. Actually, I'd work on the mirrored version on a new disk when trying to recover stuff. Never touch the old disk. It won't make anything better and can make it much, much, worse.

There is a data recovery how-to in the help.Ubuntu.com area. google finds it easily. It is very thorough.  testdisk is a last resort option really. It produces files with garbage names, though you can ask for only certain types of files. It really isn't useful to recover more than a few hundred data files. Think wedding photos, not last-trip-snapshots.

---

### Post by dragonfly41 on 2017-04-15
> [COLOR=#000000] It produces files with garbage names, though you can ask for only certain types of files.[/COLOR][COLOR=#000000]
I think that this refers to **photorec** not testdisk. photorec is part of testdisk family.
I have to say that testdisk has pulled me out of a hole on a number of occasions and recovered (saved) files with full filenames.

[/COLOR]> [COLOR=#000000]Never touch/modify the source disk until you have the best mirror possible.[/COLOR][COLOR=#000000]
Agree with that but OP doesn't seem to have a backup disk.[/COLOR]

---

### Post by TheFu on 2017-04-15
I could be mistaken between photorec and testdisk.  Ran one of them a few weeks ago - a convenience thing for some temporary files on a flash disk that became corrupted during later processing on a HDD.

Not having a backup doesn't necessarily mean not having a spare disk to mirror onto. I thought that is what the OP was trying to accomplish - a bit-for-bit mirror.

but I could be wrong. I often am.

---

### Post by von Corax on 2017-04-18
I tried fsarchiver, but it complained about being unable to mount the subject partition under **/tmp/** so I gave up on that option.

Here's what I finally did:

[LIST]
[*]partition the new spindle (/dev/hda) to approximately match the dying spindle (/dev/hdc). While I was at it, I doubled the size of /dev/hda1 (root) at the expense of /dev/hda10 (/home). 
[*]install Ubuntu on /dev/hda1. This gave me a working MBR. 
[*][FONT=courier new][FONT=system]**dd if=/dev/sdc1 of=/dev/sda1**[/FONT][/FONT] to restore the root partition. 
[*]use tar to archive the other partitions on sdc, and restore them to the corresponding partitions on sda, using /dev/sda10 as the midpoint. 
[/LIST]

The system now boots from /dev/sda, and everything *seems* to be where I left it. There are a few points of crashiness, but I shall address those as I come to them.

Next on my list: get my BSD box working as a Bacula server. (I swear that was already next  on my list before all this happened. ;))

---

### Post by deadflowr on 2017-04-18
> **dragonfly41 said:**
> [COLOR=#000000]

I believe that** [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")** is in 14.04 repo so I suggest applying testdisk to your disk to try to repair MBR for a start.
If testdisk is not in repo it is a small download.  But if your DVD is not setup as **persistent** you will lose it and any recovered data when you reboot.
And if you attempt file recovery you will need some other drive into which you save recovered files.
I would try first creating a persistent live 14.04 USB/DVD if you wish to try this idea.   
And perhaps invest in another external drive which you can use to save testdisk recovered files and later use the drive for backup.[/COLOR]

You need to enable universe (community) in the sources list (inside software sources) or ((inside Software and Updates)) when installing testdisk from a live session.

---

