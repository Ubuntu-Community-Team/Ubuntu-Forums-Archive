---
title: "Ubuntu doesn't recognize internal hard drive after update to 24.10"
date: 2024-10-11
forum: General Help
---

### Post by euphgeek on 2024-10-11
I have a 1 TB internal hard drive that has had no problems at all until I upgraded to 24.10.  When I rebooted after upgrading, it didn't recognize it at all.  I rebooted a few more times, but this was the best I could do:

```
$ cat /etc/fstab | grep cifs
/dev/disk/by-uuid/aeac7129-c4b6-47da-8dca-7b5d7a6f130a /cifs ext4 defaults 0 1

$ df -h | grep cifs
/dev/sda1       917G  726G  145G  84% /cifs

$ mount | grep cifs
/dev/sda1 on /cifs type ext4 (ro,relatime)

$ ls -l /cifs
ls: /cifs/: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
ls:  cannot access <filename>: Input/output error
total 40
-?????????  ? ?    ?          ?            ? <filename>
drwx------  2 root root   16384 Nov 26  2009 <filename>
drwxrwxrwx 43 user colord  4096 Aug 18 18:18 <filename>
-rw-r--r--  1 user user   10986 Nov  7  2009 <filename>
-?????????  ? ?    ?          ?            ? <filename>
-rw-r--r--  1 user user    7184 Sep 11  2008 <filename>
d?????????  ? ?    ?          ?            ? <filename>
d?????????  ? ?    ?          ?            ? <filename>

```

"colord" is not a valid user in my system, that I know of, and I don't believe I've been hacked.

Have there been any bug reports on things like this happening?  If so, is there a fix coming out?  If it's just me, any ideas on what I can do to fix this?

---

### Post by grahammechanical on 2024-10-12
Why did you run this command

> cat /etc/fstab | grep cifs

> What is CIFS in Linux?Common Internet File System (CIFS), **an  implementation of the Server Message Block (SMB) protocol, is used to  share file systems, printers, or serial ports over a network**. Notably, CIFS allows sharing files between Linux and Windows platforms regardless of version.




What do you have on that 1TB drive? Is this a Ubuntu server install?

Regards

---

### Post by euphgeek on 2024-10-12
It's not a server install.  I just named it /cifs because I had thought about using it as a shared drive but I decided against it.  I ran the command so that it would show the 1 TB drive's entry in /etc/fstab.  I feel like we're focusing on the wrong thing here, though.  This drive was functioning as a normal internal hard drive before the upgrade and now it's unreadable.

---

### Post by ian-weisser on 2024-10-12
Input/Output error usually means a hardware fail by the storage device.

Look up how to run a SMART test on your storage hardware.

---

### Post by euphgeek on 2024-10-12
Hmm.  Makes sense.  I bought it new in 2008, so it's possible it could be on its way out.  I do have GRC's SpinRite, so hopefully running that on my hard drive will help.

---

### Post by dragonfly41 on 2024-10-12
If you revert to older LiveUSB Ubuntu 22.04 can you view the drive?

---

### Post by yancek on 2024-10-12
Is the drive recognized in the BIOS?  What happened when you ran a filesystem check on it with fsck?

---

### Post by euphgeek on 2024-10-12
> **dragonfly41 said:**
> If you revert to older LiveUSB Ubuntu 22.04 can you view the drive?

Ah, good idea!  I tried a LiveUSB Ubuntu 24.04 and I was able to read the disk, no problem.

> **yancek said:**
> Is the drive recognized in the BIOS?  What happened when you ran a filesystem check on it with fsck?

BIOS definitely recognizes it.  Here's the output from fsck:

