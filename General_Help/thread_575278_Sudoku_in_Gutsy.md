---
title: "Sudoku in Gutsy"
date: 2007-10-13
forum: General Help
---

### Post by drworm01 on 2007-10-13
I'm having a problem with Sudoku from the gnome-games package in Gutsy beta. Game plays fine, generates new puzzles and everything, but as soon as I close the program, all my high scores, all the new puzzles and its list of all the puzzles I've completed is gone. So every time I start the program I'm looking at a puzzle I've already done. Anyone having a similar problem or know what could be causing it? I didn't have this problem in Feisty. I have tried removing and reinstalling the packages without any change.
Many thanks.

---

### Post by glennric on 2007-10-21
I am having the same problem.  Did you ever solve this?  I think it is a bug.

---

### Post by drworm01 on 2007-10-21
Nope, still unsolved. In fact I just did a clean install of Gutsy and it still has the same problem. Good to know I'm not alone though.

---

### Post by kerohazel on 2007-10-21
You may want to keep an eye on [https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761)

---

### Post by glennric on 2007-10-21
> **kerohazel said:**
> You may want to keep an eye on [https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761)

This is not the only bug regarding gnome-sudoku.  The bugs are not restricted to Ubuntu either.  The bugs are in the upstream version.  Games don't save and generated puzzles are lost when you close the program.  The save game seems to be partially due to a change in philosophy of the developers.  The loss of generated games may be a side issue.  I think they are going to make the save game feature an option in later versions.

---

### Post by MrWizard on 2007-10-23
I've filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/156487](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/156487)

If any of you have additional information that might be useful in tracking down the problem, feel free to post there.

---

