---
title: "choose OS at start up"
date: 2007-08-03
forum: General Help
---

### Post by chazaq on 2007-08-03
I have searched ... it is overwhelming ... 

I had my Dell D810 Latitude laptop dual booting with Fedora Core 6.
I removed FC6 and installed Ubuntu into the unused partition.
Ubuntu seems to be working fine. Thanks to you.

However I still need to boot into Windows XP often ...
How can I select, at start up, which OS I want. (Ubuntu or XP)?

Fedora Core6 offered a screen at booting and allowed me 30seconds to choose.

How can I get back into XP now that I have Ubuntu installed?

P.S. the Ubuntu install went ver very well  I ma considering Ubuntu for thte office desktops where I work.  Good job y'all!

---

### Post by LaRoza on 2007-08-03
Do you not get Grub asking you? Or does it hide the menu?

---

### Post by merlinus on 2007-08-03
Post output of these commands:

```

cat /boot/grub/menu.lst
sudo fdisk -l

```

(l is a lowercase L)

-merlin

---

