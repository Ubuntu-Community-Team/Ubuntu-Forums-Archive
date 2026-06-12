---
title: "Enlarge my Ubuntu partition on Dual-Boot MacBook 5.1"
date: 2012-12-01
forum: General Help
---

### Post by Waudby on 2012-12-01
Hi everyone,

I took the leap a few weeks ago and installed Ubuntu 12.04 LTS on my 2009 MacBook 5.1. Since then it's worked wonderfully and has pretty much become my primary operating system. I installed it on a 30 GB partition of my 160 GB hard drive initially, but now I'm thinking I want to make the Ubuntu partition larger (maybe ~80-100 GB). I was wondering if there was a way to do this without having to erase and reinstall Ubuntu? 

I use rEFIt to dual-boot my laptop, with the Linux partition set to default. I think there ought to be a way to use gparted to resize the partitions, but I'm not entirely computer savvy enough to figure it out (at least not without stressing I'll cause a problem while doing it).

Any help is appreciated.

Cheers

---

### Post by sudodus on 2012-12-01
Welcome to the Ubuntu Forums, Waudby,

Yes you can use gparted to do it.

It is risky to edit partitions, so I recommend that you make a complete backup of the drive to an external drive, or at least save all your personal files (documents, pictures, videos etc).

Another option is to continue to run Ubuntu on the 30 GB partition (it is enough for the system and some temporary files. You can use the free space as a separate partition for data (and select a file system, that can be read by both operating systems).

---

### Post by Waudby on 2012-12-01
Thanks sudodus. I'm glad to be here.

I'm definitely pro-backup. 

So basically, I could just use disk utility to shrink the Mac OS X partition down a bit, then use gparted to format the new blank space/place holder partition to be accessible to both operating systems? Which formatting system should I use for this? If I remember correctly, OS X is HFS+, and Ubuntu is EXT4, and they don't communicate with each other. 

Is this similar to the 1 GB Linux SWAP partition that the installation outline I followed had me create, and whose purpose I don't know? (Forgive my ignorance, please.:() 

Right now, I have a 210 MB EFI partition, a 125 GB HFS+ partition, 1 GB SWAP partition, and then the 31 GB EXT4 partition (labelled /sda1, 2, etc., in that order). I would have to shrink the Mac partition in OS X, I think? I'd then create an /sda5 partition in a mutually-readable file system, using gparted? Would I have to boot from my Ubuntu CD to make these changes?

Thanks again.

---

### Post by Bucky Ball on 2012-12-01
You need to use Gparted while running from the LiveCD as partitions need to be unmounted. You can't unmount the Ubuntu partition, obviously, as you are running from it. 

Better is to just create a data partition with the extra space and use that. You can copy all personal data directories from your current home (which is a directory in the / partition) to the data partition, delete them from /home directory then create symlinks there instead. It is easy to create them.

All installs can then use this data partition by creating symlinks to it (for instance, you may want to install another flavour of *buntu or another distro and this saves you needing to create extra /home partitions for each). The added bonus of this is if something goes pear-shaped with the Ubuntu install and you need to reinstall (last resort) your data is on a separate partition to the operating system so should be a breeze. 

The smaller size you already have for / and the OS is good as is. I never use anything over 15Gb for the / partition myself ...

---

### Post by sudodus on 2012-12-01
> **Waudby said:**
> Thanks sudodus. I'm glad to be here.

I'm definitely pro-backup. 

So basically, I could just use disk utility to shrink the Mac OS X partition down a bit, then use gparted to format the new blank space/place holder partition to be accessible to both operating systems? Which formatting system should I use for this? If I remember correctly, OS X is HFS+, and Ubuntu is EXT4, and they don't communicate with each other. 

Is this similar to the 1 GB Linux SWAP partition that the installation outline I followed had me create, and whose purpose I don't know? (Forgive my ignorance, please.:() 

Right now, I have a 210 MB EFI partition, a 125 GB HFS+ partition, 1 GB SWAP partition, and then the 31 GB EXT4 partition (labelled /sda1, 2, etc., in that order). I would have to shrink the Mac partition in OS X, I think? I'd then create an /sda5 partition in a mutually-readable file system, using gparted? Would I have to boot from my Ubuntu CD to make these changes?

Thanks again.

Well ... I suggest that you browse the internet for information about what file systems can be read and written by OS X. Linux can read and write FAT32, NTFS and several linux file systems. Probably it can read but not write HFS+ but I am not sure about that. See this text from ```
man mount
```

>        -t, --types vfstype
              The argument following the -t is used to indicate the filesystem type.   The  filesystem
              types  which  are currently supported include: adfs, affs, autofs, cifs, coda, coherent,
              cramfs, debugfs, devpts, efs, ext, ext2, ext3, ext4, [COLOR="Red"]hfs, hfsplus[/COLOR], hpfs,  iso9660,  jfs,
              minix,  msdos,  ncpfs,  nfs,  nfs4,  ntfs, proc, qnx4, ramfs, reiserfs, romfs, squashfs,
              smbfs, sysv, tmpfs, ubifs, udf, ufs, umsdos, usbfs, vfat, xenix, xfs, xiafs.  Note  that
              coherent,  sysv  and xenix are equivalent and that xenix and coherent will be removed at
              some point in the future &#8212; use sysv instead. Since kernel version 2.1.21 the  types  ext
              and  xiafs  do  not exist anymore. Earlier, usbfs was known as usbdevfs.  Note, the real
              list of all supported filesystems depends on your kernel.

              The programs mount and umount support filesystem subtypes.  The subtype  is  defined  by
              '.subtype'  suffix.  For example  'fuse.sshfs'. It's recommended to use subtype notation
              rather than add any prefix to the  mount  source  (for  example  'sshfs#example.com'  is
              depreacated).

              For  most  types all the mount program has to do is issue a simple mount(2) system call,
              and no detailed knowledge of the filesystem type is required.

The swap partition is virtual memory, disk space where content from the RAM can be dumped, if more memory is needed, than what is available as RAM.

You have four partitions. If you have an extended partition all is fine. Otherwise I suggest that you delete the swap partition and make an extended partition, and inside that you make a new swap partition of the same size (1 GB) or adjusted according to your RAM and if you intend to hibernate Ubuntu or not. You need to check the UUID of the new swap partition
```
sudo blkid
```
and edit the corresponding line in the file /etc/fstab to match it. Otherwise Ubuntu will not find it.

And after you made the swap partition you use the rest of the free space for the data partition and format it so that both systems can read and write to it.

---

### Post by Waudby on 2012-12-01
So after browsing the internet and doing a little research (mostly education, since this is all pretty much new to me), I think I've come up with a course of action.

From what I've read, people have had success using a non-journaled HFS+ partition with Ubuntu for read/write, which is also read/write with Mac OS. So I think that will be the file system I try on my data partition. 

sudodus, I don't currently have an extended partition on my hard drive. So I imagine what I will do is: 
1) Shrink my Mac partition to as small a size as it requires (maybe purging some duplicate files I have migrated over to my Ubuntu partition to maximise free space)

