---
title: "xp and gutsy cant read each other in fat32"
date: 2008-02-13
forum: General Help
---

### Post by mangoes on 2008-02-13
Hi all, 

My computer have gutsy64(ext3) and xp dual boot.  I have xp as guest os through vmware.
Both XP and Gutsy can write into the fat32 partition, but XP cant see what I put through gutsy, and vice versa.
 I mounted the windows and fat32 partitions following 
[psychocats]("http://www.psychocats.net/ubuntu") tutorial.
These are my partitions from fstab.
============================================
proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=4b879be9-912e-4fe2-95ab-31db13c24791 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c1120bff-c6ab-40b0-8402-a92e5dc47652 /home ext3 defaults 0 2
/dev/sda1 /windows ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda6 /fat_files vfat iocharset=utf8,umask=000 0 0
# Entry for /dev/sda7 :
UUID=544d6867-85d9-4898-b016-81286a358a25 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
====================================

Thanks in advance!

---

### Post by mbeierl on 2008-02-13
Sorry, but I really need to clarify something:

are you trying to mount the same partition at the same time in both Linux and Windows?  That will result in filesystem corruption and you need to unmount it from the vm guest asap.

Rationale: disk access is very slow (compared to, say, ram) and so file systems are one of the most tuned things in an OS, being designed to avoid actually using the disk as much as possible.  While this might seem odd, it actually makes sense: it keeps a copy of what the disk looks like in memory (this is known as the file system cache.)  Only when necessary does it write the actual data to disk, and it does this without worrying about some other operating system messing with the disk, because it "knows" it's the only OS using that file system.

So, when your Linux OS updates it's version of the file system on the partition, Windows does not know about it and continues to show you it's (now out of date) version of the file system.  When Windows goes to write, it can potentially overwrite part of what Linux wrote, and ... corruption occurs.

Partitions do not make good networked file systems.  What you are actually looking for is to share the files via networking.  This is done through the use of VMWare's shared folders.  You can even map it as a drive letter under Windows, making it appear like it's own drive.

Hope this helps!

---

### Post by mangoes on 2008-02-13
> **mbeierl said:**
> Sorry, but I really need to clarify something:

are you trying to mount the same partition at the same time in both Linux and Windows?  That will result in filesystem corruption and you need to unmount it from the vm guest asap.

Rationale: disk access is very slow (compared to, say, ram) and so file systems are one of the most tuned things in an OS, being designed to avoid actually using the disk as much as possible.  While this might seem odd, it actually makes sense: it keeps a copy of what the disk looks like in memory (this is known as the file system cache.)  Only when necessary does it write the actual data to disk, and it does this without worrying about some other operating system messing with the disk, because it "knows" it's the only OS using that file system.

So, when your Linux OS updates it's version of the file system on the partition, Windows does not know about it and continues to show you it's (now out of date) version of the file system.  When Windows goes to write, it can potentially overwrite part of what Linux wrote, and ... corruption occurs.

Partitions do not make good networked file systems.  What you are actually looking for is to share the files via networking.  This is done through the use of VMWare's shared folders.  You can even map it as a drive letter under Windows, making it appear like it's own drive.

Hope this helps!

Thanks for the tip mbeierl, I learn something new about files system. I'll look more into vmware shared folders.

I know that I'm trying to access the fat32 partition at the same time in both windows and linux. Not sure what about mounting at the same time, but I guess yes. I mounted the fat32 partition in linux as in the fstab file above. Windows  see the fat32 partition automatially.

But if I have separate partition for root(ext3) and /home(ext3) and windows and fat32, (as in my case) wouldnt my linux os be safe since windows can't access the root and /home partition?

---

### Post by mbeierl on 2008-02-13
Sorry, yes if the file system is visible to an operating system, it is called mounted.  So, you are safe for all your other partitions, but the fat32 one that is being accessed by both Windows and Linux at the same time is subject to corruption.

Raw file systems (fat32, ntfs, ext3, etc) are not meant to be shared.  The only safe way of sharing a file system between two (or more) systems is to use a networked file system such as Windows' SMB, CIFS, NFS, AFS, Plan 9, or VMWare's shared folder.

Lmk if you need any help with setting up a shared folder for your FAT32 /dev/sda6 partition.

Oh, and I should ask: you're not doing the same thing with /dev/sda1 (the ntfs partition), are you?  Same warnings apply there :)

---

### Post by mangoes on 2008-02-14
(blush) yes I've bee trying to put some data from ext3 to ntfs partition while windows is running as guest. No wonder why some files were missing. What a drongo.

I've also used fs-driver to make windows see the ext3 partitions. From what you've written, is this also potentially dangerous?

If you don't mind can you steer me in the right direction to set up a shared folder in vmware?

Ta mbeierl!

---

### Post by mbeierl on 2008-02-15
Yes, sorry for the delay.  Shared folders are quite simple, but they require that you install the vmware tools in the guest os.  Once the tools are installed, a special type of network file system is loaded into the guest that allows safe, simultaneous, access.  

The following instructions are specifically for vmware workstation 6, but should be applicable to other versions of vmware:

Open the virtual machine in vmware.  Go to VM -> Settings.  Select the Options tab.  Third option from the top is Shared Folders: select that.  Change the folder sharing to Always Enabled.  You can add a new folder with the add button.

Name: this is the "directory name" that shows up in the guest.
Host Path: this is the location of the actual file system to share in the host.

For example:  I have FAT32 partition that I want to share.  In my Ubuntu host I have an /etc/fstab entry that says:
```

/dev/sda2 /media/fat32 vfat defaults 0 0

```
So, I add a shared folder with a Name of "Data" and a Host Path of "/media/fat32" because that's where Ubuntu has mounted the FAT32 partition.

Now, when I power on my Windows XP guest, I can explore "Entire Network" and see "VMWare Shared Folders".  Under that I see a special computer called ".host".  Under that computer I then see a folder called "Data" - the files there are the real files from my FAT32 partition.

I can now map a network drive (say E:\) to \\.host\data and then my E: drive is the FAT32 partition.  Only, it's really Ubuntu that's managing the files, so expect some performance improvements :)

The same can be done in a Linux guest; it shows up under /mnt/hgfs.  In my example, I can go to /mnt/hgfs/Data.  hgfs, btw, stands for Host/Guest file system.  Or something like that :)

---

### Post by mangoes on 2008-02-18
Sorry for the delay here too. Just changed psu.

Thanks for this mbeierl!  I'll follow your instruction and let you know.:)

---

