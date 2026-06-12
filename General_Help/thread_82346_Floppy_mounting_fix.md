---
title: "Floppy mounting fix?"
date: 2005-10-26
forum: General Help
---

### Post by canadianwriterman on 2005-10-26
**Re: Auto floppy mounting and mounting though Nautilus:**

[I]Ok, that's all well, and although annoying, I am happy using the workaround if there isn't any other solution. However, I see that this same problem I am having is reported at [http://bugzilla.ubuntu.com/show_bug.cgi?id=17562](http://bugzilla.ubuntu.com/show_bug.cgi?id=17562), and marked as FIXED (more specifically, fixed upstream). My question then is:

where has that been fixed? I have installed the latest updates and I am still having the same problem!

Or does "fixed-upstream" mean that that has only been fixed for the next "Dapper" release. If that is so, will there not be a patch for Breezy?[/I]

The comment above was made on another forum, but I haven't seen any opinions. Does anyone know if this bugfix (apparently) is available?

---

### Post by oliwally on 2005-10-29
> Does anyone know if this bugfix (apparently) is available

Yes, I'd like to know too! How do we get Breezy to read floppies?

---

### Post by hav0x on 2005-10-29
i feel stupid :|

---

### Post by paddyg on 2005-10-29
yes, the bugfix is available and it works fine.

Just enable ---just for once--- the following rep in /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
```

then let synaptic download and install

pmount 0.9.6-1

---

### Post by gw90se on 2005-10-30
I just checked in for this problem, too. Dang, ya gotta love this forum. Y'all are quick & precise with most answers.

---

### Post by Terrycymru on 2005-11-06
Unfortunately, repository did not work for me. See screenshot of Synaptic error attached.

**SEE PAGE 2 OF THIS THREAD :[http://www.ubuntuforums.org/showthread.php?t=78986](http://www.ubuntuforums.org/showthread.php?t=78986) which provides a script and instructions how to use it. There is no need to mess around amending your sources list. This script will get the fix and install it.**

---

### Post by nSTKo on 2005-11-06
Damn, i whant to download it in the "terminal" with apt-get.
What i need to type? sudo apt-get install pmount0.9.6-1?

---

