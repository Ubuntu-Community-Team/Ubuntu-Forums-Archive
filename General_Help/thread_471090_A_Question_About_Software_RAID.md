---
title: "A Question About Software RAID"
date: 2007-06-11
forum: General Help
---

### Post by SupaRice on 2007-06-11
OK, so I have had my system running for a long time and it's been rock solid.... until I upgraded.  It grenaded.  So now I need to know if I re-install can I get the install disk to recognize my existing RAID and mount it without destroying the data?

My system is kind of a strange setup:
I have 4 physical drives, acting as two seperate software RAID arrays one is RAID0 and one is RAID1.

Drive 1 and drive 4 are both IDE, and have multiple partitions.  Drive 1 has a partition for / and a partiton for my RAID1 array.  Drive 4 has a partition for my RAID1, a partition for /boot (I think), and one as a swap partition.

Drives 2 & 3 are SATA both with only one partition each, which comprises my RAID0 array.  This is my "/share" and is a SAMBA share for general file storage.

Now, I know this is weird.... BUT, I did it for this reason.... the RAID1 array on my IDE drives is where I mounted my /home.  This was so I could have redundant storage for backup purposes.  The RAID0 array is general storage, and isn't super important data however I'd like to get that back as well.

Since I went through all this trouble to get redundancy, I'd like to be able to save my files before reloading the system.  That is unless someone can tell me how to fix it.

