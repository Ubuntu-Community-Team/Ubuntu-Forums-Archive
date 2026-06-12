---
title: "K3B crashes on Verify Written Data / How to debug it?"
date: 2008-02-23
forum: General Help
---

### Post by kung fu buntu on 2008-02-23
Unfortunately for me K3B crashes on the Verify Written Data step.

I have tried the "do not eject media" tip, both checked and unchecked and it fails miserably at both settings.
I have also tried enabling all those features for joliet and iso9660, but to no avail. Besides, it also crashes for UDF systems.

Right now I have to resort to kdiff3 to check if the media was burnt properly! :mad:

If anyone knows how do I fix this, please do tell me, otherwise enlighten me on how to debug it.


I have been able to build K3B from source, but don't know how to debug it.
I used Kdevelop and import the directory as a KDE C++ project. 
But when I press F9 it tells me: 
-------------- 
Debugger error 
Debugger reported the following error: 
No executable file specified. Use the "file" or "exec-file" command. 

Debugger error 
Debugger reported the following error: 
No registers. 
-------------- 
And I've set the executable in Run Options project menu.


Any help?
Thank you.

---

### Post by Dr.Ninethousand on 2008-03-09
I have the same problem about 8 out of 10 times..  any help?.     :(

---

### Post by Oldsoldier2003 on 2008-03-09
> **kung fu buntu said:**
> Unfortunately for me K3B crashes on the Verify Written Data step.

I have tried the "do not eject media" tip, both checked and unchecked and it fails miserably at both settings.
I have also tried enabling all those features for joliet and iso9660, but to no avail. Besides, it also crashes for UDF systems.

Right now I have to resort to kdiff3 to check if the media was burnt properly! :mad:

If anyone knows how do I fix this, please do tell me, otherwise enlighten me on how to debug it.


I have been able to build K3B from source, but don't know how to debug it.
I used Kdevelop and import the directory as a KDE C++ project. 
But when I press F9 it tells me: 
-------------- 
Debugger error 
Debugger reported the following error: 
No executable file specified. Use the "file" or "exec-file" command. 

Debugger error 
Debugger reported the following error: 
No registers. 
-------------- 
And I've set the executable in Run Options project menu.


Any help?
Thank you.
useful links:
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

[https://wiki.ubuntu.com/Strace](https://wiki.ubuntu.com/Strace)

[https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

---

