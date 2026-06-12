---
title: "Power Failure --&gt; GRUB Failure"
date: 2007-09-16
forum: General Help
---

### Post by database_dan on 2007-09-16
Hi guys, I hope you can help on this one...

My roommate's computer was on, and sitting idle for hours, running Feisty Fawn (dual boot with Windows XP), when all-of-a-sudden I turned the circuit breaker off (I needed to install a ceiling fan in his room). When he came back home this evening, he certainly enjoyed the new ceiling fan, but the mood turned sour when he booted the machine and GRUB failed to perform. I don't recall an error message, just got the GRUB prompt (never a boot menu to get into X or Win):
```

GRUB>

```

Of course I tried:
```

GRUB> boot

```
to no avail

I thought the problem was that the hard drives were never properly unmounted, so I popped in LIVE CD and mounted each of the 6 drives, shutdown Ubuntu, and rebooted. The result was the same, GRUB failed.

I have done some other checking around and have not come up with any real ideas other than:
1) fschk (do I need to throw any parameters in?)
2) formatting the swap partition clear out any data

Thanks for any help and ideas here!
~Dan:confused:

---

### Post by Sef on 2007-09-16
Try [Super GRUB]("http://forjamari.linex.org/projects/supergrub/").

---

### Post by database_dan on 2007-09-16
> **Sef said:**
> Try [Super GRUB]("http://forjamari.linex.org/projects/supergrub/").

Thanks for the reply. I have downloaded Super Grub. I burned the image to a CDROM. When I boot from the CDROM, it looks like it makes it to GRUB stage 2. No errors are thrown, but I go straight to the GRUB bash. I guess this is to be expected.

On another note, I tried booting the machine normally (without super grub), and it appears to be failing on stage 1.5, but with no error message.

Basically I don't know how to use super grub, and there isn't any documentation on the site ([http://forjamari.linex.org/docman/?group_id=61](http://forjamari.linex.org/docman/?group_id=61)). Is there a way to use the LIVE CD to repair GRUB? Or how do I use Super Grub?
Thanks,
~Dan

---

