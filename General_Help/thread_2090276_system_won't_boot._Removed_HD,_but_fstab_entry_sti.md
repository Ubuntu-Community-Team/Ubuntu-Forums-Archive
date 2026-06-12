---
title: "system won't boot. Removed HD, but fstab entry still there"
date: 2012-12-01
forum: General Help
---

### Post by syxbit on 2012-12-01
I have a boot HD, and a secondary HD. I added my secondary HD to /etc/fstab, and everything worked fine. Then I removed a secondary hard drive and sold it. I forgot to remove line in fstab, and now my system won't boot.
Is there any way to fix this besides booting a rescue disc and removing the mount line from fstab?

It seems like a really stupid idea for the system not to boot. What happens if a hard drive goes bad? You can't boot your system? Is there an fstab config setting where you can tell the system to boot if the HD isn't found?
I personally switch HDs in and out every now and again, and have been burnt by this several time.

Thanks for any advice.

---

### Post by sudodus on 2012-12-01
I think there is a text dialogue at boot. If you switch off the 'quiet' and 'splash' options (edit the grub menu commands), you will see that dialogue. You can press a key (I forget which one, but you will see it) to skip trying to mount the removed partition.

But it might be as easy to boot a live session and edit /etc/fstab.

---

### Post by dcstar on 2012-12-01
> **syxbit said:**
> 
..........
Is there an fstab config setting where you can tell the system to boot if the HD isn't found?


Yes, it is called "**noauto**" and can be found be looking at the mount man page.

Just boot off a Live CD and edit the fstab file on the hard disk, it should take you all of 5 minutes to fix.

---

