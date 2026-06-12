---
title: "Grub &amp; flash drives"
date: 2007-07-06
forum: General Help
---

### Post by M$LOL on 2007-07-06
I managed to install a system on my USB flash drive, as the installer recognized it as a SCSI disk. How do I get it to boot? The BIOS is so old that it doesn't recognize the device (I think), so Grub won't let me boot from it (gives me Error 21). Are there any other ways I can boot it?

Thanks.

---

### Post by init1 on 2007-07-07
> **M$LOL said:**
> I managed to install a system on my USB flash drive, as the installer recognized it as a SCSI disk. How do I get it to boot? The BIOS is so old that it doesn't recognize the device (I think), so Grub won't let me boot from it (gives me Error 21). Are there any other ways I can boot it?

Thanks.
If Grub loads, then the BIOS recognizes the device. Some distros simply do not work on some computers. What distro are you using? I can suggest some other distros if this one does not work. The other options for boot loading are syslinux and lilo. I may be able to make you a custom syslinux.cfg if you tell me the distro you are using.

---

### Post by M$LOL on 2007-07-08
No, I have Grub installed on a different device (primary hd), since the Bios doesn't recognize the flash one.

Oh, yeah, it's Debian 4-point-whatever. I just got the Net install CD so I didn't have to DL 700MB+ xD

---

### Post by M$LOL on 2007-07-11
Ugh, I hate to bump, but is there any way I can get this to work?

---

### Post by init1 on 2007-07-25
> **M$LOL said:**
> No, I have Grub installed on a different device (primary hd), since the Bios doesn't recognize the flash one.

Oh, yeah, it's Debian 4-point-whatever. I just got the Net install CD so I didn't have to DL 700MB+ xD
OK, I get it. I'll think about it. I might PM you later.

---

### Post by init1 on 2007-07-25
So, you installed Debian on your USB drive, and you want to boot it from the GRUB on your hard drive? GRUB may not recognize your device. Do this:
Start up your computer. Make sure your USB drive is connected.
When GRUB loads, press "c". This will put you in the GRUB command line.
Type "root (" and then press the tab key. Tell me what you see.

---

