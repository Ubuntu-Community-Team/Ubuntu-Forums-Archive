---
title: "Package needs to be reinstalled, undo?"
date: 2006-07-07
forum: General Help
---

### Post by mqnada on 2006-07-07
I think I've messed up... I'm a complete novice with linux and Ubuntu, and tried to install a printer driver for my Brother HL-5040 Laser with this driver from Brother: hl5040lpr-1.1.2-1.i386.deb. I DL'ed it with Firefox and clicked on "open" when it completed. 

Stuff happened, and now my update manager icon on the toolbar stays lit all the time. Synaptic package manager reports: 

```
E: The package hl5040lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

I'd simply like to undo this, and I've no idea how. Thanks in advance.

---

### Post by reacocard on 2006-07-07
to remove, type the following command at the terminal:

```
sudo apt-get remove hl5040lpr
```

(Applications -> Accessories -> Terminal)

---

### Post by mqnada on 2006-07-07
Thanks.

Here's what transpired:

```
john@john-laptop:~$ sudo apt-get remove hl5040lpr
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package hl5040lpr needs to be reinstalled, but I can't find an archive for it.
john@john-laptop:~$


```

No joy....

Problem still there.

---

### Post by vem0m on 2006-07-08
hmmmmm try 
```
sudo dpkg -r hl5040lpr
```

---

### Post by mqnada on 2006-07-08
Thanks for the suggestions. Since this was a brand new install anyway, I just blew it up and reinstalled from scratch, which solved everything. Imagine that! :D

I do appreciate the members of this forum being so quick to jump in with suggestions. 

Gonna spend more time understanding things before I jump in so blindly again.

---

### Post by vem0m on 2006-07-08
heh np much more friendly then windows ever would claim to be BOOOOM(i heard the bomb!) :P

---

