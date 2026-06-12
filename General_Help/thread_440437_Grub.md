---
title: "Grub"
date: 2007-05-11
forum: General Help
---

### Post by ihoodz on 2007-05-11
2nd time with in 24 hours.


Alright I'm using Ubuntu 7.04 alternate instillation disk.  I just need to know how to install Grub, so I can choose Ubuntu on my boot up.

---

### Post by shane2peru on 2007-05-11
> **ihoodz said:**
> 2nd time with in 24 hours.


Alright I'm using Ubuntu 7.04 alternate instillation disk.  I just need to know how to install Grub, so I can choose Ubuntu on my boot up.

We are going to need a little more information before we can help you on this one.  Do you mean what partition you should install it on?  Are you dual booting?  

Shane

---

### Post by ihoodz on 2007-05-11
Lets see... Info on my partitions

1 - 50 gig (storage of files)
2 - 15 gig (windows xp)
3 - 10 gig (Ubuntu) Doesn't show up on my boot up list.
4 - small (Switch)

On my start up I have the selection of "Windows xp home etc."  and a corrupt version of xp (it's just a single .dll nothing to worry about).

I've booted Ubuntu before, but when I went to boot back into xp I had the .dll error, so I repaired and it reinstalled xp while just leaving the corrupt .dll there.  I keep hearing that I need Grub to boot into Ubuntu.

I want to do this without messing up my windows xp partition this time.

---

### Post by shane2peru on 2007-05-11
> **ihoodz said:**
> Lets see... Info on my partitions

1 - 50 gig (storage of files)
2 - 15 gig (windows xp)
3 - 10 gig (Ubuntu) Doesn't show up on my boot up list.
4 - small (Switch)

On my start up I have the selection of "Windows xp home etc."  and a corrupt version of xp (it's just a single .dll nothing to worry about).

I've booted Ubuntu before, but when I went to boot back into xp I had the .dll error, so I repaired and it reinstalled xp while just leaving the corrupt .dll there.  I keep hearing that I need Grub to boot into Ubuntu.

I want to do this without messing up my windows xp partition this time.

I messed around with grub a lot and dual booted for over a year and only once was not able to get into Windows XP because of my own foolishness.  Usually you don't mess up XP, however, you have XP on 2 partition, which is a little different.  Here are two links to review:
1.  [http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+re-install+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+re-install+grub)
2.  [http://ubuntuforums.org/showthread.php?t=426895&highlight=how+to+re-install+grub](http://ubuntuforums.org/showthread.php?t=426895&highlight=how+to+re-install+grub)
I have used the 1 option before, number two just popped up.  It may be worth looking at if you have trouble installing grub.  Hope that helps.

Shane

---

### Post by ihoodz on 2007-05-11
Those are talking about the live cd, can I do the same thing with the alternative cd?

---

### Post by 13u11fr09 on 2007-05-11
It sounds like the master boot record (MBR) might have accidently been written over when xp was reinstalled.

Here's a thread with help on getting your MBR setup with grub:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

**EDIT**: Alternative CD should work...

---

### Post by ihoodz on 2007-05-11
> **13u11fr09 said:**
> It sounds like the master boot record (MBR) might have accidently been written over when xp was reinstalled.

Here's a thread with help on getting your MBR setup with grub:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

**EDIT**: Alternative CD should work...

Thanks

---

