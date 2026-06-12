---
title: "Intel Atom: Ubuntu 12.04.2 laptop black screen before login problem."
date: 2013-12-27
forum: General Help
---

### Post by convey1 on 2013-12-27
Hello, I'm quite new to Ubuntu so I'll get straight to my problem. I can't log on, when my laptop boots up all it shows is a black screen usually around the time the log in screen should appear. I've tried the ctrl alt f1 and my password seems to be incorrect, haven't changed it I know well its right, had no idea why this was happening until I had a flash back of the last thing I did which was copying things of a hard drive and getting an error saying I had run out of disk space, thought nothing of it at the time and shut down my computer soon afterwards I assume that may have caused this problem.

Thanks in advance.

---

### Post by QIII on 2013-12-27
Hello!

Can you please give us the specifications of your machine, particularly the graphics card?

---

### Post by convey1 on 2013-12-27
Yeah sure, heres most of the info.[TABLE="width: 615"]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Brand[/TD]
[TD="class: value"]Asus[/TD]
[/TR]
[/TABLE]
[TABLE="width: 615"]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Brand[/TD]
[TD="class: value"]Intel[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Type[/TD]
[TD="class: value"]Intel Atom[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Speed[/TD]
[TD="class: value"]1.6 GHz[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Count[/TD]
[TD="class: value"]2[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]RAM Size[/TD]
[TD="class: value"]1 GB[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"][COLOR=#666666]Computer Memory Type[/COLOR][/TD]
[TD="class: value"]DDR3 SDRAM[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Hard Drive Size[/TD]
[TD="class: value"]320 GB[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"][COLOR=#666666]Graphics Card Description[/COLOR][/TD]
[TD="class: value"]Integrated[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Graphics RAM Type[/TD]
[TD="class: value"]DDR3 SDRAM[/TD]
[/TR]
[/TABLE]

---

### Post by mörgæs on 2013-12-27
A hard disk running full can give all kinds of strange errors. Best to begin with removing as much stuff as possible in a live boot.

---

### Post by convey1 on 2013-12-28
Hello again, I have no idea why but it has started working again, thanks for replying to my question anyways.

---

### Post by mörgæs on 2013-12-28
Good. If you want to prevent more errors please run **df -m** and post the results in CODE tags.

---

### Post by grahammechanical on 2013-12-28
There is something that we can remember for situations like this. At the Grub menu we can select Recovery Mode and we get a menu which has, among other things, an option to "Clean" that will try to make free space.

Regards.

---

