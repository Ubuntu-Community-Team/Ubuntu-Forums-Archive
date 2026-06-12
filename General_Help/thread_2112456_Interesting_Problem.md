---
title: "Interesting Problem"
date: 2013-02-04
forum: General Help
---

### Post by barreyi on 2013-02-04
I am using Ubuntu for my (home theater PC).  I have two hard drives with multiple partitions.  A boot partition, a root partition, and an lvm partition that has 3 separate logical volumes spanning the rest of the space on the two hard drives.  I have media saved on a couple of 500GB external hard drives.  I have been transferring some media over to my HTPC that was on my external hard drives.
At first I was using my laptop and sending the files via SMB share.  For some reason this was causing my HTPC to put the partition where I was loading the media mounted on /mymedia as read-only.  When I restarted the computer the partition would be back to being writable.
I then decided to just take my external hard drive and plug it in manually to transfer files.  This worked fine at first and then the same problem occured.  When I restarted the HTPC this time I only got a cursor.  I am at a loss as to what to do, and I'm hoping to recover things because frankly it would be really annoying to re-build everything from scratch after all that work.  The external hard drive is formatted as NTFS which might possibly be causing some of the problems.  Any help would be appreciated.  Thanks.

---

### Post by takuie on 2013-02-04
Im sure one of the experts could walk you through your problem, but from personal experience I have found nothing but a LOT of hair pulling, wall punching, loud cursing, head banging problems when trying to get any Linux type operating system to work on NTFS w/o problem after problem.  

What I wound up doing was biting the big bullet right in the head and rebuilt everything on a linux formatted HD.

As for your movie drives, these should be ok to leave as NTFS or FAT32, but for the main partition which will be loading ubuntu, i would strongly recommend dropping NTFS.  just my two cents... best of luck to you!

---

### Post by barreyi on 2013-02-05
I think I was not clear enough.  The only NTFS drive is the external hard drive which has media on it that I need to transfer to my HTPC.  My HTPC uses ext2 for boot and ext4 for everything else.

---

### Post by collisionystm on 2013-02-05
Is it the entire partition marked as 'Read only' or the files themselves?

There are settings in your smb.conf that dictate the file permissions for your samba share. 

I think samba is setting the permissions on its own because of the way its configured in smb.conf and when you reboot, your OS is setting the permissions back to standard unix permissions with its settings in fstab. Its been a while since I played with samba.

---

### Post by tgalati4 on 2013-02-05
Open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for disk errors.  When copying and performing large file transfers some disks will barf and throw up errors.  This cause the kernel to set read-only as the file system is now *unclean*. When you reboot, an automatic fsck is performed to mark the partition as *clean.*  

Check your cables and power connections on the machine and watch dmesg for errors.

---

### Post by barreyi on 2013-02-06
> **collisionystm said:**
> Is it the entire partition marked as 'Read only' or the files themselves?

There are settings in your smb.conf that dictate the file permissions for your samba share. 

I think samba is setting the permissions on its own because of the way its configured in smb.conf and when you reboot, your OS is setting the permissions back to standard unix permissions with its settings in fstab. Its been a while since I played with samba.

It was the entire partition that was marked as read-only not just the files themselves.  I don't think it's the samba sharing however because the same thing happened when I tried to use my external hard drive to copy over the media directly.

> **tgalati4 said:**
> Open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for disk errors.  When copying and performing large file transfers some disks will barf and throw up errors.  This cause the kernel to set read-only as the file system is now *unclean*. When you reboot, an automatic fsck is performed to mark the partition as *clean.*  

Check your cables and power connections on the machine and watch dmesg for errors.

I'll try that, and I'm wondering how long fsck might take on a partition that's 800+GB as that's where the errors would be.  That might be why when I boot up it's just giving me a cursor.  I'm probably not waiting long enough for it to check the disk before restarting.  Thanks for your help everybody.  I'll let you know what I find.

---

