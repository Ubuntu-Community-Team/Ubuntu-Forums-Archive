---
title: "WINE: Edit System Variables on Headless Ubuntu"
date: 2014-05-15
forum: General Help
---

### Post by pat10 on 2014-05-15
Is there a way to edit system variables from terminal running WINE without GUI?

I'm running a headless Ubuntu as a continuous integration server and I have to run archaic builds which only works on Windows so I was hoping WINE could get me close to what I need.

Adding JAVA_HOME
```
Z:\var\lib\pat>reg add HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment /v JAVA_HOME /t REG_EXPAND_SZ /d "C:\Program Files (x86)\Java\jdk1.6.0_45" /f
```
returns 
```
Z:\var\lib\pat>reg add HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment /v JAVA_HOME /t REG_EXPAND_SZ /d "C:\Program Files (x86)\Jareg add HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment /v JAVA_HOME /t REG_EXPAND_SZ /d "C:\Program Files (x86)\Java\jdk1.6.0_45" /f
ADD - HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session JAVA_HOME 0 REG_EXPAND_SZ C:\Program Files (x86)\Java\jdk1.6.0_45 1
Unhandled Type 0x2  data C:\Program Files (x86)\Java\jdk1.6.0_45
The operation completed successfully
```
but after invoking
```
Z:\var\lib\pat>set
```
I don't see JAVA_HOME posted there.

Please advise which direction I need to go to. TIA!

---