I posted my problem here origionally:
[http://ubuntuforums.org/showthread.php?t=465457](http://ubuntuforums.org/showthread.php?t=465457)
However, I've gotten no response as of yet so I'm now basically just interested in remounting those RAID drives on a new install.

So will the install CD recognize my existing RAID arrays and allow me to remount them on the new installation as /home and /share without destroying the data?  Or is there a way of fixing my corrupted upgrade?  I have tried following the directions others have listed on reinstalling GRUB, but it doesn't seem to work for me given my crazy partitioning.  Or, can I at least get the live CD to recognize my arrays, so that I can pull the data off and back it up before reinstalling completely?

I thought this might help to explain my partitioning, I got it from the live CD.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12158    97659103+  fd  Linux raid autodetect
/dev/hda2           12159       14593    19559137+  83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         365     2931831   82  Linux swap / Solaris
/dev/hdc2             366       12523    97659135   fd  Linux raid autodetect
/dev/hdc3           12524       14946    19462747+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

```

---

### Post by kidders on 2007-06-12
Hi there,

> **SupaRice said:**
> Now, I know this is weird.... BUT, I did it for this reason.The first thing worth saying is that there's nothing particularly weird about the way you've organised your hard disks. It may or may not be the most *efficient* possible arrangement, but it certainly shouldn't be causing you any problems.

It seems to me that you have...
[LIST]
[*]**/dev/hda1**: RAID1 component
[*]**/dev/hda2**: Ubuntu root filesystem
[*]**/dev/hdc1**: Swap space
[*]**/dev/hdc2**: RAID 1 component
[*]**/dev/hdc3**: Ubuntu /boot filesystem?
[*]**/dev/sda1**: RAID0 component
[*]**/dev/sdb1**: RAID0 component
[/LIST]

Hopefully that's accurate. If I were you, I would consider that the only things a Linux installer needs to touch are /dev/hda2, /dev/hdc1 and /dev/hdc3. When installing Linux, my goal is always to simplify the installation itself as much as humanly possible, so that (a) the install is more likely to succeed, and (b) if it fails, it can't damage anything that matters. In your case, since your RAID arrays don't form part of the Linux system itself, I would wait until after the installation to set them up ... which is trivial, in any case.

One thing I should mention is that there's no guarantee that your partitions' /dev names will be the same before, during, or after the installation, so be sure to burn the "look" of your partition schemes into your mind before you start, so you will spot device name changes ... rather than accidentally formatting the wrong partitions!

Once your basic Linux system is installed, booted, and you've installed any software necessary to manipulate your RAID arrays (or the filesystems on them), you can ...

[LIST=1]
[*]Mount them manually, to verify that /dev/md0 and /dev/md1 (or whatever they get called) are what you think they are.
[*]Tweak your /etc/fstab to have them mounted where you want them in the future.
[*]Dismount your arrays and do a **sudo mount -a** to have your changes take effect.
[/LIST]

To answer your questions more directly though...

> **SupaRice said:**
> So will the install CD recognize my existing RAID arrays and allow me to remount them on the new installationI've never tried it (for the reasons I explained), so I can't be sure ... but I would be frankly stunned if the answer was no.

> **SupaRice said:**
> Or is there a way of fixing my corrupted upgrade?Depending on what's gone wrong, there may well be. Normally, the only reasons to do a complete reinstallation are...
[LIST]
[*]If some fiddling (or maybe an accident of some sort) that resulted in a broken system could have introduced a security problem that you may not be able to address confidently. Personally, I would rather reinstall than risk using a Linux system that is less than impenetrable.
[*]If the damage to the system itself is so extensive that reinstalling would just be faster. For example, you might have missing or corrupted files in /usr/lib that apt has lost track of, or something. Conversely, damage to /etc is never a reason to reinstall.
[/LIST]

> **SupaRice said:**
> I have tried following the directions others have listed on reinstalling GRUB, but it doesn't seem to work for me given my crazy partitioning.Likewise, a screwed up bootloader (ie a few bytes of code) is never _ever_ a reason to reinstall an entire operating system. To manage a bootloader successfully in the long term, you do need to have a complete grasp of how it and your system work together though. Common mistakes include...
[LIST]
[*]Grub (or another bootloader) breaks, the user reinstalls it, and nothing changes, because they've (re)-installed it to the wrong MBR. Naturally, this can only happen on systems with more than one hard disk.
[*]A bootloader breaks, and attempts to fix it make things worse, because its config files aren't set up properly.
[*]The problem isn't with the bootloader at all, but the parameters passed to the kernel *by* the bootloader.
[/LIST]

People who get their bootloader tangled up in knots (it happens to everyone hehe) often wind up with several of them, which starts to get very confusing. For instance, I have one PC with an IDE slot in the front of it. Every time I plug a disk into it, my BIOS rather stupidly takes it upon itself to change my disk boot order. Over time, I have accumulated non-functional copies of lilo & grub on almost all of the disks in the machine (that I haven't bothered to delete), so when I take the disk back out of its slot, it can take me a few minutes to find the right one, and figure out the correct disk order again!

Anyhow, this post has gotten long enough! I hope something in here is useful.

---

### Post by SupaRice on 2007-06-14
> **kidders said:**
> In your case, since your RAID arrays don't form part of the Linux system itself, I would wait until after the installation to set them up ... which is trivial, in any case.


Thanks for your reply!  The questions I have is this.... If I do wait until after installation to mount my RAID drives, how does that work with my /home being on one of those RAID disks?  Because setup will create one in the /root if I don't tell it otherwise correct?

Also, how do I set them up after the installation?  I used the installation to create them last time, and don't know how to generate RAID otherwise.

Third, what WOULD be the most efficient way to set this up given that redundant /home is my goal with the RAID in the first place?

---

### Post by kidders on 2007-06-15
> **SupaRice said:**
> If I do wait until after installation to mount my RAID drives, how does that work with my /home being on one of those RAID disks?In general, you would log into your box using an account that doesn't reside in /home (eg root), so that your can manipulate the directory safely. In the case of Ubuntu (since the root account is normally disabled), you could boot into single user mode, or use a boot CD.

Then, you would do something like the following...[LIST=1]
[*]lsof | grep /home [COLOR="Red"][SIZE="1"][ Just to make sure nothing in /home is in use. ][/SIZE][/COLOR]
[*]mv /home /home.old [COLOR="Red"][SIZE="1"][ Or you could simply delete the directory. ][/SIZE][/COLOR]
[*]mkdir /home [COLOR="Red"][SIZE="1"][ Recreate the directory. ][/SIZE][/COLOR]
[*]mount /dev/md0 /home [COLOR="Red"][SIZE="1"][ Mount the appropriate RAID device. ][/SIZE][/COLOR]
[/LIST]

Then, you could modify your /etc/fstab to have your RAID device mounted into /home automatically the next time, and reboot. Note that it's always safest to do these things in a _text only environment_.

> **SupaRice said:**
> Also, how do I set them up after the installation?  I used the installation to create them last time, and don't know how to generate RAID otherwise.The main reason I suggested avoiding asking the installer to do the above for you is that I've seen a large number of threads on here, started by users who have had trouble getting it to do RAID-related stuff without making mistakes. I felt reluctant to recommend doing something that might compromise your personal data. However, if you feel more confident about using the installer than taking a more manual approach, you should probably do what you're familiar with. :-)

Ubuntu *should* automatically reconstruct your RAID arrays for you at boot time, even if you don't tell the installer to expect them ... but on the off-chance it doesn't, you could add a few **mdadm** commands before step 4 above. For example...
```
mdadm --assemble /dev/md0 /dev/hda1 /dev/hdc2 [COLOR="Red"][SIZE="1"][ To manually reassemble the array. ][/SIZE][/COLOR]
mdadm --detail /dev/md0 [COLOR="Red"][SIZE="1"][ To satisfy yourself that everything's okay. ][/SIZE][/COLOR]
```I would expect anything like this to be unnecessary though.

> **SupaRice said:**
> Third, what WOULD be the most efficient way to set this up given that redundant /home is my goal with the RAID in the first place?What you've done seems perfectly fine to me. :-) although, if you had a blank slate again, it might be possible to rearrange some of your partitioning to make some minor improvements. The idea itself (ie keeping a redundant copy of /home) is very nice. The beauty of using software RAID to do it is that you can be completely confident that all Linuxes will fully support it until the end of time itself (hehe). In my opinion, it's well worth taking the time to learn to play with your array manually, so that if you ever find yourself having to recover from some sort of disaster, you feel confident that you can reconstruct your data without any hassle.

You seem a little concerned that your partitioning scheme is a little wild. It's certainly more involved than what many users come up with, but there's nothing wrong with that. It strikes me, for instance, that (a) you've put your root filesystem & swap on different physical devices, which can be smart, and (b) your RAID0 array is all on the same I/O bus, making it less likely that the components will operate at different speeds & hold eachother up. Also, the fact that you're only mirroring /home reduces the size of the performance hit RAID1 hits some systems with. You and I both seem to have the same policy when it comes to redundancy ... ie the OS is disposable ... only the "real" data is important.

I hope that answers your questions. When/if you reinstall, do whatever you feel more comfortable with to your /home ... but do be careful with the installer!

---

### Post by SupaRice on 2007-06-16
It worked!

Posting from my new install, with all of my data still intact!

Now, i've just got to get all of my stuff reconfigured like I had it before.  Thanks!

---

### Post by kidders on 2007-06-16
Excellent news. :-)

With luck, the settings (ie all the directories that start with '.') in your home directory will all wake up again, as you reinstall the software they apply to. Mail, IM histories, browser bookmarks, desktop wallpapers, etc. should all be there waiting for you.

I'd say it's probably too late now, but it strikes me that some of the stuff in your old /etc directory might also be helpful. For instance, if you'd laboured to set yourself up a web server or maybe Samba filesharing, just the way you like it, it's nice to be able to restore the original configuration with a simply copy.

All the best!

---

### Post by SupaRice on 2007-06-17
Spoke too soon! :o

So, now I have this strange situation:
I sorta followed your suggestions, only when I booted into my new system the first time it seems that only one of my /home RAID partitions was active.  So now, every other boot brings me up to a working system.  Other times, I get a non functioning system, because the other array partition doesn't have the updated/fixed data for my /home.... ie, it doesn't have my account's home directory etc...   So I think I can remedy this via mdadm while booted into the partition that has the right stuff on it, only I don't know how.  And I'm scared I'll do it wrong and wipe out the good side of the array with the bad.  Make sense?  The below output might help?  Suggestions on how to fix this array?

```

root@fs01:~$ cat /proc/mdstat
Personalities : [raid0] [raid1] 
md2 : active raid0 sdc1[0] sdd1[1]
      488391808 blocks 64k chunks
      
md1 : active raid1 sdb2[1]
      97659008 blocks [2/1] [_U]
      
unused devices: <none>
root@fs01:/home/phignutt# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Mar  6 14:29:59 2007
     Raid Level : raid1
     Array Size : 97659008 (93.13 GiB 100.00 GB)
    Device Size : 97659008 (93.13 GiB 100.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun 17 01:36:34 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 37918202:c092129c:4f048ba0:4e83cc1c
         Events : 0.340504

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2


```

---

### Post by kidders on 2007-06-17
Hmmm...

Your /home is RAID 1, right? If that's the case, being missing one component shouldn't be at all noticeable, since the mirror can carry on perfectly happily on its own. Having said that, we certainly have to get to the bottom of what's wrong ... but I'm just curious about how you even noticed the problem!

One important question is this... did you reinstall the same version of Ubuntu that you had before? This normally shouldn't make the slightest difference, but there are several possible issues that I'd like to eliminate.

---

### Post by SupaRice on 2007-06-17
I installed 7.04 and was in the process of upgrading 6.1 to 7.04 when it blew up, so yes and no about the same version question. :)

Here's what I think is happening.  The RAID array is only using one drive.  The first couple of times it booted up it was using the same one, so at the time, both drives had the same data.  When I installed the new system, I used a default user of "paul", then added back my regular user account and moved my old data back.  Then I made some changes, added users back, restored data, etc....  Then I rebooted it and it came up with the other drive which was now outdated, if that makes sense.  So when I went to login my account's home directory was missing, causing X to freak and kick me out.  I rebooted again, and everything was fine.  I did a "cat /proc/mdstat" both times and noticed that this line changed from:

```
97659008 blocks [2/1] **[COLOR="Red"][_U][/COLOR]**
```

to

```
97659008 blocks [2/1] **[COLOR="Red"][U_][/COLOR]**
```


So my guess is that it's just picking a drive at random when it boots and not bringing the other drive into the array.  I'm up and running on the correct one now, so I tried this to remove and re-add the other drive but got the below error message and so I stopped messing with it before I screwed it up.  ;)

```

root@fs01:/home/john# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Mar  6 14:29:59 2007
     Raid Level : raid1
     Array Size : 97659008 (93.13 GiB 100.00 GB)
    Device Size : 97659008 (93.13 GiB 100.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun 17 01:47:09 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 37918202:c092129c:4f048ba0:4e83cc1c
         Events : 0.340640

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
root@fs01:/home/john# mdadm /dev/md1 --add /dev/sda2
mdadm: Cannot open /dev/sda2: Device or resource busy
root@fs01:/home/john# mdadm /dev/md1 --fail /dev/sda2
mdadm: set device faulty failed for /dev/sda2:  No such device
root@fs01:/home/john# mdadm /dev/md1 --remove /dev/sda2
mdadm: hot remove failed for /dev/sda2: No such device or address

```


Does that help?  I think all I need to do is somehow remove the second drive from the array and then re-add it.  But I don't know how and I'm afraid of destroying the array. :(

---

### Post by kidders on 2007-06-18
Hmmm...

The reason I asked about Ubuntu version changes is that, from time to time, changes to the order in which things happen at boot can unexpectedly affect certain hardware. Perhaps an easier (but less realistic) example to follow might be one I encountered recently, where the components of a RAID 1 array I created were in different computers. Suppose the boot order in one version of Linux was ...[LIST=1]
[*]Local disks
[*]Networking
[*]RAID
[*]...[/LIST]... and an upgrade of some sort changed it to ...[LIST=1]
[*]Local disks
[*]RAID
[*]Networking
[*]...[/LIST]It's easy to see why, all of a sudden, my RAID array would perpetually start up degraded, because when the system reconstructed it, it wouldn't have access to my network yet, to go fishing for the non-local components. It's possible that this sort of thing might be happening to you ... but if so (and there's nothing else going on), I'm tempted to think that what you've discovered is a bug.

> **SupaRice said:**
> ```
97659008 blocks [2/1] **[COLOR=Red][_U][/COLOR]**
```to```
97659008 blocks [2/1] **[COLOR=Red][U_][/COLOR]**
```This is strange. It feels a little like, for some reason, both of your drives might not be ready/available at the critical moment in the boot process, but that there's a certain randomness to which one it is. Unfortunately, until we get to the bottom of this odd problem, [COLOR=DarkRed]**if you cannot predict which RAID component will be used, you should disable or unplug one of them to avoid losing data**[/COLOR].

> **SupaRice said:**
>  ```
root@fs01:/home/john# mdadm /dev/md1 --add /dev/sda2
mdadm: Cannot open /dev/sda2: Device or resource busy
```I don't like this. Just to reassure you though, provided you can be 100% certain of the following, you _cannot_ damage your array by repeatedly trying to add or remove component devices...[LIST]
[*]Pick a disk that you consider, for the moment, to be the "master" disk ... ie one that is always in the array. It must not be the one you are trying to add back in.
[*]Any disk you try to add will always be treated as though the array had never seen it before, and its contents will be completely overwritten. This disk cannot be smaller than the other one in the array.[/LIST]Anyhow, let's try to solve this!

** - I -**
The first thing I would do is consider making an emergency backup. This is not always possible when dealing with RAID, because most people simply don't have enough free storage space available to accommodate all the data. If, however, you do, I would suggest thinking about dumping the contents of what you might call your "master" RAID component partition to a file. That way, you could afford to be reckless, and try things you wouldn't otherwise like to do.

** - II -**
The second thing I would do is check my /etc/fstab for references to *components* of your array (ie not the array itself). None should exist. I would also remove references to the array itself, so my system made no attempt to mount it automatically. Then I would boot in recovery mode, into a text only console. Executing **whoami** should return "root". The purpose here is to start from square one, and try to reconstruct the array properly once.

An **mdadm --detail** should tell you that your array is "clean, degraded", and that the component you consider the "master" is the one that's alive. If an attempt to re-add the missing component tells you "Device or resource busy", we'll try step III. Hopefully though, the array will reconstruct, and a **cat /proc/mdstat** will tell you so. While it's doing that, you can do ...```
mkdir /mnt/raid
mount -o ro /dev/md0 /!$
```... substituting the correct device name, to mount the array in read only mode. That way, you can walk around it, and convince yourself it's okay. Once it's reconstructed...```
cd /
umount mnt/raid
nano -w /etc/fstab [SIZE=1][COLOR=DarkRed][put back a reference to your RAID array.][/COLOR][/SIZE]
shutdown -r now
```[LIST]
[*]Reboot normally.
[*]Drop to a text-only console.
[*]Check that both array components are present.
[*]Play around in text mode for a few minutes.
[*]Reboot again.
[*]Check your array one more time.[/LIST]If you can get this far without problems, we're in business. :-)

**- III -**
If you run into difficulty, we need to start looking for reasons the components of your array might not be available for use at the critical moment, when your arrays are put together at boot time. The contents of /var/log/messages, /var/log/syslog and **dmesg** may be helpful. This post is getting *waaaay* oversized though, so I'll type more about that if it becomes necessary.

In the meantime, I realise that (a) there's quite a lot in here, (b) you're dealing with something that may be related in some way to a bug in Ubuntu, and (c) you simply can't afford to risk damaging your personal data ... so I'm available all day on IM to walk you through things, if you need a hand.

---

### Post by SupaRice on 2007-06-18
Thanks so much for your help.  I'm going to try your suggestions before bothering you on IM.  But when you have time, please PM me info on how to reach you via IM.  I do have enough disk space to make a backup, on my other RAID array that seems to work properly.  

That leads to something else I wanted to mention, when you were saying there may be some reason for the resources not being available....

The other RAID array works fine, every time.  It is on the SATA drives which are dedicated to RAID 0.  This array that I'm having problems with is made of 2 partitions, 1 partition on two IDE drives, which also contain a partition for / and /var one of those being on each of the drives.  So I guess that the drives are actually available otherwise the system couldn't be booting?

---

### Post by SupaRice on 2007-06-27
:redface:

```

root@fs01:/home/john# mdadm /dev/md1 --add /dev/sda[COLOR="Red"]**1**[/COLOR]
mdadm: re-added /dev/sda1
root@fs01:/home/john# 
root@fs01:/home/john# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Mar  6 14:29:59 2007
     Raid Level : raid1
     Array Size : 97659008 (93.13 GiB 100.00 GB)
    Device Size : 97659008 (93.13 GiB 100.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun 27 09:31:50 2007
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 0% complete

           UUID : 37918202:c092129c:c16d14f0:d6ed4df2
         Events : 0.352020

    Number   Major   Minor   RaidDevice State
       2       8        1        0      spare rebuilding   /dev/sda1
       1       8       18        1      active sync   /dev/sdb2
root@fs01:/home/john# 
root@fs01:/home/john# cat /proc/mdstat
Personalities : [raid0] [raid1] 
md2 : active raid0 sdc1[0] sdd1[1]
      488391808 blocks 64k chunks
      
md1 : active raid1 sda1[2] sdb2[1]
      97659008 blocks [2/1] [_U]
      [=>...................]  recovery =  6.5% (6364992/97659008) finish=36.7min speed=41425K/sec
      
unused devices: <none>


```

Looks like I had the wrong drive number earlier.  So, it's rebuilding now it says.  I wonder if that fixes the issue when I reboot though?  Will it still join both of them to the array properly?  I'll test that theory later, unless you think that would maybe damage things?

---

