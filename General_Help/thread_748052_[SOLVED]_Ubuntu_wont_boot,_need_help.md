---
title: "[SOLVED] Ubuntu wont boot, need help"
date: 2008-04-07
forum: General Help
---

### Post by mordi05 on 2008-04-07
Suddenly I am not able to boot Ubuntu Gutsy. It had been working fine for months prior to a system crash a couple of days ago.

Since my boot settings are set to quiet I can not see exactly at which point it stops, but after the boot menu and splash I just get a black screen for infinity. i.e. it doesn't get to the login screen.

When I try to run it in recovery mode, it says that there are error on the file system and the volume has to be mounted in read-only mode. Then I get a CLI interface. Because of the read-only mode I am not able to edit the menu.lst file so that I can turn the boot process back on verbose either.

I am told to do a manual FSCK, but this just tells me the same thing, that the file system has errors.
I am dual booting windows, thats why I can still post on this forum.

Please does anyone have ant helpful suggestions. (I am absolutely no Linux guru, but I think I can understand most basic instructions and commands.)

---

### Post by prshah on 2008-04-07
> **mordi05 said:**
> 
I am told to do a manual FSCK, but this just tells me the same thing, that the file system has errors.
I am dual booting windows, thats why I can still post on this forum.


When asked to do a manual fsck, (ie without the -p or -a switches) you need to give the command ```
fsck /dev/sdb1
``` or where ever your hard drive lives on your system. During the checking process, fsck will display errors and ask you if you would like fsck to fix them for you, along with dire warnings. In my personal experience, just answering "y" to whatever fsck wants to do has always worked. Your mileage may vary.

---

### Post by fela on 2008-04-07
perhaps when you get the black screen, it is doing the fsck automatically? that happens every 39 mounts and can be rather annoying (but useful)

---

### Post by mordi05 on 2008-04-07
Ok, thanks for the answers, guys.

1. I tried booting my live CD, but I am not sure how this could help. When I boot the cd, it works because it is all from the CD, but then my only option is to do a new install, or perhaps a reapair install with I suppose loss of data.

2. FSCK does indeed display errors, but it is not able to fix them when I answer yes.

Here is one error:

[259.496000] Buffer I/O error on device sda4, logical block 524518
Error reading block 524518 (attempt to read block from file system resulted in short read) while getting next inode from scan.
Ignore error <Y>              if I answer no here, it exits

if I answer Y, I get the question: force rewrite<Y>?
Which doesn't work either.

3. I don't think it is just doing a normal FSCK when I try to boot normally. I left it on for a couple hours and it didn't help. Also there clearly is something wrong that prevents it from booting normally, or even booting the recovering console normally. i.e. I am thrown into read-only mode.

---

### Post by mordi05 on 2008-04-07
This is really killing me. Is there a way to do a repair installation with any hope of maintaining data. Like installed software, customization and most files?

Either with the live CD, or another CD.

---

### Post by prshah on 2008-04-07
> **mordi05 said:**
> 
[259.496000] Buffer I/O error on device sda4, logical block 524518
Error reading block 524518 (attempt to read block from file system resulted in short read) while getting next inode from scan.
Ignore error <Y>              if I answer no here, it exits

if I answer Y, I get the question: force rewrite<Y>?


Yes this is correct; you will get this error a multitude of times, each time with a different block. I just enter a series of "y" and leave it to get on with its job; eg, I press y<enter> about 10 times and leave it, and check back after 10-12 mins, if it is again stalled at a question, y<enter> x 10 times, and so the long day wears on.

Note that this is what I do; I don't know if you will kill your system or not doing this. Sorry for the caveat, but it's important you know that one mans meat can well turn out to be another mans poison...

---

### Post by mordi05 on 2008-04-07
I am now back on my precious Ubunutu, thank you very much. 

Earlier I thought I was just getting the same FSCK error over and over and getting nowhere. That is the problem when trying to do something you don't quite understand.

After ~1 hour of holding down the "Y" key, I am able to boot again. I don't know what my file system did in the first place to get that messed up though, but it sure was able to do it fast.

Thank you all who posted in the topic, and especially prshah who knew exactly how to fix it.

---

### Post by prshah on 2008-04-07
> **mordi05 said:**
> 
I don't know what my file system did in the first place to get that messed up though, but it sure was able to do it fast.


LOL:lolflag:

Are you using an ext2 filesystem by any chance? I had an underpowered machine that I thought ext2 would be better for. I had these problems only when using ext2 and not executing a proper shutdown, and it all never mattered when I switched to ext3.

---

