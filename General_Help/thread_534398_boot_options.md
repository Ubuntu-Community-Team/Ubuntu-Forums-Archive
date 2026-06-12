---
title: "boot options"
date: 2007-08-25
forum: General Help
---

### Post by neojags on 2007-08-25
hi,
I am a newbie. i have recently installed ubuntu 7.04 amd 64. the entire process went  on well and it gave a message that the installation was done. 
I kept winxp and ubuntu on the same hard disk. 
When i rebooted as per the requirement. i did not get any boot options and the comp directly goes to win xp. 

what might be the problem? please help

jags

---

### Post by jamvegan on 2007-08-25
I cannot recall exactly what questions the Ubuntu installer asks these days.  Do you recall being asked either of the following?

Would you like to install the GRUB bootloader to the MBR (master boot record)?

Which operating system would you like to boot by default?

If so, what did you answer?

---

### Post by meierfra on 2007-08-25
Boot from the live cd, open a terminal (Applications->Accessories->Terminal)

type 

```
 sudo fdisk -l  
```
(the l is a lower case L)
hit enter and post the output.

This will tell us whether ubuntu got installed.

---

### Post by Majorix on 2007-08-25
Did you install windows after ubuntu?

---

