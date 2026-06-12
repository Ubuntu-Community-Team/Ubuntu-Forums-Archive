---
title: "SNAP version of GIMP having screenshot path issue (fixed)"
date: 2024-11-04
forum: General Help
---

### Post by RangerK on 2024-11-04
Hi All,

After the recent update to 24.04.1 LTC, I started having trouble with screenshots.

(FWIW, I use XUBUNTU.)

In my normal workflow often took screenshots, and then opened them in GIMP to draw some stuff and illustrate concepts to my team.

Since the update, I could not do this.  I was getting a strange error saying the file wasn't there.

[IMG]https://imgur.com/a/qZkhQec[/IMG]

[IMG]https://i.imgur.com/2hOXqsH.png[/IMG]

The file was clearly there in the correct folder, however it seemed to get created immediately AFTER Gimp tried and failed to open it.

Chat GPT told me something confusing about "AppArmor confinement" which i'd never heard of before and didn't feel like learning.  It also recommended trying to non-Snap version of Gimp.  

Reverting to a non-Snap version solved my Problem.

---

### Post by TheFu on 2024-11-05
snap's cannot write to /tmp/.  Sorry.  

Directories were snap constrained programs are allowed to write are in you HOME by default and, if the project snap packager allows AND you tell it to allow writing, places under /media and /mnt are also allowed.  

Welcome to the world of snaps.

BTW, if this is SOLVED, please use the thread tools button to mark it that way so others don't waste time trying to help.

---

### Post by RangerK on 2024-11-05
Thanks for that.  

I would have assumed that the screen capture tool writes to /tmp/ before Gimp opens the file, but it seems that Gimp is asked to write there?

Anyway, the thread is marked as SOLVED.  Thanks!

---

### Post by TheFu on 2024-11-05
Snaps cannot access /tmp/ .... so if THE Gimp is a snap, it can't see any files in /tmp.   These new programmers doing the snap think decides that /tmp/ shouldn't be used for temporary files.  Crazy, right?

---

