---
title: "bug or virus"
date: 2008-05-13
forum: General Help
---

### Post by gdkeene on 2008-05-13
i have some really strange behaviour with hardy.  after about 2 hours of use, i can no longer use many applications.  for example when i open firefox, gedit, or openoffice and try to type anything, the program just closes.  the system is basically unusable.  when i first boot, it works fine.  i'm not sure if it's a certain program causig this.

also the shift key or the caps lock do not work either.  it just started happening a few days ago.  for a few weeke before that it was working fine.

any ideas/

is there something i can look for in the log to help me solve this/

thanks

---

### Post by czechman86 on 2008-05-13
try a memtest. on my macbook i had problems like this and found out that i had a faulty mem controller. good luck!

---

### Post by Rhubarb on 2008-05-13
I seem to have come across the same problem on my 64bit 8.04 install here aswell.
My poor solution to this problem that sometimes surfaces is to restart X - press Ctrl + Alt + Backspace and login again.

I can't pinpoint the source of the problem, as I've only got a suspicion it's to do with the nvidia-new drivers / compiz, or possibly because I've been playing around with my wii remote, or something else entirely.

I haven't looked through launchpad yet, the bug may have already been filed:
[https://launchpad.net/ubuntu/hardy/+bugs](https://launchpad.net/ubuntu/hardy/+bugs)

---

### Post by gdkeene on 2008-05-13
these are my last few log entries.  this is what happens when i open a terminal and then press any key - it just closes.

same with gedit, system monitor, or firefox, but not opera



May 13 11:17:33 lavoylx kernel: [ 7778.005542] gnome-terminal[16131]: segfault at 0000002b eip b7858275 esp bfa37f10 error 4
May 13 11:18:20 lavoylx kernel: [ 7818.291006] gnome-system-lo[16162]: segfault at 00000028 eip b78da275 esp bfd20b90 error 4
May 13 11:19:53 lavoylx kernel: [ 7898.416696] gnome-system-lo[16321]: segfault at 0000001c eip b789e275 esp bf86fee0 error 4
May 13 11:20:15 lavoylx kernel: [ 7916.079886] gnome-system-lo[16395]: segfault at 00000032 eip b7912275 esp bfe0e470 error 4
May 13 11:21:09 lavoylx kernel: [ 7959.550347] gedit[16423]: segfault at 00000016 eip b7785275 esp bf83e680 error 4
May 13 11:21:09 lavoylx kernel: [ 7959.707219] gnome-system-lo[16409]: segfault at 00000016 eip b78e7275 esp bfc78ae0 error 4

---

### Post by gdkeene on 2008-05-13
So I discoverd what the problem was.  It was with VMWare Server.  Everytime I used it in Full Screen Mode my computer would act like this.

Solution: don't use VMWare in full screen mode.
Better solution: uninstall VMWare Server and install Virtualbox - works well.

---

