---
title: "Do I need to reformat to resize my Ubuntu partition?"
date: 2008-06-20
forum: General Help
---

### Post by Aleksei Vasiliev on 2008-06-20
Currently, my partition is as follows:
[img]http://www.sovietnation.net/uploads/images/1214003717.png[/img]

However, it seems that I cannot create a new partition in the space I just unallocated, and I cannot resize my Ubuntu partition. Do I have to reformat my Ubuntu install to be able to use the unallocated space?

---

### Post by p_quarles on 2008-06-20
That's because you can only have a maximum of four primary partitions. To use that free space, you will need to add it to an existing partition. If you add it to the extended partition, you can use it to create new a logical partition.

---

### Post by logos34 on 2008-06-20
> **Aleksei Vasiliev said:**
> and I cannot resize my Ubuntu partition. 

right, because root is mounted (you're using it).  Boot the livecd and use Gparted there to do what p_quarles said, which is to grow the extended partition into the unallocated space, then expand /.

---

### Post by Zorael on 2008-06-20
As a side note, resizing a filesystem will likely give it a new UUID (incorrect?), so you'll need to update your grub menu.lst kernel entries so as not to get dumped back into a BusyBox shell when trying to boot. The **root=** argument is the one in question.
```
$ sudo blkid
```

---

### Post by Aleksei Vasiliev on 2008-06-20
And it worked.

Note that I had already resized my NTFS partition, here's what I did to resize my Linux ext3 partition:

0) Download, burn, and boot the AMD64 Ubuntu CD.
1) Open Terminal and run "sudo gparted"
2) Right-click the swap partition and hit swapoff to unmount it.
3) Select the Extended partition and Resize it +30GB.
4) Select the Linux ext3 partition and resize it +30GB.
5) Hit commit.
6) Wait an hour.

The UUID of the partitions did not change.

---

### Post by Aleksei Vasiliev on 2008-06-20
I am now having major problems.

Gnome keeps freezing (the top bar with Applications, Places, System, etc. and the bottom bar with the programs).
When doing a browse command, such as hitting Open or Save in a program, it often freezes for up to 15s before opening the folder.

What can I do?

---

