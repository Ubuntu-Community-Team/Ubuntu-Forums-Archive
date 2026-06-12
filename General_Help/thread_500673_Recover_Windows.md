---
title: "Recover Windows"
date: 2007-07-14
forum: General Help
---

### Post by drba77 on 2007-07-14
I was trying to dual boot, I opened the Gparted program and in my computer i have one partition named 
/dev/sda9 which was initially about 76MGiB
I highlighted it and then clicked on new and Looks like I created something named:
/dv/sda9 and the filesystem is extended and it's 2 MiB and the previous partition is gone and called now unallocated.
Then I restarted the computer because I was planning to go to windows XP to transfer my documents into flashdrive and removed the Ubuntu DVD, but I got the message that I need to insert a CD to reboot the system.
So now I can't go back to windows and I don't know what to do.
Any help,!!!!!!!
I don't want to use the windows Xp restore D beause I don't wanna lose my files on windows.
How can I go back and reverse that step which I did using Gparted.

---

### Post by 3rdalbum on 2007-07-14
The only thing you can do is restore your system from the backups you made - you have erased the Windows partition.

Please tell me you made backups.

For anyone out there who's thinking of using Gparted, it doesn't matter how careful you will be or how knowledgable you think you are: Data disasters CAN happen whenever you alter the partition table, so ALWAYS make a backup of all your data first.

Drba77, just to confirm that this is what you've done, please boot the Ubuntu CD again, go into the terminal, and copy and paste this command into there:

```
sudo fdisk -l
```

Now copy and paste the result of that command into this thread.

---

### Post by Happy_Man on 2007-07-14
I am really confused. Could you post a screenshot of how Gparted looks right now so that I'm a bit more clear on this? Although, from what I can see, the only thing you can do is restore your system. Sorry, bud.

---

### Post by SendDerek on 2007-07-14
If I've read it correctly, then I'd say that you've just erased your windows partition completely.  I don't know if you can quick-format an NTFS drive and not lose data.  I've heard of some file systems(FAT32, NTFS, ect.) that you can refromat and not lose data, but that would take some research.  See what you can find.  Also, there are data restoration programs out on the market that will allow you to gather data from a HDD that has not been written over with new information.

Otherwise, you may just want to try to run the "fixmbr" "fixboot" commands with the repair utility on the Windows XP CD.  It's worth a shot anyways.


Maybe I'm jumping to conclusions...  what does your Gparted look like now?  Does it still have that unallocated space?  Now I'm thinking that as long as you didn't click the "apply" button, your partitions should still be intact with no data loss.  Then, the troubleshooting can begin.

---

### Post by Shazaam on 2007-07-14
Follow the instructions that have already been posted here.

There IS a way to restore deleted partitions but it is NOT for the timid.  test disk is on the downloadable gpartedLiveCD and you can use it to find and restore partitions.
If you have deleted them a re-install of Windows/Linux is the easiest way to fix your problem.

---

### Post by bodhi.zazen on 2007-07-14
First please use a better title. "please help anyone!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!"  does not attract the attention of folks that can help with data recovery.


Well, you may in fact be in for deep problems :)

First, do not write any more to the disk or partition the disk.

Second, try TestDisk or PhotoRec :

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

==============

Third, if that fails, try gpart :

[http://www.linux.com/feature/57748](http://www.linux.com/feature/57748)

==========

If that fails , try fdisk

Boot the live CD

Enter the command ```
sudo fdisk /dev/hda
```

Now delete all the partitions and then make one large NTFS or FAT partition (what ever you windows was) and mark it as bootable.

See here : [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

---

### Post by drba77 on 2007-07-14
Thanks for the info, unfortunatly I didn't make backup, what is the terminal that you mentioned

---

### Post by drba77 on 2007-07-14
Here what I got:
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by drba77 on 2007-07-14
Here is a screenshot of gparted in my computer now:
/home/ubuntu/Desktop/Screenshot--dev-sda - GParted.png

---

### Post by bodhi.zazen on 2007-07-14
In the terminal type : ```
sudo fdisk -l
```

That is a small "L" and not the number 1

It will list all your partitions.

Edit : Thanks davidjmayo

---

### Post by drba77 on 2007-07-14
sorry here it is:[IMG]/home/ubuntu/Desktop/Screenshot--dev-sda - GParted.png[/IMG]

---

### Post by drba77 on 2007-07-14
oh, ok, here is what i got:
Disk /dev/sda (SGI disk label): 255 heads, 63 sectors, 9729 cylinders
Units = cylinders of 16065 * 512 bytes

----- partitions -----
Pt#    Device  Info     Start       End   Sectors  Id  System
 9: /dev/sda1               0         0      4096   0  SGI volhdr
11: /dev/sda2               0      9729 156301488   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

Disk /dev/sda9 (SGI disk label): 255 heads, 63 sectors, 0 cylinders
Units = cylinders of 16065 * 512 bytes

----- partitions -----
Pt#     Device  Info     Start       End   Sectors  Id  System
 9: /dev/sda9p1               0         0      4096   0  SGI volhdr
11: /dev/sda9p2               0      9729 156301488   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

Disk /dev/sda11 (SGI disk label): 255 heads, 63 sectors, 9729 cylinders
Units = cylinders of 16065 * 512 bytes

----- partitions -----
Pt#      Device  Info     Start       End   Sectors  Id  System
 9: /dev/sda11p1               0         0      4096   0  SGI volhdr
11: /dev/sda11p2               0      9729 156301488   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

---

### Post by davidjmayo on 2007-07-14
> **bodhi.zazen said:**
> In the terminal type : ```
sudo fdisk -l[//ccode]

That is a small "L" and not the number 1

It will list all your partitions.

sorry b.z seemed your code didn't come out 

[CODE]sudo fdisk -l
```

---

### Post by drba77 on 2007-07-14
the attachement is a screenshot of gparted

---

### Post by bodhi.zazen on 2007-07-14
Yea, that looks bad. You *might* be able to revert your partition table or recover you data.

Take a look at my first post and let us know if you need help with any of those tools.

---

