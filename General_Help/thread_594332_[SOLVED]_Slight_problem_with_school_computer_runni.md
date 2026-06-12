---
title: "[SOLVED] Slight problem with school computer running Linux"
date: 2007-10-27
forum: General Help
---

### Post by PmDematagoda on 2007-10-27
Ok, it seems that I have caused a problem on my school computer. I get the following message when trying to install anything:-

```
E:Error,pkgProblemResolver::Resolve generated breaks, this may be caused by held packages
E:unable to correct dependencies
```

This occurred after I accidentally "updated" a very critical package(The one that governs the behaviour of Firefox, Abiword and many other programs).

---

### Post by mdurham on 2007-10-27
I can't answer your query PmDematagoda, but it would probably help if you said:

what method are you using to do updates?
what was the 'very critical package' that you installed?
what new thing are you trying to install?

this might give someone a clue to enable them to help you.

Cheers, Mike

---

### Post by PmDematagoda on 2007-10-27
I was not doing an update, I was merely trying to solve the dependencies for Wine and I went too far. I cannot do any updates due to the fact that the PC is completely offline. I cannot install ANY program/package at all. The package name was, I believe to be, libc6.

---

### Post by hikaricore on 2007-10-27
If you removed/broke libc6 your options are very very limited..

---

### Post by PmDematagoda on 2007-10-27
Sadly, I believe that maybe true, but the case here is that the libc6 was updated and I believe is missing some other files required to complete the update. If I could somehow complete the "update" then this problem can be fixed.

---

### Post by hikaricore on 2007-10-27
I'm not personally familiar with the process, but I believe you may be able to boot from a livecd and chroot into your current system to resolve the problem.

Just a suggestion, sorry I can't offer more indepth info.

---

### Post by PmDematagoda on 2007-10-27
> **hikaricore said:**
> I'm not personally familiar with the process, but I believe you may be able to boot from a livecd and chroot into your current system to resolve the problem.

Just a suggestion, sorry I can't offer more indepth info.

Forgive me, but what do you mean by "chroot"? How do I do such a thing?

---

### Post by PmDematagoda on 2007-10-28
Anyone please?

---

### Post by pizzy on 2007-10-28
if you're online now then download the libc6 package stick it on a disc and then install it on the school computer

---

### Post by PmDematagoda on 2007-10-29
I would have done that already if it wasn't for the fact that nothing can be installed.

---

### Post by PmDematagoda on 2007-10-31
Doesn't anyone know any suggestions/solutions on how to solve this problem?

---

### Post by PmDematagoda on 2007-11-19
Solved it.:)

I simply used the "dpkg -i --force-downgrade" command to downgrade the "alien" Gutsy packages to the Feisty ones, Xubuntu now works properly with no more problems.

Thanks for anyone who tried to help me with this issue:).

---

