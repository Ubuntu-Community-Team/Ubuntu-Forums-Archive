---
title: "IBM Thinkpad R31 mouse goes crazy"
date: 2007-06-04
forum: General Help
---

### Post by rob1101 on 2007-06-04
the mouse (built in one) just seems to randomly go crazy quite often. when i say crazy i mean it jumps all around the screen clicking and dragging for a few seconds. this can get very annoying. any ideas on what could be the problem?

---

### Post by Pragmatist on 2007-06-05
This is a known problem that seems to have a workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21558](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21558)

And:
[https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR31?highlight=%28thinkpad%29]("https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR31?highlight=%28thinkpad%29")

What version of Ubuntu are you using (i.e. Breezy?, Edgy?, Fiesty?)

---

### Post by rob1101 on 2007-06-05
> **Pragmatist said:**
> This is a known problem that seems to have a workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21558](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21558)

And:
[https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR31?highlight=%28thinkpad%29](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR31?highlight=%28thinkpad%29)

What version of Ubuntu are you using (i.e. Breezy?, Edgy?, Fiesty?)

i am using 7.04 i think that is fiesty.? right? and i looked at the links. is there anyway i can fix this problem?

---

### Post by Pragmatist on 2007-06-05
I think you can use the kernel option they specify[B]:

 i8042.nomux=1

[/B]Kernel options, or "kopt" can be found in your /boot/grub/menu.lst file (that is a lowercase L in .lst)

This explains how to use kernel options:
[https://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d](https://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d)

---

### Post by darkstr2o4 on 2007-12-04
I just upgraded to Gusty 7.10 on a thinkpad r31 and I cannot seem to find a solution to this problem.  I attempted to append the kernel but 
**i8042.nomux=1** was already in there and it continues to act erratically. Any suggestions?

---

### Post by rob1101 on 2007-12-07
> **darkstr2o4 said:**
> I just upgraded to Gusty 7.10 on a thinkpad r31 and I cannot seem to find a solution to this problem.  I attempted to append the kernel but 
**i8042.nomux=1** was already in there and it continues to act erratically. Any suggestions?
could you post your file?

---

