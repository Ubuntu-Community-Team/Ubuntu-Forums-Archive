---
title: "Problem mounting Truecrypt partition in Ubuntu 14.04"
date: 2015-11-01
forum: General Help
---

### Post by Minny on 2015-11-01
I have been running ubuntu 14.04 LTS on my desktop for about a year now. I have 2 Truecrypt encrypted partitions on my desktop, one of which is a partition using system encryption requiring pre-boot authorisation, from which I can boot Windows 7 if I want to. The other is just for storage and doesn't require any pre-boot authorisation. I was able to mount either of these partitions from Truecrypt while running ubuntu.

About 6-8 weeks ago I started having a problem mounting the system partition in ubuntu. It comes back with an error that says 'Command "mount" returned error 1.' The partition will still mount at boot time if I choose it, enter the password, and let Windows start up. So I'm pretty certain the problem is with ubuntu, probably something got changed in an update that came out back then. Truecrypt is not having any problem mounting the partition I just use for storage.

I have tried uninstalling and re-installing Truecrypt. Didn't fix it.

I have checked my syslog and it always has this message when Truecrypt fails to mount the partition:

Nov  1 13:08:47 len-Studio-XPS-8000 kernel: [62585.811907] blkid[28331]: segfault at ffffffffa30dfd2c ip 00007f09d0e7c136 sp 00007ffd3dcad290 error 5 in libblkid.so.1.1.0[7f09d0e69000+23000]
Nov  1 13:08:47 len-Studio-XPS-8000 kernel: [62585.978203] mount[28334]: segfault at ffffffffa392b0dc ip 00007f56dd9ab136 sp 00007ffd38de1060 error 5 in libblkid.so.1.1.0[7f56dd998000+23000]
Nov  1 13:08:48 len-Studio-XPS-8000 kernel: [62586.096240] mount[28336]: segfault at ffffffffa28e5fdc ip 00007ffab9e1a136 sp 00007ffd51ad6a30 error 5 in libblkid.so.1.1.0[7ffab9e07000+23000]

Using Synaptic Package Manager I found a package installed on my system called libblkid1 and forced it back to it's previous version. This also did not fix the problem.

Can anyone offer any guidance on what the problem might be and how to fix it?

I set up a live usb of ubuntu 15.10 and installed Truecrypt on it to see if the partition would mount with this set up. Lo and behold it did. This would seem to confirm that it was some update that was pushed to 14.04 a few weeks ago that caused the problem. I would rather not upgrade my main operating sytem to 15.10 at this point though, would like to fix the problem in 14.04.

---

### Post by Minny on 2015-11-02
Bump.

---

