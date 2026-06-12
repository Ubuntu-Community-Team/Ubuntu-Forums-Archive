---
title: "HEL PLEASE. Can't mount some very important partitions after upgrade!"
date: 2013-01-10
forum: General Help
---

### Post by hortstu on 2013-01-10
One of these partitions is only a data partition but I've been using it since hardy heron and it has some pictures of my baby girl that I don't have stored any where else.  I'm starting to panic.

The other partition that won't mount is the last LTS OS. This all went wrong when I tried to upgrade to the new LTS version via the update manager.

I hesitated for a long time.  I don't know what came over me today.  I should have just cleared an old partition and installed it there.  I'm really sick about this. 

I've googled every error that I've run into but keep getting new problems and I'm not sure of the order to tackle them or which googled advice I should take.  Is there anyone awake out there that can help me with this?

TIA

---

### Post by efflandt on 2013-01-11
Which versions are you discussing?  The current LTS version is 12.04 (which is not really new, 12.10 is not an LTS version).  The previous LTS version was 11.04, but under your name you still have 10.04 listed.

Does **sudo fdisk -l** still show the partitions you are looking for?  What specific errors did you get, or does /var/log/syslog show errors for partitions or drives?  Did you try **sudo e2fsck -p** on those partitions?

---

### Post by hortstu on 2013-01-11
Thanks for the effort.

> **efflandt said:**
> Which versions are you discussing?  The current LTS version is 12.04 (which is not really new, 12.10 is not an LTS version).  The previous LTS version was 11.04, but under your name you still have 10.04 listed.

Yeah you're right I was still using 10.04 and tried to upgrade to 12.04 via the update manager.

first error I run into is at boot and it just says 

"The disk drive for / is not ready yet or not present.
Continue or wait; or Press S to skip mounting or M for manual recovery"

I had that for over an hour then decided there was a problem.

Selected M and tried a few things I found in the forums but I worry that I'm doing more damage than good.

> Does **sudo fdisk -l** still show the partitions you are looking for? 

yes

What do I enter to get the info on var/log/syslog you're asking about?

> Did you try **sudo e2fsck -p** on those partitions?

I'm trying that now.  Data partition says clean.

---

### Post by hortstu on 2013-01-11
sda1 or boot partition says

```
e2fsck: attempt to read block from file system resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

---

### Post by hortstu on 2013-01-11
When I was messing around before I got an error with dpkg

> dpkg: error: parsing file 'var/lib/dpkg/status' near line..... blank line in value of field 'Description.'

---

### Post by hortstu on 2013-01-11
Also just booted up to 8.4, I can access data partition from here.

On boot to this partiton I got this message before a choice to boot or go to a maintenance shell for manual repair.

> fsck.ext3: unable to resolve 'UUID=##########.........
fsck died with exit status 8

file system check failed

I took a picture of the UUID number in case I need it, I just didn't feel like typing it.

---

### Post by hortstu on 2013-01-11
forgive me I have to type this. This is new information that I hope gets me some help with this problem.

proc /proc proc nodev,noexec,nosid 0 0
/ was on /dev/sda7 during installation

UUID=971bf3d6-7d10-47c1-9d33-7824c1a295f6 / ext 3 errors=remount-ro 0 1
swap was on /dev/sda9 during installation

UUID=547b1a08-a4e0-416c-89a7-17948565bf87 none swap sw 0 0
sudo blkid

/dev/sda5: LABEL="hardy heron" UUID=".........." SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="hardy home" UUID="........." SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="971bf3d6-7d10-47c1-9d33-7824c1a295f6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="lucid home?" UUID=".........." SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="547b1a08-a4e0-416c-89a7-17948565bf87" TYPE="swap" 
/dev/sda10: UUID=".............................." SEC_TYPE="ext2" TYPE="ext3"

I didn't bother to type all the UUIDs. I took a picture so I have them if needed, but it seems like the two mentioned in cat /etc/fstab match up.

---

### Post by weryl on 2013-01-11
Before trying anything else I'd recommend using a LiveCD (latest ubuntu would do) to boot a live session, mount your data partition, and backup it entirely to an external hard drive / dvd / other computer / etc. If the disks aren't damaged it should be fairly easy to do.

While you're at it, you might want to make a list of your installed applications so that it's easier to do a fresh install should you want to.

After you're sure that you've backup ALL of your important data, I'd consider reinstalling 12.04 LTS entirely. Otherwise sorry I'm not experience enough to guide you through the steps of troubleshooting/fixing the actual problem, someone else here should be.

Is this a desktop PC or a server?

---

### Post by hortstu on 2013-01-11
Thanks weryl,

This is a laptop pc.  I have a live cd of 10.04.  I'll pickup an external today and do the backup.

This drive is poorly organized anyway so a fresh install might be the way to go.

My concern is that I have some data on my lucid partition and I don't think I can access that.  I'll try with the live cd.

---

### Post by oldos2er on 2013-01-11
Take a look at [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by hortstu on 2013-01-12
> **oldos2er said:**
> Take a look at [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

WOW.  Not only is that cool but it is open source.  Thanks.

---

### Post by -kg- on 2013-01-12
As an aside (and since no one else caught it):

> **efflandt said:**
> Which versions are you discussing?  The current LTS version is 12.04 (which is not really new, 12.10 is not an LTS version).  The previous LTS version was 11.04, but under your name you still have 10.04 listed.

No, 11.04 was not an LTS release.  LTS versions are released every two years.  The last LTS version was 10.04.  That being said...

Yes, you should be able to recover your files, as long as no damage was done to the data partition.  Photorec will do it, as well as a LiveCD, if you know what you're looking for.  All that's required is an external (or internal) drive of sufficient size to store what you want to save.  You shouldn't need it, though, as long as you don't format the partition which contains your photos and other files.

As another aside: I've never had any luck with an upgrade...I always install fresh and add my important files later.  That's just me, though.

---

### Post by weryl on 2013-01-12
> **-kg- said:**
> As another aside: I've never had any luck with an upgrade...I always install fresh and add my important files later.  That's just me, though.

Neither did I. Too many problems each time, reinstalling is much easier and much faster as well (the DVD torrent downloads much faster than the packages when upgrading). But, for a server, reinstalling does take quite some time and additional planning is required (that's why I asked).

---

