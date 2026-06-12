---
title: "Some issues after upgrading to Ubuntu 13.04"
date: 2013-05-01
forum: General Help
---

### Post by EquuaPotesta on 2013-05-01
So I'd just like to start this by saying I'm new to linux etc.

But here's my situation:

I was running Ubuntu 12.04 LTS and decided to do the upgrade to Ubuntu 13.04.  After the upgrade I noticed two main things, 1. I no longer have my 4 way split desktop, and 2. When I put my machine on suspend, close the lid of my laptop, and then eventually come back to wake it up, the machine just hangs on a black screen.

I'm using an Asus laptop with the 64-bit edition of Ubuntu 13.04

Any ideas?

Thanks
-Equua

---

### Post by JebusWankel on 2013-05-01
To restore the workspace switcher, there is an option in Appearance.

For the suspend issues make sure you include you laptop model and/or your graphics hardware in your google searches.

---

### Post by EquuaPotesta on 2013-05-02
I did some research and it looks like other people with Asus laptops have had the same issue on previous releases of Ubuntu, none of them had a very conclusive fix.  Quite unfortunate

---

### Post by grahammechanical on 2013-05-02
Did suspend work in 12.04?

---

### Post by EquuaPotesta on 2013-05-02
Worked like a charm. I'd close the lid after class, then open it, tap a few keys to wake it up, then come up to the lock screen.

13.04 just doesn't turn on my monitor. I'm having to resort to using my Win7 Partition (oh noooo)

---

### Post by ubnewbie2 on 2013-05-02
> **EquuaPotesta said:**
> Worked like a charm. I'd close the lid after class, then open it, tap a few keys to wake it up, then come up to the lock screen.

13.04 just doesn't turn on my monitor. I'm having to resort to using my Win7 Partition (oh noooo)


I too have lost the ability to resume after "upgrading" to 13.04.  I am on a desktop machine and resume worked fine in 12.04, and 12.10.  I am beginning to suspect something has been changed in this new version, and it's broken a few things. :(

I have also noticed I am getting a lot less answers on AskUbuntu these days, so have returned to these forums to see if more help is available here.

---

### Post by EquuaPotesta on 2013-05-03
So I've decided it'd be best just to roll back to 12.04 (honestly don't see that many advancements in 13 other than a prettier gui)

So i guess follow up question. Is there a way to cleanly roll back to 12.04 and keep my stuff? I'm probably asking too much of linux for all this but anyway a man can dream

---

### Post by ubnewbie2 on 2013-05-03
> **EquuaPotesta said:**
> So I've decided it'd be best just to roll back to 12.04 (honestly don't see that many advancements in 13 other than a prettier gui)

So i guess follow up question. Is there a way to cleanly roll back to 12.04 and keep my stuff? I'm probably asking too much of linux for all this but anyway a man can dream


Well, if you use the built-in backup facility to backup your home directory, it can be used to fully restore it after a clean install of a new operating system.  I have done this on some upgrades.  Also, I have seen a method of generating a list of installed apps that can be turned into a script to automatically re-install every app you had previously.  Probably can be found by Googling.

However, I suppose there is the chance that some program has changed it's data and/or config files during the 13.04 upgrade, that may not handle the downgrade, and I suppose that includes the backup program - other than that, I think it is feasible.  If it fails, you can always return to 13.04, restore your home directory and apps.

I would create a new partition on a hard disk somewhere, and try it there before disturbing the working system.

---

