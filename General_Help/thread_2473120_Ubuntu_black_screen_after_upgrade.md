---
title: "Ubuntu black screen after upgrade"
date: 2022-03-24
forum: General Help
---

### Post by Somebi on 2022-03-24
Not booting and stuck with black screen. Can't open terminal with ctrl+shift+1 to 7. On the 7th screen it is showing something related to recovering journal etc.
I have dual boot and same hard drives are used for Windows, no problems there at all, Windows 11 is booting fine and working as always.
Before upgrade, system was working flawlessly.

One thing i have learned for sure. NEVER UPGRADE THE DAMN UBUNTU!!! It is always breaking OS. 
Seriously guys, it's a total fail. If it would at least let me get to the terminal...
Now i need to make recovery USB and try to repair Ubuntu...

---

### Post by Somebi on 2022-03-24
Upgrading from 20.04 to 21.10 if you are curious.

---

### Post by Somebi on 2022-03-24
Ok, after some investigation. It seems that assembled/built kernel is not working. Malfunctioning version 5.13.0-38-generic and when switching to 5.11.0-50-generic it is booting without problems.

---

### Post by grahammechanical on 2022-03-25
I do not understand why you would want to upgrade Ubuntu 20.04 to Ubuntu  21.10 when Ubuntu 21.10 reaches end of life support July 2022. My  install of Ubuntu.20.04.4 has the Linux 5.13.37 kernel and has been  using the 5.13 kernel for some months. I do not see any advantage to  upgrading to 21.10 this late in its life support period. Especially,  when 20.04 has caught up with any improvements that came with 21.10.

Did the online upgrade to 21.10 succeed, even imperfectly? 

When it comes to online upgrades there are certain precautions we all must take.

1) Backup important data.

2) Revert the desktop back to its default consideration.

3) Disable any PPA's.

4) Become familiar with Grub Advanced Options for Ubuntu>Alternate kernels and Recovery mode.

There  may be other precautions that some others might wish to offer. I know  some of us will recommend doing a fresh install. Right now you might  wish to continue booting into the 5.11 kernel and running the normal  update/upgrade process. It may just fix the 5.13.38 kernel.

Regards

---