2) From the LiveCD, use gparted to delete my existing SWAP partition, create an extended partition with the remaining disk space (not used by EFI, Mac or Linux), and create my SWAP partition within the extended partition. Update fstab accordingly.

3) Create a non-journaled HFS+ partition in the remaining space (within the extended partition, yes?) that will function as my data partition. 

4) Set up symlinks as Bucky Ball suggests to the data partition so I can access files from the / partition. I gather that if I set up symlinks from OS X to the data partition, I will be able to access the files from there as well?

I have read that there are 'hard' links and 'soft' links, and that since my data partition is unmounted (as I understand it), I will have to use 'soft' links? This part I am a little uncertain on. 

Again, this is all stuff I've learned in the last six hours (more fun than studying), so if I've written something that is totally wrong, or have gotten muddled, don't hesitate to correct me. I won't cry. (Too much...)

---

### Post by sudodus on 2012-12-02
Yes, it looks good to me.

> **Waudby said:**
> 

3) Create a non-journaled HFS+ partition in the remaining space (within the extended partition, yes?) that will function as my data partition.

Yes
> 

4) Set up symlinks as Bucky Ball suggests to the data partition so I can access files from the / partition. I gather that if I set up symlinks from OS X to the data partition, I will be able to access the files from there as well?

Yes. You can access the files without symlinks, but these are shortcuts for quick access.
> 
I have read that there are 'hard' links and 'soft' links, and that since my data partition is unmounted (as I understand it), I will have to use 'soft' links? This part I am a little uncertain on.

Hard links mean that two addresses point to the same position on the storage area. Soft links are pointers to files and folders similar to shortcuts in Windows. Hard links are only for files within the same partition. Soft links work for directories and across partitions (file systems) as well. But you need to mount the partition for the link to work.

And you can choose to mount the data partition automatically with a line in /etc/fstab or you can mount it manually whenever you need it. Usually it is quite convenient to mount partitions with the file browser: just click on its icon.

If you put a descriptive label on your partitions, for example ubuntu, osx, data, it will be easier to recognize them. Use gparted to add labels (it should be a safe operation).

---

### Post by Waudby on 2012-12-02
Thanks for clearing things up, re., mounting partitions and symlinks. I think I've got a pretty decent handle on things now. Since I anticipate using the information in the data partition frequently, I think I'll just edit fstab and have it mount automatically. Adding labels seems like a good idea.

I did some initial tidying up today, cleaning my hard drive. Once that's finished, I'll proceed with shrinking the Mac partition and go from there. It may have to wait a few days though as exams come up, so I'll report back once it's all done, or comment on any problems that crop up.

Thanks again all.

---

### Post by ivotkl on 2012-12-02
I agree with sudodus, go ahead and backup everything.
 
OS partition should be 10-15 GiB. Swap partition should equal 50% of your RAM if possible (some of us people use only 25% or 1GiB - what suits best). It is used, for instance, when you suspend/hibernate computer as a "storage" place of applications currently opened so that they are restored when you boot up the OS again or come back from suspension. I believe it works somehow like Windows' virtual memory.

---

### Post by Bucky Ball on 2012-12-02
> **Waudby said:**
>  I think I'll just edit fstab and have it mount automatically. Adding labels seems like a good idea.

Mac should mount the data partition automatically anyway and you will be able to see the partition in the file manager in Ubuntu and it should mount when you click it automagically (partitions will/should be recognised and included automagically when you install). You shouldn't need to do anything to fstab but if so, do some research first but if you can't nut it out, post a new thread.

> **Waudby said:**
> It may have to wait a few days though as exams come up, so I'll report back once it's all done, or comment on any problems that crop up.

*Wait til after your exams* is my advice for sure. ;)

Again, any problems not related to the title of this one, please post a new thread. You will increase your chances of help with a descriptive title and as much info as you can muster. 

Good luck with the exams and see you when you resurface.

---

