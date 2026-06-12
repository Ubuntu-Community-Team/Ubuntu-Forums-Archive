---
title: "Disk capacity, free space, and Ext3 reserved blocks"
date: 2006-07-13
forum: General Help
---

### Post by j3r3miah on 2006-07-13
I have recently switched over a partition from NTFS to Ext3. There is some missing disk space that I can't account for. I'm sure there is a reasonable explanation I'm missing. Here's the situation:

I have two identical 320GB hard disks. One is in a firewire enclosure, but I don't think that is relevant. They are identically sized.
```

[FONT="Courier New"]Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS[/FONT]
```
One contains an Ext3 filesystem while the other is still NTFS. The df report is what confuses me:
```

[FONT="Courier New"]Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdb1     ntfs    299G  268G   31G  90% /media/Downloads
/dev/sdb1     ext3    294G  103G  192G  35% /media/Backup[/FONT]
```
So here's the question: **How come the Ext3 drive reports a size of 294G while the NTFS drive reports a size of 299G?** I calculate 298.09GB. 

Additionally, since I only plan to use this drive for backups and shuffling around big files, I used tune2fs to reduce the reserved blocks to zero. **What are the consequences of having no reserved space in an Ext3 filesystem? Does this disable journalling?** As I understand it, the journal is not stored in that space--correct? I'm not terribly concerned about fragmentation. If I need the full capacity of the drive, it will only be temporarily and speed won't be critical.

Perhaps my two questions are really two views of the same issue. Maybe the unnaccounted-for 5GB is holding the journal and othersuch filesystem housekeeping devices which I don't understand. Can anyone confirm?

**The missing space is not accounted for by reserved blocks--I have already reduced that to zero with tune2fs -m 0.**

---

### Post by j3r3miah on 2006-07-14
> **j3r3miah said:**
> Perhaps my two questions are really two views of the same issue. Maybe the unnaccounted-for 5GB is holding the journal and othersuch filesystem housekeeping devices which I don't understand. Can anyone confirm?
Well I can confirm that the lost 5GB are certainly not holding the journal. I just formatted the NTFS drive to Ext3. I noticed in the output that the journal is only 32768 blocks--128MB. df actually shows that space as used, as you can see on the freshly formatted drive:
```

[FONT="Courier New"]Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdb1     ext3    294G  129M  294G   1% /media/Downloads[/FONT]
```
So where did the ~5GB go? Anyone?

---

### Post by HAARP on 2006-07-14
ext2/3 by default reserves 5% of the space for the poweruser. You can change that in the formatting tool, tho.
That's why I use ReiserFS ;)

---

### Post by RAOF on 2006-07-14
> **j3r3miah said:**
> ...**What are the consequences of having no reserved space in an Ext3 filesystem? Does this disable journalling?**
...
The reserved blocks are there for root's use.  The reason being that the system gets **really** narky if you completely run out of room on / (specifically /var, or /tmp, I think).  Programs won't start, wierd errors will pop up, that sort of thing.  With some room reserved for root, you can at least be sure to be able to run the really **important** programs, like sudo and rm :).

So, in short, if the drive doesn't contain /var or /tmp, then there's not much point in having space reserved for root.

---

### Post by j3r3miah on 2006-07-14
> **RAOF said:**
> So, in short, if the drive doesn't contain /var or /tmp, then there's not much point in having space reserved for root.
That's just what I wanted to hear. Thanks.

Still, any idea where my 5GB went?

---

### Post by j3r3miah on 2006-07-15
Really? No one has any idea? I tried to find a white paper on the Ext3 filesystem that might explain it, but so far nothing.

It's not that I think my space is "lost" and I want to recover it... I just want to know what it's being used for and why. Who knows? Somebody knows.

---

### Post by HAARP on 2006-07-15
Is there much stuff on it? ext2/3 does a terrible job at handling folders. The folder structure alone can sometimes take up to several hundred MBs. But 5GB? I don't know
According to some file system comparisons, ext2/3 decreases your disk space. And I'm not talking about those 5% for the superuser.

