---
title: "[SOLVED] Hard drive errors"
date: 2008-05-16
forum: General Help
---

### Post by meanerelk on 2008-05-16
Any help with this would be greatly appreciated, because I am going crazy trying to figure it out.

When I boot, e2fsck gets run on one of my hard drives, and it goes crazy with errors. The thing is, smartctl reports that the drive is fine. I've also checked the connections, but the SATA cables seem to be secure. So I don't think it is a hardware problem, otherwise I would just get a new drive. As it is, I'm afraid that if I buy a new drive I'll just have the same errors.

I've had this problem with both Gutsy and Hardy. The drive is a WD Caviar 500GB, and my motherboard is a Gigabyte GA-P35-DS3P.

I've tried to reproduce the errors below. I get screens and screens of these types of errors, and e2fsck can't seem to fix anything:

```

[2658.009687] ata2.01: status: {DRDY ERR}
[2658.009687] ata2.01: error: {UNC}
[2658.009687] ata 2.01 exceptionEmask 0x0 SAct 0x0 SErr 0x0 action 0x0
[2658.009687] BMDP Stat 0x45
[2658.009687] cmd c8/00:06:a1:01:28/00:00:00:00:00/f2 tag 0 dma 3072 in

[2658.009687] Buffer I/O error on device sdb1, logical block 18088113.

Error reading blog 451999 (Attempt to read block from filesystem resulted in short read ) while getting next inode from scan. Ignore? <y> Yes

Force rewrite? <y> Yes

```

---

### Post by meanerelk on 2008-05-16
Update: well, e2fsck has been running for over two hours now, with no sign of slowing down. It's still spitting out the same errors, and the hard drive clicks every time it does so. Would it be safe to interrupt it and try to save some of my data, or what? The whole disk must be fubared.

---

### Post by az on 2008-05-16
> **meanerelk said:**
> Update: well, e2fsck has been running for over two hours now, with no sign of slowing down. It's still spitting out the same errors, and the hard drive clicks every time it does so. Would it be safe to interrupt it and try to save some of my data, or what? The whole disk must be fubared.

Yes, stop the fsck right now and image your drive.

Once you have an image of the drive (on another disk of equal or greater size) you can try to recover data from the copy.

Use gnu ddrescue to make an image.  

See
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by meanerelk on 2008-05-17
Thanks, az, I'm downloading Ubuntu Rescue right now. Hopefully I'll be able to save my data with it.

Once that's done, however, how might I go about figuring out what the problem with the drive is? I'd like to figure out whether the drive needs to be replaced, or what. It passes the smartctl report, but fsck can't seem to fix it (or at least it runs for hours). 

I ran:

```

e2fsck -vy /dev/sdb1

```

which generated hours of output like this. 

```

Error reading blog 451999 (Attempt to read block from filesystem resulted in short read ) while getting next inode from scan. Ignore? <y> Yes

Force rewrite? <y> Yes

```

Is this fixing anything, or should I do something else? How can I fix it, or narrow down the problem?

---

### Post by meanerelk on 2008-05-18
So I started imaging the drive with ddrescue last night. I woke up and it is still running, after more than eight hours. Ever couple seconds the hard drive clicks and another error message appears, just like when I was running e2fsck: 

```

[2658.009687] ata2.01: status: {DRDY ERR}
[2658.009687] ata2.01: error: {UNC}
[2658.009687] ata 2.01 exceptionEmask 0x0 SAct 0x0 SErr 0x0 action 0x0
[2658.009687] BMDP Stat 0x45
[2658.009687] cmd c8/00:06:a1:01:28/00:00:00:00:00/f2 tag 0 dma 3072 in

```

I've googled around, but I can't really figure out what it means. Could anyone enlighten me?

---

### Post by meanerelk on 2008-05-18
Update: I've stopped and started the process several times, and I've realized that the imaging process always starts producing those errors at the exact same spot, 18,755 mb into the disk.

Is there any way to figure out what it could be? A physical problem with the disk, a problem with the filesystem, or what?

---

### Post by az on 2008-05-19
> **meanerelk said:**
> Update: I've stopped and started the process several times, and I've realized that the imaging process always starts producing those errors at the exact same spot, 18,755 mb into the disk.

Is there any way to figure out what it could be? A physical problem with the disk, a problem with the filesystem, or what?

Keep letting it go.  It may get a good read and you may get all your data back.

You have a damaged hard disk.  You will not be able to fix it.  You may be able to avoid the bad area(s) but I would not consider using that disk any more.  It is not reliable.

---

### Post by meanerelk on 2008-05-19
az, I finally managed to recover my data. Thanks again for your help.

You were right, the disk is bad. After running the long SMART diagnostic, it failed, and it also failed the manufacturer's diagnostic. I will RMA it.

---

