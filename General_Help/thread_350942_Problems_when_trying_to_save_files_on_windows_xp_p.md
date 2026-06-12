---
title: "Problems when trying to save files on windows xp partition"
date: 2007-02-01
forum: General Help
---

### Post by FrancisA on 2007-02-01
Hello, I hope I'm not totally wrong here.

Following (very annoying) problem
until recently, all was working fine so far, but since the last few days,
I have problems with the windows xp paritition, which I mounted in fstab.

I edit(ed) files with SciTE and stored them on the windows xp partition.
So far so good, then I controlled them with reopen the files.
They are stored und you see the changed datas.

When I start windows xp with grub (last time I was on windows I shutdown it with standby),
I see after the restart, that the files are not updated, they looks unchanged, as I did 
not edit them before using Ubuntu.
So I restart Windows XP (I chosed shutdown), then the scandisk or the 
in german "Datenträgerüberprüfung" (data volume check or how is it called in english) started, it complains about interlinked files, and repairs them.

That is very annoying, to not rely on ubuntus file storing to windows xp partition.

I want to change files directly under the windows Xp partition (one can await or 
trust, that linux have no problems with FAT32, isn't it?), and not copy them back and forth
always.

Windows XP home edition, Ubuntu Edgy, FAT32.

What is wrong? :( 
Did I damaged something? I cannot remember changing any crucial things in the last time.
For Answers which helps solving that problem, i would be veeerrry grateful. :) 

Many thanks in advance!

---

### Post by gwpritch on 2007-02-01
What files did you edit?
There should be no problem with writing to fat32 partion, I have been doing it forever without any troubles.
This is probably a stupid question but has to be asked....are you sure its fat32 and not NTFS.

---

### Post by Sef on 2007-02-01
> I want to change files directly under the windows Xp partition (one can await or
trust, that linux have no problems with FAT32, isn't it?)

Yes, Linux and Windows can both write to FAT32.   It is most likely that your XP partition is NTFS, and Linux can't write to that without special software that is still beta.

---

### Post by FrancisA on 2007-02-01
> **Sef said:**
> Yes, Linux and Windows can both write to FAT32.   It is most likely that your XP partition is NTFS, and Linux can't write to that without special software that is still beta.
Thank you for replying, It is definitly FAT32. Strange. I will try again that evening.

---

### Post by FrancisA on 2007-02-01
> **FrancisA said:**
> Thank you for replying, It is definitly FAT32. Strange. I will try again that evening.

I checked again, today it is working (?)

could it be that before, I choosed not standby, but real shutdown.

BTW: I cannot copy files with ascii higher than 127 from winxp to ubuntu partition,
that means, i can copy but the german umlauts äöü and strong ß is corrupted.

Can I adjust something for that?

Thanks again!

---