```
$ sudo fsck /dev/sda1
fsck from util-linux 2.40.2
e2fsck 1.47.1 (20-May-2024)
fsck.ext4: Input/output error while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

---

### Post by yancek on 2024-10-13
Did you get the same results when you ran the alternate commands suggested in the fsck output you posted?
Seems odd it would mount and be accessible in an older version of Ubuntu and not the latest.  Have you tried commenting out the entry in fstab for that partition and mounting it manually?

---

### Post by euphgeek on 2024-10-13
I wasn't sure what that would do, and I didn't want to make any changes without understanding of how to undo them.  Especially since it works just fine in 24.04.

---

### Post by dragonfly41 on 2024-10-13
Another idea is to install rEFInd as parallel boot option to see if that loads your drive.
rEFInd can be installed without impacting on your usual grub. But after installing rEFInd you need to go into BIOS to choose rEFInd loader as your first boot option. Then we can see if rEFInd finds the drive without issue in 24.10
.

---

### Post by euphgeek on 2024-10-13
I tried installing rEFInd and rebooted into my BIOS, but I didn't see anything other than the usual UEFI disk, UEFI USB drive, UEFI network, etc.  And I didn't see any new boot options, either.  Maybe I'm just not familiar enough with rEFInd to be able to use it properly.

---

### Post by yancek on 2024-10-13
>  I wasn't sure what that would do, and I didn't want to make any changes  without understanding of how to undo them.  Especially since it works  just fine in 24.04. 				

Running the different fsck options suggested will either repair the system or not, giving you the same error.  Unmounting and remounting manually also should not create any problem.  It will either work or not, if not probably the same error.

---

### Post by euphgeek on 2024-10-14
What I mean is, does it permanently change the superblock, and if so, how do I find out what it's using as the current superblock so I can change it back?

---

### Post by yancek on 2024-10-14
You indicate that the drive functions properly when you use 24.04 so the suggested solution would be to stick with 24.04 which is an LTS release and will have support for years after support for 24.10 ends.  If you don't have a valid requirement/reason to upgrade, don't do it and certainly NOT from an LTS to a short term release.

If you don't understand the superblock information, you could read the page at the link below to see if it helps.  If not, don't change anything if it works on 24.04.  fsck and similar software does not 'repair' hardware, it is not possible for software to 'repair' physical hardware.  It just marks bad blocks so they are not used.  If you don't understand something, don't do it.

[https://askubuntu.com/questions/1033923/how-to-find-superblock](https://askubuntu.com/questions/1033923/how-to-find-superblock)

>  "colord" is not a valid user in my system, that I know of

The above comment is from your initial post.  It's wrong.  Look at the files /etc/passwd and /etc/group and you will see colord in both.  There are many system users not just the users/groups you create.

Manually mounting or trying to mount that partitions filesystem after commenting out the /etc/fstab entry was suggested to see if there would be any warning/error messages.

---

### Post by euphgeek on 2024-10-14
> **yancek said:**
> You indicate that the drive functions properly when you use 24.04 so the suggested solution would be to stick with 24.04 which is an LTS release and will have support for years after support for 24.10 ends.  If you don't have a valid requirement/reason to upgrade, don't do it and certainly NOT from an LTS to a short term release.
I've always updated to the most recent release and I've never had problems this bad before.  But it shouldn't be too hard to format my / partition and reinstall 24.04, since /home is on a separate partition.  I just thought I could figure out a solution to this problem or at least help the community by reporting it.

> If you don't understand the superblock information, you could read the page at the link below to see if it helps.  If not, don't change anything if it works on 24.04.  fsck and similar software does not 'repair' hardware, it is not possible for software to 'repair' physical hardware.  It just marks bad blocks so they are not used.  If you don't understand something, don't do it.

[https://askubuntu.com/questions/1033923/how-to-find-superblock](https://askubuntu.com/questions/1033923/how-to-find-superblock)

OK, I read the page, followed the suggestion and then ran the commands.  Here are the results:
```
$ sudo e2fsck -b 8193 /dev/sda1
e2fsck 1.47.1 (20-May-2024)
e2fsck: No such file or directory while trying to open /dev/sda1
Possibly non-existent device?

$ sudo e2fsck -b 32768 /dev/sda1
e2fsck 1.47.1 (20-May-2024)
e2fsck: No such file or directory while trying to open /dev/sda1
Possibly non-existent device?

```

> The above comment is from your initial post.  It's wrong.  Look at the files /etc/passwd and /etc/group and you will see colord in both.  There are many system users not just the users/groups you create.
Fair.  I figured it may have been something like that.

> Manually mounting or trying to mount that partitions filesystem after commenting out the /etc/fstab entry was suggested to see if there would be any warning/error messages.
I think the drive has completely disappeared now.  I'm getting the following:
```
$ sudo mount -t ext4 /dev/sda1 /cifs
mount: /cifs: special device /dev/sda1 does not exist.
       dmesg(1) may have more information after failed mount system call.
```

---

### Post by yancek on 2024-10-14
The results of the mount and fsck commands indicate the drive may be bad.  Check connections to the drive.  If it still works with 24.04 that would be confusing.

>    But it shouldn't be too hard to format my / partition and reinstall 24.04,  

Just make sure you do NOT format the /home partition if you install 24.04.

---

### Post by euphgeek on 2024-11-02
OK, it's been a couple weeks and I was finally able to get back to this.  I was able to successfully reinstall 24.04 and my /cifs terabyte hard drive is fully recognized again and I can access all the files on it with no trouble.  It also cleared up some issues that popped up whenever I rebooted the system, making me sometimes have to press the reset button several times just to get back in.  So I think the lesson here is that if you value your data and a stable system, never upgrade to 24.10.

---

