---
title: "How do I create an image backup of Windows with dd?"
date: 2015-11-22
forum: General Help
---

### Post by kuverit on 2015-11-22
Hi,

I have a fresh installation of Windows (dual booted with Kubuntu) which I would like to backup. The Windows partition size is about 100 GB. Used space is around 15 GB.

I have never used dd, but I think I read somewhere that it also backs up free space. Is that correct? If so, it means that the backup file would be about 100 GB, wouldn't it?

---

### Post by kuverit on 2015-11-22
On a second thought, would built-in system backup in Windows be a better choice?

---

### Post by sudodus on 2015-11-22
I would recommend ***Clonezilla*** for that kind of backup. It does not copy the unused data blocks, so it is much faster than dd.

(If you overwrite all unused data blocks with zeros, and compressed the dd-image, if will be much smaller, in your case around 15 GB or even less, but the process will still be much slower than Clonezilla).

-o-

The ***built-in system backup in Windows*** might be a better choice. You should also make ***recovery disks*** for Windows (if possible with your version of Windows).

-o-

To be really sure, you should also ***test*** that your backup really works. It means that you remove your internal drive and insert a new one of at least the same size and restore the system into the new drive.

0. A live Clonezilla (CD/DVD/USB) drive or Windows recovery disks
1. The original internal drive
2. The drive with the backup (typically a set of compressed files on an external drive)
3. The new internal drive

---

### Post by kuverit on 2015-11-22
Thanks for the reply Sudodus. Actually, I'm on a laptop so I  can't actually take out my hard drive. Also I don't have an external  hard drive.

I read your reply just now and I've already used the  Windows built in system-backup feature. Also, my Windows isn't an OEM  installed version. So, I don't have recovery disks. I do have the  Windows 10 iso.

I'm backing my stuff up because I'm trying to  achieve this, which is kind of risky:  [http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html](http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html)

---

### Post by sudodus on 2015-11-22
Yes, it is a good idea to back up your data :-)

Where are you storing the backup? On DVDs or at an internet cloud service? I used an external USB/eSATA hard disk drive, which is quite good for me.

In many laptops it is rather easy to take out the hard disk drive, but it can be difficult in some old laptops with an IDE PATA disk (not SATA).

---

### Post by The Cog on 2015-11-22
There is also a utility called fsarchiver which makes backup copies of partitions, ignoring the unused space. I have successfully restored windows partitions from fsarchiver archives in the past.
Not saying it's any better than clonezilla - I've never used clonezilla. It's just another option. Clonezilla can also backup partition table and bootloader, so I get the impression it is intended more for backing up an entire machine whereas fsarchiver is probably more aimed at backing up individual partition contents.

---

