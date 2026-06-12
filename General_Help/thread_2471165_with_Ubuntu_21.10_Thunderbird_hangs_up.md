---
title: "with Ubuntu 21.10 Thunderbird hangs up"
date: 2022-01-22
forum: General Help
---

### Post by s9032g@comcast.net on 2022-01-22
I notice a number of posting on "ask ubuntu" about this problem. Thunderbird freezes with one or two orange dots by it after use. Have to restart to clear it. Suggestion for using xorg rather than Wayland creates other problems.

Ideas? Snap version?

---

### Post by s9032g@comcast.net on 2022-01-24
Maybe no one is interested. Orange dot shows Thunderbird running, but frozen. System check of processes does nor show it running./

---

### Post by uninvolved on 2022-01-24
Do you have any extensions? 

TB should recently have updated to version 91 - at least it did in the LTS (an unusual circumstance).

I had to go through my extensions and use the process of elimination to get TB working properly again.

---

### Post by s9032g@comcast.net on 2022-01-27
I have version 91.5 with no extensions except an English Pak

---

### Post by walts48 on 2022-01-29
> **uninvolved said:**
> Do you have any extensions? 

TB should recently have updated to version 91 - at least it did in the LTS (an unusual circumstance).

I had to go through my extensions and use the process of elimination to get TB working properly again.

What extensions were causing your problem?

Seems to me something in the Ubuntu build adds those dots.

---

### Post by uninvolved on 2022-01-29
I use quite a few extensions and it turned out to be one about hiding local folders that was supposed to be good for 78+, as memory serves.

---

### Post by FoxJT on 2022-03-11
I am seeing the same problems and have reported them on here.
System: Ubuntu: 21.10 / Gnome: 40.4.0 / TBird: 91.5.0
TBird Problems: Orange dots not clearing and increasing monotonically until TBird "crashes". Right click opens an unremovable window. / TBird crashing after an indeterminate period while moving emails around (linked list problem?) /  Problem with Message Filters' drop down menus. The problems can be "solved" usually, with a reboot, but that shouldnt be necessary!!

The problems seem to have been around for quite a while, but no-one (?) seems to be working on this? Is it a problem with extensions?

---

### Post by FoxJT on 2022-06-07
System updated: TBird 91.9.1 / Ubuntu 22.04 / Gnome 42.1.

Orange dot problem appears to have been solved.

Message filter problem is still there!

---

