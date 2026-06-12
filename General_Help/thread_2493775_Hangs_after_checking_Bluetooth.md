---
title: "Hangs after checking Bluetooth"
date: 2023-12-24
forum: General Help
---

### Post by mokane324 on 2023-12-24
Ubuntu: 23.10
Hardware: Lenovo X1, maybe three years old.

Installed updates last night. This morning, entered password and system hung. Restarted, now hangs after "Reading supported feature" failed on Bluetooth--never had any Bluetooth issues. 

GRUB works fine. This is an internal Ubuntu issue, I think. 

A couple questions:

1. Before making major system changes, I need to back-up. What is the command line syntax to copy files to an external drive?
2. Perhaps a reinstall of Ubuntu 23.10 would fix this. What is the syntax for reinstall saving current file settings (and files)?
3. Is this a known problem with a known solution? A Google search turned up a few examples of this issue with Arch.

All help appreciated.

---

### Post by #&amp;thj^% on 2023-12-24
I have the same type X1 7th Gen, I have no issues with 23.10 or develoment 24.04
Try to bootup again.

---

### Post by mokane324 on 2023-12-24
I didn't either--until installing the updates last night. I was copying music to a USB and left it to run overnight. When I tried to login on the graphic interface, it hung, so I had to shut the computer down. I thought that perhaps it had run out of space, but I could enter recovery mode and there is reported 45g free, so that's not the problem. I tried rebooting many times, but always with the same result. I have been able--by using startx--to get a graphical interface back. So am backing up now. But I think the solution is a reinstall, this time from the graphic interface, which I haven't researched.

---

### Post by #&amp;thj^% on 2023-12-24
Ok I get it now, Yes from the live installer copy over to another drive the stuff you need.
On the next install just don't tick the format option, that "should" leave most if not all your /home intact.
But Defiantly back-up first just in case.
Good Luck

---

