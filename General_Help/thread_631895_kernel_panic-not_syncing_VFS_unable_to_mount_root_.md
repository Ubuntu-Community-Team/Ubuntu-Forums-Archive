---
title: "kernel panic-not syncing: VFS: unable to mount root fs"
date: 2007-12-04
forum: General Help
---

### Post by willie_wang on 2007-12-04
hi everyone.

i've got a major problem! i think my laptop went into suspend and now i can't boot into ubuntu. it throws the following error message when i try to boot into safe mode.

```
kernel panic-not syncing: VFS: unable to mount root fs on 
unknown block(0,0)
```

i can boot into the live cd. is there anything i can do from there to fix this problem? any help would be a lifesaver as i have to work on this pc at uni tomorrow :(

Wil

---

### Post by ResumeMan on 2007-12-17
Sooo...do you suppose you could tell us what you did to solve the problem? I have the same problem and am not having a lot of luck in my forum search.

---

### Post by willie_wang on 2007-12-19
oops, sorry, wasn't really solved. i did a restall of the whole OS. sorry i can't help further.

---

### Post by xaxas on 2007-12-19
Dam fvuckin unstable OS ...
I install some updates and my ccsm gets screwed beyond repair :|

Now, after 3 days i try to install 6 more updates and kaboom ...

```
kernel panic-not syncing: VFS: unable to mount root fs on 
unknown block(0,0)
```

Now what ?
I'm on my live cd looking for answers and nothin ...
Going to reinstall the OS and hope i don't have to format to much :|

People, one sugestion: DO NOT UPDATE !!! No matter what ... DO NOT UPDATE !!! The dam updates screw everyhing up ...

---

### Post by nickoli_02 on 2007-12-19
Don't blame ubuntu, this is grub's fault. This is actually a pretty common error message. The problem is, when you did the update, something changed in your /boot/grub/menu.list, so now it's pointing to the wrong partition and expecting to see an OS. Anyways, the easiest way to fix this is keep a backup of your /boot/grub/menu.lst file, and of /etc/fstab. It's OK if the menu.lst file changes but make sure it's pointing to the right partition.

---

