---
title: "Questions on partition notifications and actual sizes"
date: 2020-08-10
forum: General Help
---

### Post by davepool on 2020-08-10
I could just as easily have posted this in New to Ubuntu (since I still am...sorta) but since the questions are only peripherally related to an Ubuntu distro (Kylin) and are more about Linux, I thought it best to leave them here.

So over the weekend I decided to do a little distro hopping and, on the strength of all of the updates and improvements now in Kylin 20.04.1, I decided to install that over a Manjaro installation that was already in place and functioning. I was, per usual, just going to opt for "Other" with the installer and choose that partition.

The first thing I noticed was the installer notifying me “Partition 9 does not start on physical sector boundary” and that (IIRC) I should delete the partition and re-create it.  I deleted it (via the installer...or so I thought) and then realized I was probably over my head a bit and opted for the expedient solution of backing up a step or two in the installer and opting for Install Alongside...etc.

Anyway, that all went well and Kylin was installed...but I noticed GRUB still showed Manjaro, even though that partition had been deleted (supposedly). But it hadn't been. Using Fdisk (and some instructions I found), I was able to delete sda9 and, once I updated GRUB and reinstalled it, the "phantom" entry of Manjaro in the menu was gone.

Leaving me with these two questions: 

1) What was that notification of "Partition 9 does not start on physical sector boundary" all about and what would the "more correct" response to it have been? 

2) Why do Disks and GParted report noticeably different sizes for the partitions my two Linux distros occupy?  Disks shows Ubuntu Kylin in a partition (sda10) of 97GB and EndeavourOS in a partition (sda8) of 98GB while GParted shows those two partitions as 90.68 and 90.99 respectively?

---

### Post by oldfred on 2020-08-10
Alignment is only important on newer 4K physical partitioned drives. Large drives & SSDs are now mostly 4K drives. But if older 512 sector drive warning will not matter. If using the now very old MBR(msdos) partitioning the extended partition will also give error, but that error does not matter.

Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://developer.ibm.com/technologies/linux/](https://developer.ibm.com/technologies/linux/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Some Linux tools show partition size before formatting uses space for journal. Linux also allocates 5% for superuser to try to prevent a crash if you let it get full.

---

### Post by kneutron on 2020-08-10
> I deleted it (via the installer...or so I thought) and then realized I was probably over my head a bit and opted for the expedient solution of backing up a step or two in the installer and opting for Install Alongside...etc.

--When you went back in the installer menu, it probably discarded a pending operation instead of committing it to disk.  Gparted does similar.  Even fdisk will not write pending operations to disk until you commit with 'w'.  **Parted** is different, so beware if you use that program.

> 2) Why do Disks and GParted report noticeably different sizes for the partitions my two Linux distros occupy?

--Probably the difference between GB and GiB.  Of the two, I would trust **Gparted** a bit more.  If you have two different interpretations of available space, it's probably better to trust the smaller of the two - just in case.

REF: [https://docs.ukcloud.com/articles/other/other-ref-gib.html#:~:text=GiB%20(Gibibytes)%20is%20a%20standard,is%20defined%20as%201024%C2%B3%20bytes.](https://docs.ukcloud.com/articles/other/other-ref-gib.html#:~:text=GiB%20(Gibibytes)%20is%20a%20standard,is%20defined%20as%201024%C2%B3%20bytes.)

> What was that notification of "Partition 9 does not start on physical sector boundary" all about and what would the "more correct" response to it have been?

--Use gparted or fdisk to create your partitions and you shouldn't have to worry about it, they should end up aligned properly.

---

### Post by davepool on 2020-08-10
> **oldfred said:**
> Alignment is only important on newer 4K physical partitioned drives. Large drives & SSDs are now mostly 4K drives. But if older 512 sector drive warning will not matter. If using the now very old MBR(msdos) partitioning the extended partition will also give error, but that error does not matter. 

I suppose I could have/should have further explained that the device is a Lenovo Flex 3 that was once a Windows 10 unit. Check that, it still is. When I first started exploring Linux, this was my "donor device" and I was reluctant to have my first install (Linux Mint) completely wipe the HD so, as a result, that was my first "install alongside" procedure. Net-net, there are still quite a few partitions (both ntfs and fat32) that are either Windows or Lenovo ID'd.

As for the rest of the info in your post, I appreciate receiving it but, gads, I'm gonna hafta spend some time absorbing it. Are you familiar with the acronym MEGO?  It stands for My Eyes Glazed Over! &#55357;&#56838;

---

### Post by davepool on 2020-08-10
Good info there, thanks @kneutron! Yeah, I was aware of the Fdisk need for the "w" command to write changes. Good to know that GParted might work much like the installer and not move ahead with a function until or unless *you* have moved ahead. 

Fact is, I've only looked at GParted, never used its functions. Of course, I'd seen it mentioned many times. But last night an online friend said he was puzzled why I didn't use it when the installer said sda9 needed to be deleted (if only to have the friendliness of a GUI and not need the terminal) and my reply was "Because I don't have it (in Kylin). And in distros where I *might* have had it, I've never used it." I'm not a whole lot more fond of the terminal than he is but, hey, once I looked it up, Fdisk was "get into command mode" and, after that, 3 single key entries (the last being "w") and I was done!

---

