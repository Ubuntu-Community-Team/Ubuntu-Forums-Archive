---
title: "Can't boot to GUI- 23.04"
date: 2023-07-16
forum: General Help
---

### Post by thelonghop on 2023-07-16
I've been running 23.04 for a couple months with no issue.  After a recent reboot, the GUI doesn't load, but I can get to the CLI.  I'm not sure who to get the desktop.  I've tried startx, but it doesn't start the desktop.

---

### Post by Bashing-om on 2023-07-16
thelonghop - Hello; Welcome to the forums.

How about we consider a broken graphic's driver ?

Boot to the grub menu and select  advanced options >>
A) What results in booting here an older kernel ?
B) Select a recovery kernel - and in the resulting menu choose "failsafeX"

what results from either/both ?

[INDENT]we can fix a broken system
[INDENT][INDENT]A broken heart takes a while
[/INDENT][/INDENT][/INDENT]

---

### Post by thelonghop on 2023-07-17
> **Bashing-om said:**
> thelonghop - Hello; Welcome to the forums.

How about we consider a broken graphic's driver ?

Boot to the grub menu and select  advanced options >>
A) What results in booting here an older kernel ?
B) Select a recovery kernel - and in the resulting menu choose "failsafeX"

what results from either/both ?
[INDENT]we can fix a broken system[INDENT][INDENT]A broken heart takes a while
[/INDENT]
[/INDENT]
[/INDENT]

Hi, thanks.  I had to modify the grub file to get the menu to show, but was finally able to select the previous kernel and it booted to the gui!  I updated to my latest graphics driver, rebooted and it loaded without issue.  Thanks for pointed me in the right direction.

---

### Post by Bashing-om on 2023-07-17
thelonghop - outstanding

Pleased you have resolution to the issue :D

As this issue is ended --
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

As a point of concern:
> 
 modify the grub file

should not have been needed unless you had set the time out to zero. Generally just spamming the escape key will produce the grub boot menu, from which one can make the selections.

[INDENT]all a process of learning
[/INDENT]

---

