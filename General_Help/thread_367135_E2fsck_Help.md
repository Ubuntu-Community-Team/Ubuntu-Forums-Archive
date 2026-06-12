---
title: "E2fsck Help"
date: 2007-02-21
forum: General Help
---

### Post by xur17 on 2007-02-21
I was having some trouble with one of my hard drives on my server.  I noticed that when I tried to transfer files to it, it gave me errors.  So, I unmounted it, and was going to run e2fsck, but instead remounted it, and saw this is /var/log/messages:

EXT3-fs warning: mounting fs with errors, running e2fsck is recommended

How do I run e2fsck to fix these errors.  I have been reading through the man page, and am still confused.

What is the difference between this:
-c

    This option causes e2fsck to run the badblocks(8) program to find any blocks which are bad on the filesystem, and then marks them as bad by adding them to the bad block inode. 


and this:

-p

    Automatically repair ("preen") the filesystem without any questions. 

What should I run?

I really appreciate any help you can give.

---

### Post by kpkeerthi on 2007-02-21
I would advice you to run the tool by booting into LiveCD and type e2fsck in terminal and follow the prompts. As for the options,  -c switch marks bad blocks in the harddisk so the OS does not write any data into those trouble areas. Option -p repairs the file system without prompting for your inputs. This is identical to 'Fix errors automatically' option in chkdsk used in Windows.

---

### Post by esaym on 2007-02-21
boot into live cd or unmount the drive.  You can't unmount the drive if it is root or busy.  If it is busy ```
sudo umount -l (lowercase L)
``` might work.  I always find it easier to boot with the live cd and then check all the partitions.

To run the check: ```
sudo e2fsck -f /dev/hda1
```  The -f is to force the check.  If you boot with the live cd you might as well optimize the filesystem some: ```
sudo tune2fs -O dir_index
```

Directory indexing speeds up file location in directories with lots of files in them.  after enabling directory indexing you need to optimize the directories with ```
sudo e2fsck -f -D /dev/hda1
``` Again the -f to force and -D to optimize directory indexing in current directories.

Replace "/dev/hda1" with what ever your partition is (hda1 hda2 hdb3 sda1 sdb2 etc etc) See /etc/fstab for your partition locations. 

*Noticed you can only check partitions and not disks.

Keep us posted with any errors you find.  This sounds interesting...

---

### Post by xur17 on 2007-02-21
Thanks for all your help.  I decided to unmount the drive, and then run e2fsck, and see from there.  It went through, and it kept giving me this error:

Error reading block 13829888 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 6914073.  Ignore error<y>?

I said yes for all of those (a lot of them), and then ran the e2fsck again, this time getting less errors.  I ended up losing a number of files, but this is okay.  I am thinking of maybe just wiping the partition.

---

### Post by esaym on 2007-02-21
> **xur17 said:**
> Thanks for all your help.  I decided to unmount the drive, and then run e2fsck, and see from there.  It went through, and it kept giving me this error:

Error reading block 13829888 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 6914073.  Ignore error<y>?

I said yes for all of those (a lot of them), and then ran the e2fsck again, this time getting less errors.  I ended up losing a number of files, but this is okay.  I am thinking of maybe just wiping the partition.

If you are using ext3 you really shouldn't ever get data loss.  Have you forced your computer off recently or lost power?  You might want to install smartmontools and run: smartctl -a /dev/hda

It will spit out the smart status of your drive.  It might be going bad...

---

