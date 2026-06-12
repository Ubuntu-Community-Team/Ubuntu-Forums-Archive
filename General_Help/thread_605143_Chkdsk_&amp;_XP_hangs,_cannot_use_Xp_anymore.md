---
title: "Chkdsk &amp; XP hangs, cannot use Xp anymore"
date: 2007-11-06
forum: General Help
---

### Post by melden on 2007-11-06
Hi all,

I'm having a huge problem. XP doesn't start anymore. (Yeah, not really a "huge" prob, except that ubuntu doesn't detect my printer/scanner anymore since upgrading to 7.10 and of course I still have a few games/progs XP only. :( So I cannot fully switch to ubuntu for now..) Once XP asked to chkdsk but it eventually froze at the end.

Anyway, I have an idea of where the problem is after days of googling (I'm still a complete n00b...). I have several ntfs partitions mounted and been copying stuff on them regularly. One day my partitions disappeared and I couldn't boot xp. I then used ntfsfix and that fixed the problem mounting the partitions back in ubuntu. However xp still won't start..

Please, any help would be greatly appreciated...  I'm at a complete loss!

Thanks,

melden

P.S. anyone know how to copy files onto nfts partitions without getting that kind of error from xp?

---

### Post by Zackariah on 2007-11-07
What don't you mean by XP won't start anymore ?
Does GRUB list it at all ?

Please give a little bit more info.

---

### Post by melden on 2007-11-07
Sorry, English isn't my first language.

Yes GRUB lists it as Other OS. XP starts with the usual progress bar and then I get a black screen, it just hangs there. I once got into ChkDsk (think it was after the ntfsfix), it scanned all my partitions but stopped responding after it said the computer will restart. Then the same thing happened again; I got the black screen as before.

Thanks for the reply!

---

### Post by Moh Kohn on 2007-11-08
I have pretty much the same problem.

I am a newb to linux/ubuntu, installed 7.04 and upgraded to 7.10.  Now xp wont load, it shows as other os in the grub menu but as OP it hangs after standard loading screen it just hangs.  My ntfs partitions are now no longer visable in ubuntu if I try to enable write function on them, with ntfs configuration tool, it gives an error message saying windows has locked them.

---

### Post by melden on 2007-11-08
Moh Kohn,
Have you tried the ntfsfix? I was able to remount the partitions back on ubuntu, but still no xp... My last resort would be to re-install/repair xp.

---

### Post by Moh Kohn on 2007-11-08
No I haven't tried that yet, I was more concerned at xp not loading than anything else so I will try when I get home from work.

---

### Post by melden on 2007-11-10
Update:
I still cannot get into XP. I tried loading the XP cd at startup to "repair" it. Setup loads the files, but hangs after that, I don't even get to the EULA where it asks to press F8. 

When I go to ubuntu, all my partitions are gone again (XP apparently is messing with them during chkdsk) and I have to use ntfsfix to get them remounted. That way, I was able to backup my XP folders.

So anyone has any suggestions? How can I install XP again? Is it possible to do it via ubuntu?

Thanks!

---

