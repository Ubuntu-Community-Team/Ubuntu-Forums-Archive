---
title: "Burning CD's"
date: 2008-04-30
forum: General Help
---

### Post by spacefreak86 on 2008-04-30
I got this error message after burning the ISO of Hardy - Alternate i386:

Could not start process Unable to create io-slave:
klauncher said: Unknown protocol"

BTW, the CD was burned using K3B. I tried burning a second one, and still nothing. I booted up the computer, hoping it was just a software issue, but it didn't recognize the LiveCd upon boot (after manually telling it to try to boot off the CD).

Anyone have a starting point for me to try to fix this?

---

### Post by mankygitt on 2008-05-01
Have you verified the checksum of the iso ?
You may have a partial or corrupted download.

You can do this easily in a terminal: CD to the directory where the iso resides on your harddrive (assuming you have a linux-based os) and md5sum <name of ISO file>
eg: I have the 8.04 release candidate live cd image, so
...LinuxDistros$ ```
md5sum ubuntu-8.04-rc-desktop-i386.iso
```
returns
```
86dc6f4792fa5a69e73e30cd33cdfd11  ubuntu-8.04-rc-desktop-i386.iso
```

which matches the published CheckSum value for this ISO on the downloads mirror I obtained it from.

Other things to check: If you are burning to a DVD check that you're using DVD media that is compatible with your optical drive. There are newer DVD-R formats and speeds which often require firmware upgrades.

Good luck
Manky

---

### Post by spacefreak86 on 2008-05-01
Okay, I checked the checksum from the Kubuntu site and it matches. What else could be the issue?

---

