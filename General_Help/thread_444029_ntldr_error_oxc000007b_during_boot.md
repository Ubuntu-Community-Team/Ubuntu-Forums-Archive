---
title: "ntldr error oxc000007b during boot"
date: 2007-05-15
forum: General Help
---

### Post by raybaron on 2007-05-15
I  have been trying to install minefield v 0.7 on my Gateway laptop. I am dual booting XP and Vista. XP is in the first partition and Vista on the second. The Wubi install went fine and the Ubuntu option appears in the boot menu but when I select Ubuntu I get an error c000007b \grldr no found. I looked in the root directory of c: and it's there. If grldr is in windows root why cant ntldr find it? The last line of my boot.ini file reads 
c:\grldr="Ubuntu"  (as set by the installer) I get into an endless loop if I keep picking Ubuntu from the windows start menu and have to hit ESC to finally get out of it.
 Linux is new to me- I have been a UNIX/SCO  user for 22 years and now that my new employer is running Linux I want to get up to speed on the o/s ASAP. I'ver been using Windows forever and tired of the bugs, viruses and bad system performance and crashes I get all of the time.

I'm really anxious about getting this running and need help. I'll hand it over to you guys :)

thx - Ray

---

### Post by ago on 2007-05-15
> **raybaron said:**
> I  have been trying to install minefield v 0.7 on my Gateway laptop. I am dual booting XP and Vista. XP is in the first partition and Vista on the second. The Wubi install went fine and the Ubuntu option appears in the boot menu but when I select Ubuntu I get an error c000007b \grldr no found. I looked in the root directory of c: and it's there. If grldr is in windows root why cant ntldr find it? The last line of my boot.ini file reads 
c:\grldr="Ubuntu"  (as set by the installer) I get into an endless loop if I keep picking Ubuntu from the windows start menu and have to hit ESC to finally get out of it.

I do not understand if grldr is not there how can you get into a loop? Anyway try to copy grldr and menu.lst to the other partitions as well.

---

### Post by tinybit on 2007-05-15
> **raybaron said:**
> I am dual booting XP and Vista.


Though I don't know why, I guess something unusual happened. For instance, if VISTA changed NTLDR and the new NTLDR might work differently.

As an alternative, you may instead try this way:

c:\grldr.mbr="ubuntu"

The grldr.mbr can be from the latest test releases of grub4dos.

---

