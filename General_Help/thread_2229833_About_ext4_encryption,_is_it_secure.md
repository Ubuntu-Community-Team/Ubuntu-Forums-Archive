---
title: "About ext4 encryption, is it secure?"
date: 2014-06-15
forum: General Help
---

### Post by fede11223344 on 2014-06-15
Hi, I want to keep my files secure, I have it on a usb drive, the drive is formated as ext4 encrypted with a very very large password (with symbols, numbers, etc). How secure are my files? I mean, if someone have this usb drive, could this guy break this encryption? I'm not asking how to, but I want to know only if it is possible.

Other question, when I install ubuntu 14.04 on my pc, I can encrypt all the drive (I've done this) only checking a checkbox.. how secure is this? Could anyone who has my PC access to files in /home?

Thank you!

---

### Post by TheFu on 2014-06-16
How long will you NOT tell the passphrase when beaten?
Security is hard.
A tiny mistake has almost always been discovered in every security method known. Sometimes those mistakes aren't known publicly for a decade, but they still existed.

If you want to keep the NSA out or Egyptian government, don't be a target.
If you want to keep your little brother out, it is probably fine.

---

### Post by grahammechanical on 2014-06-16
I think that Ubunt uses eCryptfs as the encryption mechanism which in turn uses the AES cipher. So, here is some reading.

> [COLOR=#333333][FONT=Ubuntu]eCryptfs is widely used, as the basis for Ubuntu's Encrypted Home Directory, natively within Google's ChromeOS, and transparently embedded in several network attached storage (NAS) devices.[/FONT][/COLOR]

[https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)

[http://ecryptfs.org/about.html](http://ecryptfs.org/about.html)

[https://slo-tech.com/clanki/10008en/](https://slo-tech.com/clanki/10008en/)

[http://www.linux-mag.com/id/7568/](http://www.linux-mag.com/id/7568/)

[http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

Regards.

---

