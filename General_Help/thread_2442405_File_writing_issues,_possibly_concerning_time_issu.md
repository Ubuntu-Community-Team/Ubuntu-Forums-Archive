---
title: "File writing issues, possibly concerning time issue"
date: 2020-05-03
forum: General Help
---

### Post by silverzephyr42 on 2020-05-03
I am attempting to rename some files in the System32 folder of my Windows 10 PC using a bootable Ubuntu USB drive. I have done this with no issues on other computers with this USB, however I am unable to rename on my current PC. I do not think it is Windows Fast Boot as I have seen suggested as a cause of this, as it would appear to be off. I have seen time discrepancies as another cause, and I have noticed when I boot into Ubuntu it sets my clock 2 hours forward. Windows corrects this when I boot back into it, but how do I fix this if this is indeed the cause? (Note: I am not an administrator on my PC, bear that in mind with solutions)

---

### Post by CelticWarrior on 2020-05-03
Welcome.

It's Windows Fast Startup (Fast Boot is a firmware, UEFI, feature) and yes, it is likely ON. Also you probably shouldn't be changing Windows system files from another OS. In many cases it makes Windows unbootable and requiring repair.

Regarding the time difference when dual-booting it has been explained in many places and neither is correct, it's a matter of definitions: [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
There you can find two solutions but apply only one in either Windows or Ubuntu. I prefer changing Windows.

---

### Post by silverzephyr42 on 2020-05-03
I've checked the control panel settings though and fast startup is not checked. Are you absolutely certain it's fast startup?

---

### Post by CelticWarrior on 2020-05-03
> **silverzephyr42 said:**
> I've checked the control panel settings though and fast startup is not checked. Are you absolutely certain it's fast startup?

No, I'm not certain and for reasons already expressed I won't be helping you with something you shouldn't be doing under no circumstances.
If you want help with Ubuntu ask away. If you want help with Windows please find a Windows centric forum. Ubuntu is NOT a repair tool for Windows.

---

### Post by Mark Phelps on 2020-05-03
@CelticWarrior is correct -- you should NOT be messing with files in the Windows folder from Linux.  That is a sure-fire way to corrupt the OS and render it unbootable.

If you're having a problem with clock settings, then open a thread for THAT and folks will respond to that.  There are changes you can make in Ubuntu that will get the clocks to tell the same time -- without hacking Windows system files.

---

### Post by Impavidus on 2020-05-03
> **silverzephyr42 said:**
> I am attempting to rename some files in the System32 folder of my Windows 10 PC using a bootable Ubuntu USB drive.
...
(Note: I am not an administrator on my PC, bear that in mind with solutions)

So you attempt to use an Ubuntu live disk (where you are the admin) to change things in Windows, as you can't do that in Windows because you're not the admin? Sounds like a hacking attempt, i.e., not supported by this forum. I suggest you contact your admin.

---

### Post by wildmanne39 on 2020-05-03
We do not support this kind of activity on the forum, clearly if the owner of the computer wanted you to make changes that only an admin can make they would have given you admin privileges, not to mention as already stated this is a good way to break windows.
> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalized with infractions and warnings.
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
Thread closed.

---

