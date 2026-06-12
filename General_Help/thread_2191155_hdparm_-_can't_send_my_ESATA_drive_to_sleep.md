---
title: "hdparm - can't send my ESATA drive to sleep"
date: 2013-12-01
forum: General Help
---

### Post by Belveder on 2013-12-01
Hi,

I know that the question how to efficiently turn hard drives on and off is discussed a lot, but I did not find any answer to my problem anywhere yet. I'm running a small Atom-based server on an Asus AT4NM10T board, and I used a cable to create an ESATA connector from one of my internal SATA connectors. I connect an external Buffalo Drive Station via ESATA to this connector, and it works fine basically. The mount point is shared over samba, but is only used seldomly to stream videos. 

The real problem is that I can't put the drive to sleep. Whenever I do a 
```
hdparm -y /dev/sdb
```
or
```
hdparm -Y /dev/sdb
```
it turns off and immediately on again (including some cracking due to repositioning of the heads). I also used smartctl or 
```
sdparm --stop /dev/sdb
```
but that has basically the same effect. So for the time being I left the drive spinning; I used auditd to watch the folder access, but there is no access. Still the drive won't spin down... setting APM on the drive (hdparm -B ...) of course does not work due to the use of the external controller... I also tried to work with /proc/diskstats, but that does not really work either.
Same for 
```
sg_start --stop /dev/sdb
```


Is there anyone who can tell me why I can't shut down the drive? Even if I unmount it, I can't... Any help is highly appreciated.
Cheers...

---