[img]http://linuxgazette.net/122/misc/piszcz/group001/image003.png[/img]
([http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html))

---

### Post by Littleweseth on 2006-10-13
Can someone confirm my outline of the steps needed to format an existing partition to ext3 without the superuser-reserved space? I'm a bit twitchy about figureing this out myself, since last night i typoed '1' for '2' in the command mkfs.ext3 /dev/sda2. Bye bye very large data partition - oops!

anyway, my proposed comnand list to format /dev/sda2 to ext3;
sudo mkfs.ext3 /dev/sda1
sudo tune2fs -m 0
sudo e2fsck

The last is included because according to the manpage of tune2fs, doing tricks like reducing the reserved space makes linux unhappy.

(As a sidenote, data recovery software like GetDataBack and Stellar Phoenix for windows worked wonders on my rather large collection of files... are there equivalents for linux? All i managed to find was Foremost (foremost.sourceforge.net) - which is a shade intimidating.)

---

### Post by dcstar on 2006-12-31
> **j3r3miah said:**
> Really? No one has any idea? I tried to find a white paper on the Ext3 filesystem that might explain it, but so far nothing.

It's not that I think my space is "lost" and I want to recover it... I just want to know what it's being used for and why. Who knows? Somebody knows.

Use the **baobab** package to check it, it seems to report the correct "Available" number where df doesn't.

I suspect that df doesn't report space that *may* be required by the FS under certain circumstances (the space may be technically available, but df only lets you know what is available for user purposes).

---

### Post by jmccarthy14 on 2007-04-25
check this out though:

joseph@joseph-laptop:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             13456612  12334220   1122392  92% /
varrun                  517844       148    517696   1% /var/run
varlock                 517844         4    517840   1% /var/lock
procbususb              517844       124    517720   1% /proc/bus/usb
udev                    517844       124    517720   1% /dev
devshm                  517844         0    517844   0% /dev/shm
lrm                     517844     23052    494792   5% /lib/modules/2.6.20-15-generic/volatile



.... don't think thats superuser space.  baobab claims 31.4 gig .  now what happened was i deleted an ext3 partiton and extended//resized the one that was before it over the open space.  i have a feeling that the data from the old partition is not clean/clear, and its accounting for most of my wasted space.  what do i do/

---

### Post by erikf154 on 2007-11-11
Even easier (more readable):
**df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.7G  4.5G  234M  96% /
varrun                 506M  276K  506M   1% /var/run
varlock                506M        0  506M   0% /var/lock
udev                   506M   104K  506M   1% /dev
devshm               506M        0   506M   0% /dev/shm
lrm                       506M    33M  473M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6              33G    27G   3.8G  88% /home
/dev/sda7              92G    81G   6.1G  94% /music
/dev/sda3             7.1G   6.4G   693M  91% /windows

---

### Post by Keith Hedger on 2007-12-16
dont forget to unmount your drive before trying to format it!

---

### Post by bigmell2 on 2008-03-28
I know this thread is old but here is your solution on this page...

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)


to sum up run...

sudo tune2fs -m 0 /dev/sda1

replace /dev/sda1 with whatever the name of the disk is.  You can find this out by typing 

df -H

---

### Post by egorchel on 2008-06-05
Hey Folks!

Just came across this thread, I see it has been solved, but it seemed
strange that no one read the man pages... it says definitively where that
5% of storage goes:

```
chelhost ~# man mkfs.ext3
```

scroll down a bit:

```
-m reserved-blocks-percentage
      Specify the percentage of the filesystem blocks reserved for the super-user.  This avoids fragmentation, and  allows  root-owned
      daemons,  such as syslogd(8), to continue to function correctly after non-privileged processes are prevented from writing to the
      filesystem.  The default percentage is 5%.
```

Man pages are the best source of info when it comes to such quirks.

Egor.

---

### Post by articpenguin on 2008-06-10
ext3 has the most overhead out of all the filesystems in the linux kernel.

---

