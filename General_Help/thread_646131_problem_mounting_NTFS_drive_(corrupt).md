---
title: "problem mounting NTFS drive (corrupt?)"
date: 2007-12-20
forum: General Help
---

### Post by thebeefytaco on 2007-12-20
I reformatted my system recently, (storage drive wasn't even involved, it also used to mount fine) and now here is what I get as an error code (and I'm using NTFS 3g)
```
Mounting /media/disk failed.

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

I've set up raid on other hard drives in the system, but not this one.
I haven't done chkdsk on windows yet, the only reason it was nfts is because it was my brother's old drive and I didn't feel like reformatting to put stuff on it, but now I have A LOT of important data on it such as my just completed website which I don't have any other backup of.

Please let me know if you need any more information on how to fix this problem and anything that you think would help, and I'll try and reply asap.

thanks.
EDIT: i've started to try and recover some of the files with testdisk

---

### Post by thebeefytaco on 2007-12-21
ok, so possibly a problem with my current installation? I booted into system rescue cd and it could see all of the files fine, but when I try to load it through this install it says it's corrupt, reinstalling is the last thing I want to do since i juuust finished configuring everything to my liking.

---

### Post by monkeyking on 2007-12-21
Do a backup,
and then try to fix it.

[http://groups.google.com/group/microsoft.public.windowsxp.general/msg/8855796167331b7c?q=fixmbr+c:+Sam+From+there+try:&hl=en&lr=&rnum=1](http://groups.google.com/group/microsoft.public.windowsxp.general/msg/8855796167331b7c?q=fixmbr+c:+Sam+From+there+try:&hl=en&lr=&rnum=1)

---

### Post by thebeefytaco on 2007-12-21
thanks I'll try that out after I finish typing up this paper

---

