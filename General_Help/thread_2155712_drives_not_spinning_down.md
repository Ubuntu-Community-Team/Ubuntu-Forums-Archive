---
title: "drives not spinning down"
date: 2013-06-19
forum: General Help
---

### Post by SlugSlug on 2013-06-19
hi

I have the following in /etc/hdparm.conf:

```
/dev/sdb {
spindown_time = 121
}
/dev/sdc {
spindown_time = 121
}
/dev/sdd {
spindown_time = 121
}
/dev/sde {
spindown_time = 121
}
/dev/sdf {
spindown_time = 121
}
/dev/sdg {
spindown_time = 121
}
/dev/sdh {
spindown_time = 121
}
/dev/sdi {
spindown_time = 121
}
```


non of my drives are spinning down, if I issue a 
sudo hdparm -y /dev/sdh


then they do spin down.

4 drives (sdb > sde) are a member of a software (mdadm) raid and /dev/sda is ssd so excluded that

---

### Post by TheFu on 2013-06-19
Is spinning down a RAID set a good idea?  Forget if it is allowed. is it a good idea?

---

### Post by SlugSlug on 2013-06-19
not sure, dont see why not. Still want the other drives to spin down regardless

---

### Post by TheFu on 2013-06-19
> **SlugSlug said:**
> not sure, dont see why not. Still want the other drives to spin down regardless

Data corruption is a reason "why not."  I know that some drives spin down automatically and it requires 15 seconds to spin back up. That's a long time for an OS to wait, IMHO.  I avoid using those HDDs in my arrays. Personal choice.

[http://www.tomshardware.com/forum/257925-32-spin-spin-down](http://www.tomshardware.com/forum/257925-32-spin-spin-down) has more authoritative answers than mine. Seems I could be completely wrong.   

Found this on my RAID system: *Please  read  /usr/share/doc/hdparm/README.Debian for notes about known issues, especially if you have an MD array.*  It is running 10.04, so there may be fewer/different issues on newer versions.

Inside that file on my system is says:
> Please do not add anything to hdparm.conf, and instead run hdparm by hand only after you are sure that your array has finished rebuilding.
Seems there are failure modes that CAN cause data corruption when hdparms is used on mdadm RAID disks.

Good luck.

---

### Post by SlugSlug on 2013-06-19
thanks, am not to bothered about the raid it's a raid0 so no rebuilding just crash and burn :)

I've no idea why hdparm.conf has no effect on any drive tho...?

---

### Post by TheFu on 2013-06-19
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/595138](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/595138)  seems related?  Perhaps?

RAID0 for a scratch area is perfect, which seems to be your use. I used RAID0 improperly about a decade ago and lost 80% of my data, not just the data on the failed drive.  OTOH, I got "backup religion" due to that, so it was a huge win overall.

---

### Post by sandyd on 2013-06-19
If the drive support power management (I have come accross some that dont), see if it is smart that is waking the drives up

See [http://ubuntuforums.org/showthread.php?t=1725263&p=10668174&viewfull=1#post10668174](http://ubuntuforums.org/showthread.php?t=1725263&p=10668174&viewfull=1#post10668174)

---

### Post by SlugSlug on 2013-06-19
dosen't look like smart is installed, is there an alternitive to hdparm to spin the drives down?

Does suspending the system spin them down, and will a ftp or ssh connection wake it back up if mobo supports WOL

---

