---
title: "Install software without being root"
date: 2007-12-28
forum: General Help
---

### Post by Dooley on 2007-12-28
Hi there,

I was wondering if its possible to install new software without root access. Ie make changes only to my home directory not to system wide ones. 
I'm sure this is possible but I just have no idea how. 

Thanks in advance for your help.
Dooley

---

### Post by Kzin on 2007-12-28
As far as I understand you could compile things manually, set up the configure to install to a directory only you had access to (Such as your home folder, and assuming there is a configure shell script with the source).

Not sure if it can be done for something like apt-get as I am not really familiar with debian packages.

---

### Post by Steveway on 2007-12-28
Why do I hear it screaming security risk?
I'm not quite sure.
But if you think about it you'll know what I mean.

---

### Post by Dooley on 2007-12-28
Kzin do you happen to know what I need to pass into the configure command to install to my home directory.

I know this may pose a security risk but if the admin could install software correctly in the first place......

---

### Post by Dooley on 2007-12-28
Acutally tis all good --PREFIX= works fine

:D

Cheers.

---

### Post by Kzin on 2007-12-31
> **Dooley said:**
> Acutally tis all good --PREFIX= works fine

:D

Cheers.

So you got it installed?

---

