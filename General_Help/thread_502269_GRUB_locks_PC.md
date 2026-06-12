---
title: "GRUB locks PC"
date: 2007-07-16
forum: General Help
---

### Post by le_jawa on 2007-07-16
Ok, I'm stumped on this one, and wanted to see if somebody might see something I'm overlooking.

I just did a fresh install of Windows XP (I already had Windows dual-booting with Ubuntu for the last few years).  In doing this, I knew I'd have to re-install GRUB, but I wasn't worried about it, I've done it plenty of times before.  No problem, right?  ;)  The Windows install went fine, so once I had it in working order, I decided it was time to get GRUB & Linux back, so I popped in a Fedora CD I had handy and booted into rescue mode.  I ran GRUB from the CD and gave it the following commands:

```

root (hd0,1)   #Linux is installed on /dev/hda2  (or sda2 with the new kernel)
setup (hd0)

```All of the usual success messages came up, and I was satisfied, so I quit GRUB and rebooted.  When the PC should have booted GRUB, it instead just froze without even giving me a GRUB phase message.  I thought this _could_ be because I used Fedora's GRUB, so I booted from the CD, mounted /dev/hda1 again (as before) and ran GRUB from my Ubuntu partition this time instead of from the rescue CD.  I repeated the above procedure, and received the same result.

Any thoughts as to why GRUB is locking my PC?  I've never seen it do this before.  It's locked so hard that even a three-finger salute won't work.  I'm open for suggestions.

Thank you,

Jason

---

### Post by splintercellguy on 2007-07-16
Probably redundant but maybe try Super GRUB? And are you hard drives in any special configuration?

---

### Post by le_jawa on 2007-07-16
Nothing that I would call special.  hda is a drive with 4 partitions (one Win, 3 Lin) and has a zip drive slaved to it.  The second controller has a CD-burner and DVD burner on it.  They've never been a problem before.

I've heard that GRUB 2.0 is in the works.  Is that the same as super GRUB?

---

### Post by le_jawa on 2007-07-17
Well, I got off my duff and looked up Super GRUB; he has done really nice work with that thing.  I don't know what it did differently than I did, but it worked.  Thank you for the tip!

Jason Lewis

---

