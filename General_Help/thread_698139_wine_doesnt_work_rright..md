---
title: "wine doesnt work rright."
date: 2008-02-15
forum: General Help
---

### Post by girtart3d on 2008-02-15
i installed wine. but when i start an .exe file it says it cant find a hard disk location to store temporary files. and when i run winecfg i get 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
is there a fix for this?

---

### Post by randy78 on 2008-02-15
> **girtart3d said:**
> i installed wine. but when i start an .exe file it says it cant find a hard disk location to store temporary files. and when i run winecfg i get 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
is there a fix for this?

Try this

Open a terminal and type:
winecfg

Then, once the configuration dialog opens, select Drives
Click the AutoDetect button
Click Apply
Finally, click OK

Just be careful about this, because it will give Wine access to your entire system...
I always just give it access to my /home/ drive, then remove everything else except for C:

Good luck ;)

EDIT: Maybe I misunderstood, but are you saying that Wine doesn't come up at all from winecfg?

---

### Post by girtart3d on 2008-02-15
i think it fixed one of the problems. but now it says
unable to create a temporary file. Setup Aborted
error 3:path not found.

---

### Post by randy78 on 2008-02-16
> **girtart3d said:**
> i think it fixed one of the problems. but now it says
unable to create a temporary file. Setup Aborted
error 3:path not found.

Copy and paste the exact text of the error message so we can see what's going on ;)

---

### Post by girtart3d on 2008-02-16
well i cant copy and paste it because its on an error box. but it says
c:/windows/system 32
There was a problem creating this folder.
The installation will be cancelled.
i set the installation path to /home/me , but i tried a bunch of different paths as well. nothing seems to work.

---

### Post by Darkade on 2008-02-16
> **girtart3d said:**
> well i cant copy and paste it because its on an error box. but it says
c:/windows/system 32
There was a problem creating this folder.
The installation will be cancelled.
i set the installation path to /home/me , but i tried a bunch of different paths as well. nothing seems to work.

Make sure to have read/write permissions in your ~/.wine folder. I know you having no permission to your own folder sounds silly but happens

---

