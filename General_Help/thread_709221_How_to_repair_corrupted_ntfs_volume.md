---
title: "How to repair corrupted ntfs volume"
date: 2008-02-27
forum: General Help
---

### Post by PlatoFunFactory on 2008-02-27
Hey all,

I'm dual booting Windows Visa Home Premium and Ubuntu Studio (Feisty) and have a Western Digital My Book (Essential Edition) 160GB external hard drive formatted NTFS that's giving me trouble. Starting today, Windows doesn't recognize it. In Ubuntu, I can only mount it as read only. Ran ntfsfix on it  and it said I should run chkdsk on it. Problem is, the HD isn't showing up under windows, so how do I run chkdsk on it?

Many thanks.

---

### Post by taurus on 2008-02-27
While you are still able to access it under Ubuntu, why don't you back up your files on that drive and reformat the whole thing again.  Then, you would have a clean drive so you don't have to worry about loosing data later when it won't allow you to access it even under Ubuntu.

---

### Post by Salpiche on 2008-02-27
sounds like you unplugged the disk from without ejecting, try plugging it after a reboot, first on vista if it does see it then eject it and do the same on Ubuntu. it has happened to me more than once.

You can also go to [http://support.microsoft.com/search/](http://support.microsoft.com/search/) and search for the problem and solution there if it is something else. (I did and found nothing under vista yet you might have more luck)

---

### Post by housam on 2008-02-27
> **PlatoFunFactory said:**
> Hey all,

I'm dual booting Windows Visa Home Premium and Ubuntu Studio (Feisty) and have a Western Digital My Book (Essential Edition) 160GB external hard drive formatted NTFS that's giving me trouble. Starting today, Windows doesn't recognize it. In Ubuntu, I can only mount it as read only. Ran ntfsfix on it  and it said I should run chkdsk on it. Problem is, the HD isn't showing up under windows, so how do I run chkdsk on it?

Many thanks.

Under windows go for start>> all programs >> accessoiries >> comand prompt.
then type ```
C:
```
then type```
CHKDSK
```
or type ```
CHKDSK/F
```

---

### Post by PlatoFunFactory on 2008-03-02
Thanks for the suggestions but no luck so far. 

@taurus: I'm a little low on space to try that option, but using a shared folder on my laptop I might be able to manage it. 

@housam: If I understand the command correctly, you have to be...forgive my inappropriate description here...at the level of the disk to run chkdsk. 
That is, simply running "chkdsk /F" will check and fix your C drive (assuming Windows is installed to "C:\"
I would have to change my directory to the faulty drive for it to chkdsk it, which I can't do since it won't mount (or whatever the Windows equivalent is). 

If anyone has any ideas, I'm all ears.

---

