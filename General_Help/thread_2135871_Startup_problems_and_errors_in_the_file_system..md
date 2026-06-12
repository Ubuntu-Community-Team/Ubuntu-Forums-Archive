---
title: "Startup problems and errors in the file system."
date: 2013-04-15
forum: General Help
---

### Post by NBPX on 2013-04-15
Ubuntu 12.10 calls frequently to check the disks when booting. The problem is that it shows no sign of really being checking it. I just skipping the check to enter the system.


The problem is that now I'm not allowed to modify files on disk and Firefox will not open. Sometimes Chromium neither. When I try to open Firefox comes a message that is already open and asking to close it. But it's not open.


Today I turned on the laptop, using Windows 7, and it appeared that black screen with text prompting fixes disk. I choose to fix. After that, when the Ubuntu boots, this problem appears.


Ubuntu is installed with Wubi, but is on a partition separate from Windows 7, so I deduce that the problem is not with him.


It's difficult for me. Ubuntu has the same level of instability that Windows XP. I prefer it because the user experience is better for me, but I have to reinstall every three months because of one problem or another. And the worst is that this installation is recent. I do not have time to be correcting mistakes all the time because of work and college.

---

### Post by oldos2er on 2013-04-15
> **NBPX said:**
> Ubuntu is installed with Wubi, but is on a partition separate from Windows 7

Are you certain of that? Wubi by definition installs Ubuntu to a file (root.disk) in a Windows partition.

Your problems could possibly be caused by a failing hard disk. Have you run Windows' chkdsk?  Or checked the drive's [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") data?

---

### Post by bcbc on 2013-04-15
Doesn't sound right. All these problems. If you're shutting down normally then it might be some hardware/driver issues. What brand/model/graphics card do you have?

It might be better with a non-Wubi install - especially if you use it more than Windows - but unless you figure out what's causing the instabilities you might have problems with that as well.

---

### Post by NBPX on 2013-04-23
> **oldos2er said:**
> Are you certain of that? Wubi by definition installs Ubuntu to a file (root.disk) in a Windows partition.

Your problems could possibly be caused by a failing hard disk. Have you run Windows' chkdsk?  Or checked the drive's [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") data?

root.disk was in Ubuntu partition.

Disks are ok. Windows don't have problems during execution.

Don't run [COLOR=#000000]chkdsk. [/COLOR]Don't know what is smart data or how to check it.

Problem solved (at least by now). Ubuntu reinstalled (without Wubi). At least it looks a little bit more fast.

---

