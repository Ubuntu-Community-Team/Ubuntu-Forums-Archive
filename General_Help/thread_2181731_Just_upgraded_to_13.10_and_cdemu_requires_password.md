---
title: "Just upgraded to 13.10 and cdemu requires password to mount/unmount images"
date: 2013-10-18
forum: General Help
---

### Post by adec2 on 2013-10-18
Hi as per thread title really.
I upgraded from 13.04 to 13.10 and cdemu requires password to mount/unmount images all of a sudden is this a cdemu bug or something new that has been added to 13.10 security? Can anybody else confirm this is not just me please?

---

### Post by Goa'uld on 2013-10-18
> **adec2 said:**
> Hi as per thread title really.
I upgraded from 13.04 to 13.10 and cdemu requires password to mount/unmount images all of a sudden is this a cdemu bug or something new that has been added to 13.10 security? Can anybody else confirm this is not just me please?

CDEmu doesn't need a password. I'm not sure what in Ubuntu that cause this.

For starters are your user a member of the "cdrom" group? 

And does your Ubuntu attempt to automatically mount the images loaded by CDEmu. In other words do you get a password request immediately after loading an image in cdemu? I'm not sure where automounting is configured. For me it works correctly without any tinkering.

---

### Post by adec2 on 2013-10-19
When i browse to my image and select it, then the password pops up only after entering my password does it actually mount the image and yes i am already in the cdrom group

Edit. For some reason the problem isnt occurring now, I did nothing but switch the computer on this morning and bam it doesnt ask for a password lol

---

