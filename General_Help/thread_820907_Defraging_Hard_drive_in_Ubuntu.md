---
title: "Defraging Hard drive in Ubuntu?"
date: 2008-06-06
forum: General Help
---

### Post by jras20 on 2008-06-06
Do I need to de frag my hard drive in Ubuntu?  I had Windows Vista but quit using it now in Ubuntu.  I hear you dont need to, is that true?
Thanks

---

### Post by HDave on 2008-06-06
Ubuntu uses the ext3 file system.  The way it works interally is such that it does not need to be defragged.  

Just another great feature of linux over windows.

---

### Post by Pjotr123 on 2008-06-06
You heard correct:
[http://ubuntutip.googlepages.com/faq](http://ubuntutip.googlepages.com/faq)
(number 3 )

Provided you have at least 20 % free space on the partition.

---

### Post by y-lee on 2008-06-06
You usually do not need to defrag linux file systems but it is *not true* that they can not become fragmented:

> There is a myth that “linux filesystems don’t need to be defragmented.” As it may be truth in general, it still can be dispelled by a simple script, which creates a certain number of directories and in each of them creates and deletes a certain number of files - in, let’s say, two passes. So, does your filesystem need defragmentation?

See [Defragmentation of Linux Filesystems]("http://polishlinux.org/apps/cli/defragmentation-of-linux-filesystems/")


You may also want to see [Ext4 defragmentation with e4defrag]("http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/")

Note however the average person does not need to defrag as others above have said. :)

---

### Post by Pjotr123 on 2008-06-06
> **y-lee said:**
> You usually do not need to defrag linux file systems but it is *not true* that they can not become fragmented:



You may also want to see [Ext4 defragmentation with e4defrag]("http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/")

Note however the average person does not need to defrag as others above have said. :)

Keep at least 20 % free space on your partition: fragmentation will remain below 1 % and probably even below 0,5 %. 

Whatever you do, don't mess with potentially dangerous defraggers! They can muck up your system real bad. Increase partition size or delete files if free space threatens to sink below 20 %. Much wiser.

---

### Post by y-lee on 2008-06-06
> **Pjotr123 said:**
> Keep at least 20 % free space on your partition: fragmentation will remain below 1 % and probably even below 0,5 %. 

Whatever you do, don't mess with potentially dangerous defraggers! They can muck up your system real bad. Increase partition size or delete files if free space threatens to sink below 20 %. Much wiser.

I **would not** advise the average new to linux person to defrag, i posted the links to the articles on defragmentation and linux for educational purposes. Linux gurus however are free to do what they want to and usually don't care (much that is) if they trash their system doing something dumb.

---

### Post by Sef on 2008-06-06
Ext3 automatically defrags about every 25 or 30 boots.  

Reiferfs does not ever need to be defragged.

---

### Post by Joeb454 on 2008-06-06
> **Sef said:**
> Ext3 automatically defrags about every 25 or 30 boots.  

Reiferfs does not ever need to be defragged.

I never knew that about ReiserFS :)

And I believe you can use "tunefs" to change how often Ext3 does this? Or is that to change how often it checks the integrity of auto-mounted NTFS drives?

---

### Post by ctrlER on 2008-06-06
> **Sef said:**
> Ext3 automatically defrags about every 25 or 30 boots.  

Reiferfs does not ever need to be defragged.

Ext3 checks the disks for errors, it doesn't defrags it. Ext3 doesn't need defraging if the disk has some free space available (at least 10%~20% free).

---

