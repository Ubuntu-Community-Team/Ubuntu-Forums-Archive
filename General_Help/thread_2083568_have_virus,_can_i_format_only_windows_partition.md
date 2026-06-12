---
title: "have virus, can i format only windows partition?"
date: 2012-11-13
forum: General Help
---

### Post by jinjin on 2012-11-13
ok i run dual boot ubuntu and widows xp  i just got a virus on my windows xp.  is it possible to format only the windows xp partition leave the ubuntu intact and still have it work in a dual boot?  previously, when i had a virus on my xp, i would format the whole drive and reinstall both ubuntu and windows xp and reconfigure everything and that was a pain in the butt since ubuntu was perfectly fine  and i still had to reinstall programs, move files and take care of system even though it didn't have the virus.


so this time, can i just reformat windows xp partition, reinstall xp and programs and still have it work on dual boot?  people told me that doing this will mess up the MBR and stuff.  i don't know anything about that so can anyone tell me how this works?

i need help badly

---

### Post by dFlyer on 2012-11-13
You should be able to. You will have to run grub after the install to pick up the windows install.

---

### Post by uRock on 2012-11-13
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) should get you back up and running after reinstalling Windows. Your anti-virus software can't remove the malware?

---

### Post by sentimentGX4 on 2012-11-13
Yes, you can. After reinstalling Windows, the Windows bootloader will be installed and you will not be able to directly boot into your Ubuntu. Use a LiveUSB (or other Live Media) to boot into Ubuntu and reinstall Grub by typing commands into the terminal.

---

### Post by jinjin on 2012-11-13
thanks alot, i love the ubunutu community :D so knowledgeable and helpful :D and this virus is too much so using malware scanners and combfix, rkill, etc didn't help much.  


actually i have another question, there is no way for this virus to someone spread from my windows xp partition and affect ubuntu partition right?

---

### Post by uRock on 2012-11-13
> **jinjin said:**
> there is no way for this virus to someone spread from my windows xp partition and affect ubuntu partition right?

Nope, Windows can't see the EXT partition being used by Ubuntu.

---

### Post by carl4926 on 2012-11-13
> **jinjin said:**
> 


actually i have another question, there is no way for this virus to someone spread from my windows xp partition and affect ubuntu partition right?
In short No

---

