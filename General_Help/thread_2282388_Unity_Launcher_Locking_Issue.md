---
title: "Unity Launcher Locking Issue"
date: 2015-06-13
forum: General Help
---

### Post by alex400 on 2015-06-13
I'm unable to lock applications (e.g. google chrome) to the unity launcher such that they remain locked after I close them.  To lock an application, I open it, right click it's icon in the unity launcher, and then select "lock to launcher."  When I close the application, the icon vanishes from the launcher.

A related problem is that icons I try to remove from the launcher (e.g. libreoffice) do not stay removed.  I right click the icon I want to remove, select "unlock from launcher," and the icon temporarily disappears.  However, the next time I attempt to *lock* another icon to the launcher (which is always unsuccessful, as above), all of the previously removed icons reappear.

So far I've been unable to find any other documented cases of this issue.  Thanks in advance,

Alex

---

### Post by yetimon_64 on 2015-06-13
Check the following link, maybe try following the steps in the first answer by opening "unity-control-center" in terminal then open the "Appearance" Tab. Then see if you get any errors, particularly any errors like 
> Cannot open dconf database: invalid gvdb header

The link : [http://askubuntu.com/questions/586166/can-not-unlock-from-and-lock-to-launcher](http://askubuntu.com/questions/586166/can-not-unlock-from-and-lock-to-launcher)

The following quote from the link makes me think you may have a similar sort of problem,
> All the things remain the same except that applications in Launcher changed back to default. Why? And I cannot unlock from Launcher and lock to Launcher, ...

---

### Post by alex400 on 2015-06-14
You sir are a gentleman and a scholar.  It worked! \\:D/

Thanks a million.

---

