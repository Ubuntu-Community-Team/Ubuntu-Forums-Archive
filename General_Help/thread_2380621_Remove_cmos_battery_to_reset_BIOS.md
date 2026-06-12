---
title: "Remove cmos battery to reset BIOS?"
date: 2017-12-19
forum: General Help
---

### Post by MibunoOokami on 2017-12-19
Hi all, I need to get into BIOS to get a computer to boot with efi. The owner didn't know a password was set for BIOS. I've read online you can remove the cmos battery which will remove the password, I'm skeptical about this and don't want to spend time opening a machine only to find this doesn't work or worse something goes wrong. 

Has anyone tried this with success? Possible other way of successfully getting into password protected BIOS?

Thanks in advance

---

### Post by Frogs Hair on 2017-12-19
[SIZE=2]Procedures may differ depending on brand , so look for info for the specific model. I'm [COLOR=#000000]skeptical of battery removal too though removing reseting the battery has never caused any problems for me. Setting a bios password on my computer requires security questions so I would remember having done it. [/COLOR][/SIZE]

---

### Post by leunam12 on 2017-12-20
I don't think removing the battery will get rid of the password, there are usually two solder points that you have to short with a metal object like a paper clip and sometimes it takes a lot of tries before you can actually clear the password. It all depends on the manufacturer and you have to find specific information for your computer brand

---

### Post by Autodave on 2017-12-20
Google it: give make and model of computer and you will likely find it online.

---

### Post by MibunoOokami on 2017-12-20
> **Autodave said:**
> Google it: give make and model of computer and you will likely find it online.

Dr Google originally said what I put in the OP. 

However I've been doing extensive searching before, during and after posting this, says the only way around the problem will be by using a checksum when I enter an incorrect password three times. Only the machine in question won't provide a checksum.

---

### Post by MibunoOokami on 2017-12-20
Bit the bullet, pulled machine apart, removed the CMOS battery and swapped the BIOS jumper and the password has been disabled. Not sure which of the two worked, perhaps a combination of the two, whichever it was this was the solution. 

Thanks for the advice, I hope this info might help others in the future. 

FWIW I had also tried in the neighbourhood of 25 different so called backdoor passwords for BIOS with no success.

---

### Post by raleigh3 on 2017-12-20
Glad you got it fixed. :-)

---

