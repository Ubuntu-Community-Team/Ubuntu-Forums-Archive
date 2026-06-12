---
title: "Can't empty the rubbish bin"
date: 2017-10-14
forum: General Help
---

### Post by Phil Binner on 2017-10-14
My system is now full, and this is because I can't empty the rubbish bin. I have tried selecting "Empty rubbish bin on bootup, when I get the message that the system has run out of space; I have tried opening the rubbish bin and clicking on "Empty", and I have tried manually deleting items.  I have also tried changing preferences in Edit for the rubbish bin, but preferences refuse to change.  This seems to be something to do with permissions.

---

### Post by ajgreeny on 2017-10-14
In file manager for your system navigate to .local/share/Trash/files and look at the permissions from a right click ->Properties.

In my system the user (me) is owner and has read/write/execute permissions. No one else has permissions.
You can also look at the permissions for the individual files in .local/share/Trash/files which should be owned by you as well.

---

### Post by Phil Binner on 2017-10-16
Actually, it's got so its got 0 space now and most of it has stopped working. There's nothing I need to keep on that computer so I'll just re-install.  Thanks for your help.

How do I get at the title of this thread to mark it as solved.

---

### Post by vasa1 on 2017-10-16
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dadathome on 2018-01-18
whenever I can't empty the trash bin its because I deleted something from a thumb drive that has since been removed, when I plug it back in and empty trash again it goes empty

---

