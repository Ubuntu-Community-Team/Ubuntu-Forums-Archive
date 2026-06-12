---
title: "Problems with booting Windows and grub."
date: 2015-10-26
forum: General Help
---

### Post by matias18 on 2015-10-26
I have this problem, first i installed windows 7, later ubuntu 14 and in this instance i lost the grub

I do this:

sudo grub-mkconfig -o /boot/grub/grub.cfg

later:

sudo reboot

and when i select "windows 7 (loader)" i see the black screen only.

how can i fix it?

---

### Post by Vladlenin5000 on 2015-10-26
Hi and welcome.

First of all please explain why you did what you did, what were you trying top achieve, etc. Then somehow might have an idea.

---

### Post by matias18 on 2015-10-26
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732")sorry vladlenin500, i post the question in other thread and one moderator move here. i update the question

---

### Post by Vladlenin5000 on 2015-10-26
Of course it was moved and FYI I was the one to report it in the first place. Thread hijacking isn't the way to ask for help.

---

### Post by matias18 on 2015-10-26
Look, it was not on purpose , I thought it was related to my problem , why he had installed both operating systems and had problems with the grub, I assumed it was a related problem

---

### Post by Vladlenin5000 on 2015-10-26
I didn't said nor even implied it was.
Still waiting for relevant informations though. This back and forth isn't conducive to a solution either.

---

### Post by matias18 on 2015-10-26
there are the information, i install first the windows 7, after that, i install ubuntu, i lost the grub, i reconfigure the grub and now i see the windows 7 but when i select it, i see only a black screen. its all

here the fdisk results

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   977120255   488200704    7  HPFS/NTFS/exFAT
/dev/sda3       977121278  1953523711   488201217    5  Extendida
La partición 3 no se inició en el limite físico del sector
/dev/sda5       977121280  1937010687   479944704   83  Linux
/dev/sda6      1937012736  1953523711     8255488   82  Linux swap / Solaris

---

### Post by Vladlenin5000 on 2015-10-26
Can you please explain what you mean by "I lost GRUB"??
If you were able to boot Ubuntu then you certainly didn't. And if it booted _directly_ to Ubuntu that just means the Windows installation wasn't "seen" by the installer. The reason for that is most likely the Windows partition being hibernated or in bad shape during the Ubuntu installation.

Did you format the NTFS partition(s) before installing Windows or manually during the Windows installation, leaving unallocated space for Ubuntu?
Or did you let the Windows simply take over the entire disk and later shrink the partition to make room for Ubuntu? If so, how and with what tool? Did you run CHKDSK after shrinking? And, of course. have ypu confirmed the Windows was booting before installing Ubuntu?

---

### Post by matias18 on 2015-10-26
with "i lost grub" i mean what i dont see the "windows 7 (loader)" option

when i install first windows 7 i use all the disk and when i install ubuntu i choose make 2 partitions with 499 GB each, after that i don't do nothing new

---

### Post by Vladlenin5000 on 2015-10-26
> **matias18 said:**
> when i install first windows 7 i use all the disk and when i install ubuntu i choose make 2 partitions with 499 GB each, after that i don't do nothing new

So you must have shrink the Windows partition unless, of course, you installed Ubuntu in a different drive. Assuming it is the same drive you must have resized (shrink) ate some point. I asked precisely HOW and with WHAT TOOL? And I also asked whether or not you're able to boot Windows after the partition change and BEFORE installing Ubuntu?

To be honest, I'm just asking for confirmation because I have a pretty good idea about what happened...

---

### Post by matias18 on 2015-10-26
i dont use any particular tool, when i install ubuntu askme for made the partition

and im unable to boot windows after install ubuntu

---

### Post by Vladlenin5000 on 2015-10-26
> **matias18 said:**
> i dont use any particular tool, when i install ubuntu askme for made the partition

Confirmed indeed. That's exactly what you did wrong (as expected).

ALWAYS resize Windows partitions with Windows tools. The native tool is fine.
After shrinking ALWAYS run the error correction tool (again a Windows native tool - chkdsk).
Then, after assuring Windows boots correctly with its newly resized partition, you can proceed to install Ubuntu (or anything else for that matter) in dual boot.

Doing otherwise often results in exactly what you experienced. And there's no way top correct it from Ubuntu. Windows 7 and newer are all very "sensitive" about their system partitions. Shrinking with the partitioning tool included in the Ubuntu installer might have worked in the past with XP but even then it was a russian roulette.
_Now you need to reinstall Windows_ and do it right this time (read above). The Windows installer also lets you create the system partition with a specific size. Doing that is obviously preferable; as soon as you confirm the Windows is booting fine you can proceed with dual boot installation with Ubuntu or anything else for that matter.

Last but not least, ask yourself if you really need Windows. You most certainly don't.

---

### Post by matias18 on 2015-10-26
i simply change the priority to boot and set hard disk and now works, is not necessary reinstall nothing, thanks

---

