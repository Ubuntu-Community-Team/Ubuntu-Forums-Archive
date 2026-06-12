---
title: "How do I Get untubu to work?"
date: 2008-07-08
forum: General Help
---

### Post by yamadog1998 on 2008-07-08
i Downloaded Untubu From Wabi Installer When Starting Up It Goes To Untubu Screen Then Goes To Command Screen with Some Stuff Like ash And Type "help".I Had This Installed Before And never Saw This Screen.I Had To Redownload And Now I Can't Get It To Boot,I Can Only Use Windows.Help Thanks.

---

### Post by ago on 2008-07-08
Run chkdsk /r in windows.
Also if you press esc at boot, select recovery/verbose mode to get more info.
Useful commands are:

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep -i err /casper.log
grep -i mount /casper.log

---

### Post by plastichero on 2008-07-09
Do you stuck at some point with this prompt? 

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/COLOR]

I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that Iselected, it may be different for you)

---

### Post by yamadog1998 on 2008-07-09
Thats It.Thanks

---

### Post by plastichero on 2008-07-09
nice to know it works. :D

---

