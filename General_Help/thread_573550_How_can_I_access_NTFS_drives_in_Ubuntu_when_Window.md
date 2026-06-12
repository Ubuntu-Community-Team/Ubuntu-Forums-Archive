---
title: "How can I access NTFS drives in Ubuntu when Windows has Crashed?"
date: 2007-10-11
forum: General Help
---

### Post by OzzyFrank on 2007-10-11
OK, I've noticed something that is basically making a liar out of me, considering I've been going around telling people if their Windows is dead but the drive is OK, they can use Ubuntu (even just the Live CD) to reclaim files and back them up to another drive.

However, when Windows has crashed or frozen and I've been forced to hit the reboot button, I can't access that drive in Ubuntu. Worse yet, I can't even access other NTFS partitions, like the one that is on the same drive as Ubuntu and shouldn't in my mind have anything to do with the Windows crash... but it does. So I'd like to know first off if anyone knows why other NTFS partitions are affected, and secondly how to remedy this.

I mean, I thought it was bad enough the first time I noticed this, and that was after a Windows crash that did indeed need a Scandisk after boot. Now it just happens every time I've been forced to reboot after a Windows crash, even though it is generally not so severe a Scandisk is needed. If I reboot into Windows then restart properly, all is fine with all my NTFS partitions in Ubuntu, but obviously this raises the question whether Ubuntu (installed or Live) can be used to backup stuff on NTFS drives when Windows will no longer boot (and we've all had that before). Any ideas?

---

### Post by Belinrahs on 2007-10-11
hmmm.....you say Scandisk was ran? No Windows OS that had NTFS also had scandisk. That's just a bit confusing. What OS is on the hard drive?

---

### Post by cmnorton on 2007-10-11
This is a quick guess. You might try recovering Windows using the recovery disk or recovery console (if you can boot that far). You might also be able to recover using the installation media and run recovery console from there. Don't do this without some documentation in front of you.

---

### Post by Officer Dibble on 2007-10-11
If you are experiencing these crashes often, then it is time to change your hard drive my friend. You would need something more than just another OS if the drive isn't being read properly - and that is sadly the problem on many aged drives.

My suggestion would be to grab what data you can, taking into account the sensitivity of the drive, or if it is stable enough to make an image of, do that and then do your salvaging from a stable drive.

---

### Post by OzzyFrank on 2007-10-11
First off.... OK, so I got the name wrong. For years it was Scandisk, so I still call it that. Whatever you call it, it does the same job. So OK, Checkdisk or Chkdsk or Czech-disk... whatever. I use XP.

Secondly, **my drive is OK**, i just have to run certain programs that sometime freeze Windows. I think all of us have had that at one stage, hence the move to Windows.

I STRESS here that being **unable to access ANY NTFS drive in Ubuntu** happens after a crash that DOES NOT need any Windows repair like [Whatever]disk - just a reboot and all is fine. Also keep in mind my question was how to access these files from said NTFS drive (and others) when Windows has actually died and is beyond repair - this is for rescuing files. So in a nutshell I am asking how can someone whose Windows has died beyond all repair rescue their files from that drive when even a simple freeze from a working Windows on a working drive prevents this? (And also prevents one from accessing other NTFS partitions in the system?).

Now, I'm happy to answer all your questions, but can someone actually answer mine. Hate to appear selfish, but that's why I started this thread. Cheers.

---

### Post by taurus on 2007-10-11
Assuming your Windows is on /dev/sda1, try

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
sudo ls -la /media/sda1
```
Or use nautilus with root permission so you can access /media/sda1.

```
gksudo nautilus
```

---

