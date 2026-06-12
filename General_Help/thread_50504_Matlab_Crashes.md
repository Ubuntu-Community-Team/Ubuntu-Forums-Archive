---
title: "Matlab Crashes"
date: 2005-07-20
forum: General Help
---

### Post by mithion on 2005-07-20
I installed matlab R14 sp1 a few weeks ago and I have comme to notice a very annoying bug.  Everytime I paste something such as an equation, the program crashes.  Then, in the command console, the following message appears:  
[FONT=Lucida Console]
philippe@phil:~$ matlab
Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!                                            #Matlab is running at this point
X Error of failed request:  BadValue (integer parameter out of range for operation)   #Matlab has crashed at                                      this point
  Major opcode of failed request:  18 (X_ChangeProperty)
  Value in failed request:  0x4
  Serial number of failed request:  11049
  Current serial number in output stream:  11051
philippe@phil:~$
[/FONT]
Is this problem comming from linux itself, or is it an inherent flaw in matlab?  In the even of the former, what can be done to correct it?

---

### Post by mvandeg on 2005-07-20
The error:
```
Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!
```
is common, but I never had Matlab crashing, also with R14 SP1. Did you already look on [http://www.mathworks.com/support/](http://www.mathworks.com/support/)?

---

