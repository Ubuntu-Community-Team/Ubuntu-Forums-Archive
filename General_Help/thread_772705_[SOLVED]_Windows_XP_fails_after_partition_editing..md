---
title: "[SOLVED] Windows XP fails after partition editing. HELP"
date: 2008-04-28
forum: General Help
---

### Post by werries on 2008-04-28
So first.
I edited some partitions, i have a Dell XPS M1210 laptop. I installed Ubuntu 7.10 back in the day, and dual booted Windows XP Media Center and Ubuntu perfectly fine. I updated to 8.04 recently. then I decided I didn't require DellUtility or MEDIADIRECT partitions. Deleted, and increased the ext3 and NTFS partitions to fill. Reboot, and nothing works. After some work, I backed up my files from both partitions using the LiveCD. I reinstalled hardy heron and it worked fine.

However, Windows would not boot with grab. it said Grub Error 22. So, I ran the recovery console, fixed master boot, did fixboot c:, and then reinstalled grub using livecd. sweet. Then it gave me a hal.dll corruption error. So i downloaded the registry file and placed it in my system32 folder with ubuntu. Still, no boot. I then found out you can't just put it in there and so i had issues, i was given Error 12 by Grub, Invalid Device Request.

So, after much frustration, had all windows documents backed up to an external, I reinstalled using my dell disk. Windows XP booted up fine, however...everything was gone. It wouldn't even detect my wireless card, no drivers for it. So, pissed, I want to boot back into ubuntu, but had to put grub back. so used the livecd, put it on (hd0,5) cause that was the return from find /boot/grub/stage1.  Now, however, It still gives me the error 12: invalid device requested. So not only is my windows xp not booting properly, i had reinstalled it and all my settings and applications were deleted.

I need Windows for my Zune. I need it for webcam support for AIM as pidgin has none. And i need it for Visual C++ compatibility with my programming class, as I sometimes need the windows.h header, along with support for integer to character transfers, as I cannot seem to just do a "cout << (char)254; ", but maybe thats extended ASCII problems. 

So essentially, I need Windows to boot and get internet, and then I can fix it myself. I am only somewhat computer savvy, and know basic Linux stuff. But don't assume I know how to do certain things. Please help! I'm really frustrated.

---

### Post by werries on 2008-04-28
solved. my /boot/grub/menu.lst was pointing to the wrong partition, as (hd0,1) did not have anything on it anymore. (hd0,0) was now the windows partition.
installing drivers once more.

---

