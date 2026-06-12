---
title: "GRUB failure Error 17, SuperGrub &quot;unlucky&quot;"
date: 2008-02-22
forum: General Help
---

### Post by the_phoenix on 2008-02-22
Hi:

This Newbie needs your help.

In Xubuntu, earlier this week, mycomputer just would not boot.
Kept getting 

GRUB loading...
Error 17

Someone on here recommended SuperGrub. I tried it, and got 

"unlucky" loading report
and Error 15

What do I need to do?
I have photo and work files that I need really badly, on that machine, and the Live disc won't let me reach them.

Is there a way to reload the entire boot file (if there is such a thing) without my computer being formatted, in the process?

Please help me, Linux Geeks and Gods.

---

### Post by Herman on 2008-02-22
:) Hello the_phoenix,
First, try [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method, OR,[ Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line method.

Then try again to boot.

If it still won't boot, please boot your Ubuntu LiveCD again and post the output from the command,
```
sudo fdisk -lu
```Regards, Herman :)

---

