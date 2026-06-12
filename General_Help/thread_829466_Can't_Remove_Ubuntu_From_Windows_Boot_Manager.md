---
title: "Can't Remove Ubuntu From Windows Boot Manager"
date: 2008-06-14
forum: General Help
---

### Post by Miker1012 on 2008-06-14
I uninstalled Ubuntu earlier but in the boot manager, Ubuntu is still there. It won't run, but how do I remove it? I run Windows Vista( :( ). Thanks.

---

### Post by meierfra. on 2008-06-14
Get EasyBCD (see signature).  EasyBCD is a GUI for the  Visa Boot Loader.

---

### Post by chex_m8 on 2008-06-14
did you try removing it from your boot.ini file.

---

### Post by meierfra. on 2008-06-14
> did you try removing it from your boot.ini file.

Vista does not have a "boot.ini".

---

### Post by jason.tx on 2009-01-11
I am fairly new to Ubuntu myself and so I installed Ubuntu on to my Vista computer and removed it incorrectly.  Naively I thought if I install it again I could remove it correctly and remove it from Window Boot Manager, not the case.  After several Ubuntu and Window forums I found this way to remove Ubuntu (or any OS from the Windows Boot Manager) from the Windows Boot Manager without additional software.

- Click start
- Type: cmd
- Right-click cmd when it appears under Programs
- Click Run As Administrator

Once the prompt is up type bcdedit.exe
this will list all of the OS that start up in Windows Boot Manager

Once you have this list you use the command bcdedit.exe/delete *file name* 
example: bcdedit.exe/delete {802d5e32-0784-11da-bd33-000476eba25f}


I believe in giving credit where it is due so here are the links I used:

To open cmd prompt as an administrator in Vista
[http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html](http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html)

To remove an OS from Windows Boot Manager
[http://technet.microsoft.com/en-us/library/cc721886.aspx](http://technet.microsoft.com/en-us/library/cc721886.aspx)

---

### Post by yacine on 2009-03-04
Thanks. Very helpful. It solved my problem too!

---

### Post by scrooge_74 on 2009-03-04
Mark this as solve, so others can benefit

---

### Post by s.banks on 2009-05-09
> **jason.tx said:**
> I am fairly new to Ubuntu myself and so I installed Ubuntu on to my Vista computer and removed it incorrectly.  Naively I thought if I install it again I could remove it correctly and remove it from Window Boot Manager, not the case.  After several Ubuntu and Window forums I found this way to remove Ubuntu (or any OS from the Windows Boot Manager) from the Windows Boot Manager without additional software.

- Click start
- Type: cmd
- Right-click cmd when it appears under Programs
- Click Run As Administrator

Once the prompt is up type bcdedit.exe
this will list all of the OS that start up in Windows Boot Manager

Once you have this list you use the command bcdedit.exe/delete *file name* 
example: bcdedit.exe/delete {802d5e32-0784-11da-bd33-000476eba25f}


I believe in giving credit where it is due so here are the links I used:

To open cmd prompt as an administrator in Vista
[http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html](http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html)

To remove an OS from Windows Boot Manager
[http://technet.microsoft.com/en-us/library/cc721886.aspx](http://technet.microsoft.com/en-us/library/cc721886.aspx)


Excellent! It worked like a charm on Windows 7.

---

### Post by nagarjun16 on 2009-07-21
Excellent! It worked like a charm on vista

---

### Post by rob22941 on 2010-05-04
> **jason.tx said:**
> I am fairly new to Ubuntu myself and so I installed Ubuntu on to my Vista computer and removed it incorrectly.  Naively I thought if I install it again I could remove it correctly and remove it from Window Boot Manager, not the case.  After several Ubuntu and Window forums I found this way to remove Ubuntu (or any OS from the Windows Boot Manager) from the Windows Boot Manager without additional software.

- Click start
- Type: cmd
- Right-click cmd when it appears under Programs
- Click Run As Administrator

Once the prompt is up type bcdedit.exe
this will list all of the OS that start up in Windows Boot Manager

Once you have this list you use the command bcdedit.exe/delete *file name* 
example: bcdedit.exe/delete {802d5e32-0784-11da-bd33-000476eba25f}


I believe in giving credit where it is due so here are the links I used:

To open cmd prompt as an administrator in Vista
[http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html](http://www.vistax64.com/vista-account-administration/10743-bcdedit-exe-access-denied.html)

To remove an OS from Windows Boot Manager
[http://technet.microsoft.com/en-us/library/cc721886.aspx](http://technet.microsoft.com/en-us/library/cc721886.aspx)

I'm saving this thread thanks. Worked for me.

---

### Post by joefisherman on 2010-12-10
Thanks a bunch!  Worked for me as well.:D

---

### Post by asr050806 on 2010-12-13
I've installed Ubuntu onto an external hdd and now I can't get back into win 7 on my internal hdd. I can open Ubuntu and see the bcdedit.exe file but I can't open it to edit it!
Does anyone have any solutions???

---

