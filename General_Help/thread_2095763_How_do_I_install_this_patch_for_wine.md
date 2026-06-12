---
title: "How do I install this patch for wine?"
date: 2012-12-17
forum: General Help
---

### Post by silverhaze06 on 2012-12-17
So I'm running the Netflix desktop app for ubuntu, and am effected by [the choppy video bug]("https://bugs.launchpad.net/netflix-desktop/+bug/1083858"). There is a patch to try and fix it [here]("https://launchpadlibrarian.net/126046826/tmp.diff") but I have no idea how to install it. Any help would be great!

---

### Post by andrew.46 on 2012-12-18
I could not see which application this patch is designed for? But in general a patch can be applied to source code and then the source code needs to be compiled and then the application packaged.

---

### Post by mc4man on 2012-12-18
It's unclear whether the author of the patch wished it against wine-1.4/1.5 or   wine-compholio-1.5.x. It would likely apply against any though 
I'd guess the latter.

Easily done as in screen - make build folder, cd to it, apt-get the source.
Dl & place patch ( currently named tmp.diff) in build folder. cd to source & run
```
patch -Np1 -i ../tmp.diff
```

Ex.
> :~/Desktop/wine/wine-compholio-1.5.19~raring$ patch -Np1 -i ../tmp.diff
patching file dlls/ntdll/time.c
patching file dlls/ws2_32/socket.c
Hunk #1 succeeded at 5891 (offset 8 lines).

Don't have or want to install wine or have netflix so that's all I can say.

---

### Post by silverhaze06 on 2012-12-18
> **mc4man said:**
> It's unclear whether the author of the patch wished it against wine-1.4/1.5 or   wine-compholio-1.5.x. It would likely apply against any though 
I'd guess the latter.

Easily done as in screen - make build folder, cd to it, apt-get the source.
Dl & place patch ( currently named tmp.diff) in build folder. cd to source & run
```
patch -Np1 -i ../tmp.diff
```

Ex.

Don't have or want to install wine or have netflix so that's all I can say.

Ok, i got the file in a folder called wine on my desktop. I copied the wine build into that folder from /opt/wine-compholio
but after that I'm completely lost. What do I need to type in exactly to get this working? I have no idea when it comes to all this code.

---

### Post by mc4man on 2012-12-18
> **silverhaze06 said:**
> Ok, i got the file in a folder called wine on my desktop. [COLOR="Red"]I copied the wine build into that folder from /opt/wine-compholio[/COLOR]
but after that I'm completely lost. 
No, you'd need to get the intended?? wine source, patch, compile & install. (or possibly just replace 2 newly compiled .dll's

I'd think if this 'fix' is good then it'll show up in your compholio ppa shortly so you may wish to wait..

---

### Post by silverhaze06 on 2012-12-27
> **mc4man said:**
> No, you'd need to get the intended?? wine source, patch, compile & install. (or possibly just replace 2 newly compiled .dll's

I'd think if this 'fix' is good then it'll show up in your compholio ppa shortly so you may wish to wait..

True, marking this as solved.

---

