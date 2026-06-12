---
title: "Partitioning questions."
date: 2008-03-14
forum: General Help
---

### Post by Arcor on 2008-03-14
I installed Ubuntu, and used the "Guided - Use largest continual free space" (or similar named) option for setting up the partitions.

Now i'm in this situation:

8GB Empty Space (Marked Unusable in the Installation Partition Manager, not sure why this is here.)
12GB NTFS partition, for Windows
~130GB Ext3 Partition, for Ubuntu
2GB Swap Partition.

I'm wanting, essentially, to change the 130GB Ext3 Partition into a 12GB or so Partition for Ubuntu and the rest of it as space which both Windows and Linux can read and write. 

First question, then, is how would i go about getting hold of a program to partition drives with?

Secondly, i'm fairly certain i'd have to delete the 130GB partition and convert the resulting free space into 2 partitions?

and finally, Is it worth using some of the shared partition (both SO' can read/write to it) for OS-specific applications, such as installing a Win-only application to it, or should i simply make my Windows and Linux partitions bigger to make sure they can hold the apps for their specific OS?

I appreciate that a lot of this sounds incredibly simple to some of you, but i've only installed Ubuntu last night/this morning, and am trying to learn :P

---

### Post by logos34 on 2008-03-14
> **Arcor said:**
> First question, then, is how would i go about getting hold of a program to partition drives with?

System>admin>partition editor (Gparted)

Read the docs at the website.

> Secondly, i'm fairly certain i'd have to delete the 130GB partition and convert the resulting free space into 2 partitions?

Actually, you can simply shrink ubuntu root partition down, then create a new ext3 (extended) partition, possibly incorporting the 8 GB space.  (If /swap separates it, move it).


I'd keep apps for each OS on their own partitions, but you can share data partition using fs-driver or ntfs-3g, depending on whether its ext3 or ntfs.  

You might also look into running your windows programs in linux on Wine--then you could dump windows and liberate another 12gb space.

---

### Post by gobuntu on 2008-03-14
Hi Arcor,

The 8GB partition is most likely a reserved space for Windows use, likely where files are for a reset the pc to store-shelf condition, OR, for system restores. Those partitions have special type codes that Linux installations don't use.

You did end up with a very large partition for Linux. 

You could, from Windows, delete that Linux partition and start over.

There are many ways to do it, but what I  would do is make a large NTFS partition in which I  can put BOTH windows data and Linux data, now that Linux can read/write both, specially if the data you are to have there is things like music, movies, and so forth.

If you are to do Linux work like large databases, or other programs that use a lot of data, of movie editing, or multimedia in linux, then you do larger linux partitions.

I have always separate partition for data, anyway, and typically 12 GB for windows INSTALLATION, and about 6 GB for Linux INSTALLATION and some data is fine, the rest of the disk is an NTFS partition for data which both Windows and Linux can read and write to, with no risk of being in systems files either way.

This is also great for backups, re-installations, etc.

---

### Post by Arcor on 2008-03-14
Thanks guys.
I think i'll take your suggestion, Gobuntu, and shrink the Linux partition down to around 6-10gig, and create a new NTFS partition for data storage. (I had no idea Ubuntu could write to NTFS, i was told that it had to be FAT32 if i wanted both OS to be able to read/write.)

I just did sudo apt-get install gparted, and it seemed to install fine, but Gparted's not showing up in my Applications menu, any ideas?

---

### Post by gobuntu on 2008-03-14
> **Arcor said:**
> Thanks guys.
I think i'll take your suggestion, Gobuntu, and shrink the Linux partition down to around 6-10gig, and create a new NTFS partition for data storage. (I had no idea Ubuntu could write to NTFS, i was told that it had to be FAT32 if i wanted both OS to be able to read/write.)

I just did sudo apt-get install gparted, and it seemed to install fine, but Gparted's not showing up in my Applications menu, any ideas?

Not all we install shows in the menu, (specially if they are terminal text based programs), but you can in a terminal type gparted if it indeed installed.

Or, you can check in Applications to see if you can Add it to the menu.

---

### Post by Arcor on 2008-03-14
I've managed to navigate to gparted, and i'm looking at my partitions right now, but i can't move/resize the partition (presumably because it's mounted, but it won't let me unmount it. It said there may be other partitions mounted on the mountpoint, but i've unmounted every partition i have and still getting the error.)

---

### Post by sandysandy on 2008-03-14
u can use the gparted live CD to resize partitions . u can download it from the net. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

