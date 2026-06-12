---
title: "GRUB error 18"
date: 2007-09-08
forum: General Help
---

### Post by MsErja on 2007-09-08
I am staying near New Delhi railway station and my UBUNTU, the newest version, has collapsed I need help from someone who knows the system well enough to be able to clear the problem.
I have 

GRUB
error 18 or 
GRUB 
error 16 displayed on the screen.

I need the computer now and will not stay so long in Delhi. I really hope someone can help me.
Please contact
9871527660

Ms Erja from Finland

---

### Post by logos34 on 2007-09-08
error 16 & 18:
[http://users.bigpond.net.au/hermanzone/p15.htm#16](http://users.bigpond.net.au/hermanzone/p15.htm#16)
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

Go into the Bios and make sure hard disk detection is set for [auto], not [user].

Boot the live cd and do a filesystem check of root partition:

**sudo e2fsck -f -y -v /dev/hda1 ** (substitute your root for hda1)

---

