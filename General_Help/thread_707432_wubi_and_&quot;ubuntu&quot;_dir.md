---
title: "wubi and &quot;ubuntu&quot; dir"
date: 2008-02-25
forum: General Help
---

### Post by Oxpa on 2008-02-25
i had a directory named "ubuntu" in my hard drive. There was not only ubuntu iso's, but some more information (about 30 GB). I used wubi, everything was OK. The problem was, when i wanted to uninstall wubi, it removed the "ubuntu" dir... 

May be wubi should check if there already an "ubuntu" dir?)

---

### Post by ago on 2008-02-25
> **Oxpa said:**
> i had a directory named "ubuntu" in my hard drive. There was not only ubuntu iso's, but some more information (about 30 GB). I used wubi, everything was OK. The problem was, when i wanted to uninstall wubi, it removed the "ubuntu" dir... 

May be wubi should check if there already an "ubuntu" dir?)

Good point, sorry for any incovenience. It will be taken care of.

---

### Post by ago on 2008-02-25
[https://bugs.launchpad.net/wubi/+bug/195489](https://bugs.launchpad.net/wubi/+bug/195489)

---

### Post by ago on 2008-02-25
I have gone through the code, I think what happens when a folder called "ubuntu" already exists is that it is still used for the installation but the existing files should not be deleted.

They will be deleted though if subsequently you uninstall Wubi. 

Is that what happened to you?

---

### Post by Oxpa on 2008-02-25
yes, it is exatly my problem=)

mmm... ok, by steps:

There are 3 hds installed in my PC. They are C:(system), E: and ReiserFS drive for some unises.
In E;\ubuntu were: ubuntu iso's, kubuntu iso's, SLES, SLED, BSD, Solaris and some utils like winISO, hp format utility for flash drives, etc. (some iso's were unpacked into subfolders)

I downloaded ubuntu iso to the "E:\ubuntu" folder.
Unpacked it into" E:\ubuntu\ubuntu-7.10-desktop-i386" folder
Saw a wubi exe file, and launched it ( it's always the same with me: click then repair=) ), it told me there is no proper cd disk or something like that.
I mounted iso with Alchohol, launched wubi again, it installed some files and ask me to reboot.
I rebootted, nothing happend at boot, but when Windows launched wubi told, that ubuntu had already been installed. It asked me, if i want to unisntall wubi, i answered YES, then it deleted whole folder.

That's all=)

PS sorry, for my english, if smth.

---

### Post by ago on 2008-02-25
Do you have vista (that's another bug relating to modifying the vista bootloader when permission escalation is required)?

"it told me there is no proper cd disk or something like that." 
Can you provide me with the exact msg, or better with the wubi log? It's in your temp folder (type %temp% in windows explorer) .

---

### Post by Oxpa on 2008-02-25
i have XP installed.
 i'll post here the log tommorow. 
There is no wubi file or  log at this time. But i'll repeat everything=)

---

### Post by Oxpa on 2008-02-25
> **ago said:**
> Good point, sorry for any incovenience. It will be taken care of.
never mind, i accidentally formatted all the 320GB drive into reiserfs then... So i'm restoring all the data in any way)) (i can't even believe i didnt check the data before formatting!!!)

---

