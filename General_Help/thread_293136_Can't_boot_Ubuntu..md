---
title: "Can't boot Ubuntu."
date: 2006-11-04
forum: General Help
---

### Post by delta99 on 2006-11-04
H o w d y

Ok first off all I had windows installed. I then installed Ubuntu. I could dualboot no problem.

Then I deleted and re-installed windows.

My Linux partition remains intact, but I no longer get prompted which os to boot. Can anyone suggest a solution?

Thanks :-D

---

### Post by meng on 2006-11-04
Yes this is an expected problem when Windows is installed (or reinstalled) after Ubuntu. You need to reinstall grub, the instructions are here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by aurimas on 2006-11-04
Probably you should edit menu.lst file. Easy metdod may be using "super grub disk". Google for this.

---

### Post by greeklegend on 2006-11-04
Just boot the LiveCD and run "sudo grub-install /dev/hda"
That should restore GRUB

---

### Post by delta99 on 2006-11-05
Thanks guys, will try it out. Excellent advice :)

---

