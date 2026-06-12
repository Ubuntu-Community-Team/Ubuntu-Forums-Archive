---
title: "very strange grub issue (partition # changed)"
date: 2007-05-20
forum: General Help
---

### Post by mrweirdo on 2007-05-20
this is a strange one. We recently had our house get painted so I had to shut my dell poweredge server down and moved it to another room temporally for a day. Well the next day when I put it back and tried to boot up ubuntu linux 6.06 LTS. I got this error message during grub bootup:

file not found error 15:

After some investigation it looked like it couldn't find the link to vmlinuz so I entered the grub comand option and issued a **find /vmulinuz** and it found my boot partition at **root (hd2,0)**. Afterwords i went to edit the grub startup options temporarily and noticed that the boot partition used to be **root (hd0,0)**.

 Does anyone know why the partition would suddenly change numbers out of the blue? all I did was turn the computer off. Hardware wise it hasn't changed at all since before I installed ubuntu which also happens to be the only os installed.  Just to note I have two SCSI ultra 320 73gb maxtor drives in there.

Again does anyone know what might cause this? has anyone experienced similar issues?

---

### Post by m.musashi on 2007-05-20
Usually, drive numbers only change when you make changes in the BIOS or the physical connections to the motherboard. Since you moved the computer recently, any chance one of the drive cables came loose?

---

### Post by mbradlcu on 2007-05-20
I had this happen after an apt-get upgrade,, I'm sure I didn't change anything in the bios although it could have changed... it also happened again after upgrading to 7.04,,,

---