that way u will find the partitions u want to work on are not mounted.

regards

---

### Post by gobuntu on 2008-03-14
> **Arcor said:**
> I've managed to navigate to gparted, and i'm looking at my partitions right now, but i can't move/resize the partition (presumably because it's mounted, but it won't let me unmount it. It said there may be other partitions mounted on the mountpoint, but i've unmounted every partition i have and still getting the error.)

I don't think you can resize the Linux partiton because it is Active.

As said above, you do it via the boot live CD of Ubuntu that you already have (which I think it has gparted), Knoppix, or similar.

---

### Post by Arcor on 2008-03-14
I've run the LiveCD, and i've rearranged some of the partitions and can quite simply make one from here, however, after quickly double checking, i've found nothing online to indicate that Ubuntu can read/write to NTFS partitions without NTFS-3G.

A few things say that NTFS-3G isn't 100% stable, is it worth risking it, or simply settling for FAT32 (If i'm even correct in assuming that windows and Linux can both write to and read from FAT32.)

Again, thanks for all your help :)

---

### Post by diegosouza on 2008-03-14
Hey man, nowadays ntfs-3g is stable. When you read a post telling it isn't stable, pay attention to the published date.

Regarding the partitions, I have another suggestions to you, if you don't mind about 3D video acceleration for some windows games, you could keep just ubuntu and install the windows as a virtual machine. It's very easy to use Virtualbox for it. Through Virtualbox you cold easily share folders between the host system (ubuntu) and the guest system (windows).

I told it all because you have 2 GB of swap, so if you have at least 1 GB of RAM memory, you can run at least one virtual machine without problems.

---

### Post by sandysandy on 2008-03-14
>  however, after quickly double checking, i've found nothing online to indicate that Ubuntu can read/write to NTFS partitions without NTFS-3G.

with ubuntu 7.10 u can both read and write to NTFS (windows) partitions.

i am doing so practically.

regards

---

### Post by gobuntu on 2008-03-14
> **Arcor said:**
> I've run the LiveCD, and i've rearranged some of the partitions and can quite simply make one from here, however, after quickly double checking, i've found nothing online to indicate that Ubuntu can read/write to NTFS partitions without NTFS-3G.

A few things say that NTFS-3G isn't 100% stable, is it worth risking it, or simply settling for FAT32 (If i'm even correct in assuming that windows and Linux can both write to and read from FAT32.)

Again, thanks for all your help :)

Hi Arcor,

So far, it is documented as 'new features' that Gutsy incorporated the achievements of the ntfs-3g project so as to read AND write reliably.

I have quite extensively verified that to be true, as far as reliability is concerned.

However, I do have an issue on what happens when data is DELETED from an NTFS partition (in Ubuntu of course), because it puts it in an invisible .Trash folder.

However, currently I am researching how to PERMANENTLY delete that .Trash folder, for when I delete THAT folder, it simply puts itself INSIDE ANOTHER .Trash folder.

For what I am doing, though, this is kind of OK, but not in the long run.

As far as Fat-32, I DO NOT recommend it to myself, as this is what I tried before nts-3g and there are problems, due to limitations, not only in Ubuntu but also in Windows.

For instance, some softwares like Databases, DO NOT work on Fat-32 because that system lacks features by them  required.

If you run those programs in Windows, use NTFS to hold their data.

If you run those programs in Linux, use ext3 for data, or other available, which have  journaling and capability to support modern security requirements of those softwares in particular.

If you just want to use those programs TO LEARN, you don't need more partition space for either than the one suggested above.

The advise is to keep it as simple as possible, and grow/compound when the need is there.

Ubuntu philosophy is kind of like that. For instance, it renders only ONE linux partition, where other systems typically install  several (makiing partitions of what in linux are subdirectories). You can do that in Ubuntu when you want to or need, though.

Good luck.

---

### Post by gobuntu on 2008-03-15
Friends,

I have now concluded that since "Empty the Trash Can" does not apply to the external, automount USB drive, any data deleted in the NTFS drive can only be PERMANENTLY DELETED from a terminal by the command "su rm -rf 
FileName".

"FileName", of course is the name of the hidden Trash file. 

Perhaps by mounting manually the USB onto a drive-place, the deleted data would go to the Desktop Trashcan, the "Empty the Trash Can" can apply also to the USB, but I have not tried that yet.

I have found no reliability nor performance problems at all.

On the contrary, all very well.

---

