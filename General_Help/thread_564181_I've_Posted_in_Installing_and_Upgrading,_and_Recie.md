---
title: "I've Posted in Installing and Upgrading, and Recieve no help"
date: 2007-09-30
forum: General Help
---

### Post by TheShadows on 2007-09-30
Ubuntu 7.04 Hangs on install from live CD at 91%. I changed from a CRT to a 15" NEC LCD52V. Had problems and could only boot to live cd for some reason. I did try reconfiguring the Xserver, and still no go.

So i cleaned the partition and tried install again and its hanged at 91%. Been like that for several hours.

Also keep recieving errors like this one:

udevd-event[1906] (sometimes [1908]): run_program: '/sbin/modprobe' abnormal exit

---

### Post by TheShadows on 2007-09-30
bump

---

### Post by TheShadows on 2007-09-30
Can anyone help? I'd really like to get my ubuntu running again. Please.

---

### Post by TheShadows on 2007-09-30
Ok i'll add some more to this since i can't seem to get a reply.

It hangs at 91% on install which is: module 'aec62xx' for IDE Chipset Support.

Ubuntu 7.04 Hangs on install from live CD at 91%. I changed from a CRT to a 15" NEC LCD52V. Had problems and could only boot to live cd for some reason. I did try reconfiguring the Xserver, and still no go.

So i cleaned the partition and tried install again and its hanged at 91%. Been like that for several hours.

Also keep recieving errors like this one on boot of the Live CD:

udevd-event[1906] (sometimes [1908], [1907], [1915], [1918]): run_program: '/sbin/modprobe' abnormal exit

System Spec's:

AMD Athlon Duron 1.3Ghz
512mb Ram
80GB HD
2x CD-R/RW Drives
1x CD/DVD-R/RW Drive
1x SATA Controller Card (PCI)
1x EIDE 133 Raid Controller Card (PCI)(Highpoint Technologies)
1x 80GB HD (on EIDE controller Card)
OS: Ubuntu 7.04 Fiesty Fawn (Trying to reinstall)
Monitor: LCD 15" Flat Panel (Model LCD52v AccuSync)

---

### Post by TheShadows on 2007-09-30
bump

---

### Post by TheShadows on 2007-09-30
Ok i'll add some more to this since i can't seem to get a reply.

It hangs at 91% on install which is: module 'aec62xx' for IDE Chipset Support.

Ubuntu 7.04 Hangs on install from live CD at 91%. I changed from a CRT to a 15" NEC LCD52V. Had problems and could only boot to live cd for some reason. I did try reconfiguring the Xserver, and still no go.

So i cleaned the partition and tried install again and its hanged at 91%. Been like that for several hours.

Also keep recieving errors like this one on boot of the Live CD:

udevd-event[1906] (sometimes [1908], [1907], [1915], [1918]): run_program: '/sbin/modprobe' abnormal exit

System Spec's:

AMD Athlon Duron 1.3Ghz
512mb Ram
80GB HD
2x CD-R/RW Drives
1x CD/DVD-R/RW Drive
1x SATA Controller Card (PCI)
1x EIDE 133 Raid Controller Card (PCI)(Highpoint Technologies)
1x 80GB HD (on EIDE controller Card)
OS: Ubuntu 7.04 Fiesty Fawn (Trying to reinstall)
Monitor: LCD 15" Flat Panel (Model LCD52v AccuSync)

---

### Post by overdrank on 2007-09-30
> **TheShadows said:**
> Ok i'll add some more to this since i can't seem to get a reply.

It hangs at 91% on install which is: module 'aec62xx' for IDE Chipset Support.

Ubuntu 7.04 Hangs on install from live CD at 91%. I changed from a CRT to a 15" NEC LCD52V. Had problems and could only boot to live cd for some reason. I did try reconfiguring the Xserver, and still no go.

So i cleaned the partition and tried install again and its hanged at 91%. Been like that for several hours.

Also keep recieving errors like this one on boot of the Live CD:

udevd-event[1906] (sometimes [1908], [1907], [1915], [1918]): run_program: '/sbin/modprobe' abnormal exit

System Spec's:

AMD Athlon Duron 1.3Ghz
512mb Ram
80GB HD
2x CD-R/RW Drives
1x CD/DVD-R/RW Drive
1x SATA Controller Card (PCI)
1x EIDE 133 Raid Controller Card (PCI)(Highpoint Technologies)
1x 80GB HD (on EIDE controller Card)
OS: Ubuntu 7.04 Fiesty Fawn (Trying to reinstall)
Monitor: LCD 15" Flat Panel (Model LCD52v AccuSync)

HI have you checksum the disc
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by HermanAB on 2007-09-30
You can try these common trouble fixing switches:
linux noapic nolapic

Otherwise, try another distribution such as Mandriva, Fedora or Suse.  Each distro has a different install script and different machines in their labs that they test with.  So if you shop around a bit, you may get lucky.  Underneath the glitz, all the distros are the same anyway.

Cheers,

Herman

---

### Post by TheShadows on 2007-09-30
I heard Fedora Core was umm yea....not all that great. What one is most similar to Ubuntu?

And where do i do the code you mentioned? Not the CheckSum for the Disc.

---

### Post by bapoumba on 2007-10-01
Threads merged.

---

