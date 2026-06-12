---
title: "Tried Gutsy, now I can't boot"
date: 2007-11-02
forum: General Help
---

### Post by Mimsy on 2007-11-02
I wiped Feisty from the laptop whose specs are in my sig, and did a clean install of Gutsy. It didn't work out very well, the W200 driver would not work, despite trying fixes that had worked for others, and the installation was very unstable over all. Lots of black screens of crashing death.

So I put in my Feisty live Cd to do a clean reinstall of that OS, since that one worked very well. It went through the whole process, so I assume it is on there. However, when I try to boot from hard drive, I get this screen:

> Starting up...


invalid compressed format (err=1)

-- System halted

I have tried to boot to recovery mode, but the same thing happens. I can boot from live CDs, but not from the hard drive.

Help...?

---

### Post by arkara on 2007-11-02
this seems to be a corrupted partition.
try to delete it from the live cd and then reinstall the fiesty.

---

### Post by Mimsy on 2007-11-03
Typing from Feisty on the laptop right now. :)

I deleted the partitions from the live CD, using fdisk, and reinstalled with my Feisty disk. Everything looks like it's back to normal, all I need to do now is restore my backups. Thanks! :)

---

