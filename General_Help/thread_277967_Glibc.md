---
title: "Glibc"
date: 2006-10-15
forum: General Help
---

### Post by jpe2000 on 2006-10-15
Well, I never got any help on this from the Gaming board here on the Ubuntu forums. I am trying to install Unreal Tournament 2003 for Linux. Please help me.

Here is my error.

[B]
make[1]: *** No rule to make target `/home/josh/build/Versions.all', needed by `/home/josh/build/abi-versions.h'. Stop.
make[1]: Leaving directory `/home/josh/Desktop/glibc-2.5'
make: *** [all] Error 2[/B]

PS - I need version 2.2 or higher. I'm trying to get version 2.5 to install.

---

### Post by DirtDawg on 2006-10-15
> **jpe2000 said:**
> Well, I never got any help on this from the Gaming board here on the Ubuntu forums. I am trying to install Unreal Tournament 2003 for Linux. Please help me.

Here is my error.

[B]
make[1]: *** No rule to make target `/home/josh/build/Versions.all', needed by `/home/josh/build/abi-versions.h'. Stop.
make[1]: Leaving directory `/home/josh/Desktop/glibc-2.5'
make: *** [all] Error 2[/B]

PS - I need version 2.2 or higher. I'm trying to get version 2.5 to install.

Is this error happening when you're trying to install Unreal or the glibc library?

I believe glibc is in the repositories. Have you tried installing it through synaptic? Also, if you're trying to build Unreal from source, then you'll need anything named glibc-dev or similar as well.

---

### Post by jpe2000 on 2006-10-15
I get that error when trying to install glibc. And I have tryed Synaptic but it's version 2.0.

---

### Post by DirtDawg on 2006-10-15
I've been looking into this and I think the entire O.S. is built around glibc. Therefore, I belive upgrading glibc might fry your system entirely. 

I'm not sure about this, it's just the impression I'm getting from the reading I've done the last half hour or so. 

Sorry I can't be of more assistance. Hopefully, someone will trip over this thread with more knowledge about base-level libraries than I have. 

Anyone?

---

### Post by jpe2000 on 2006-10-15
I hope I'm able to upgrade.

---

### Post by jpe2000 on 2006-10-15
Bump before I go to bed.

---

### Post by po0f on 2006-10-16
jpe2000,

I doubt a game made in 2003 requires a library version that wasn't in existence back then.  ;)  On Dapper, the current version of glibc, aka libc6, is 2.3.6, which is greater than 2.2.  Edgy's libc6 is 2.4, as glibc-2.5 is still in development.

---

### Post by jpe2000 on 2006-10-16
[B]cp: reading `Maps/CTF-Geothermal.ut2.uz2': Input/output error
failed to uncompress file.
./setup.sh: line 104:  5629 Aborted                 "$setup" "$@"
./setup.sh: line 104:  6652 Segmentation fault      "$setup" "$@"
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup
The program returned an error code (1)[/B]


Why do I get this error then?

---

### Post by jpe2000 on 2006-10-16
Bump anyone?

---

### Post by jpe2000 on 2006-10-16
Bump before I go to bed.

---

