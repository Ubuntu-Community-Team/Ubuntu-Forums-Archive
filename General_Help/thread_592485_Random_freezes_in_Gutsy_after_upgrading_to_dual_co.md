---
title: "Random freezes in Gutsy after upgrading to dual core Athlon 64"
date: 2007-10-26
forum: General Help
---

### Post by MegaSvensk on 2007-10-26
Hi,

I upgraded my CPU from an Athlon 64 3500+ to a dual core Athlon 64 4200+ and now I'm experiencing random freezes in Ubuntu. It freezes completely so that it's not even possible to restart X. It is not overheating because in Windows XP I completed a whole 3DMark test without any issues.


Does anyone have any idea what could be causing this problem and how to resolve it?

Thanks.

---

### Post by MegaSvensk on 2007-10-26
Bump.

---

### Post by MegaSvensk on 2007-10-26
Well, to hell with it. I'll just use Windows.

---

### Post by chrisccoulson on 2007-10-26
Can you give a more specific description of your hardware first? Chipset? Graphics?

Are you using proprietary drivers for any of the hardware?

Are you using the 64-bit version of Ubuntu?

What are you doing at the time of the freeze (ie, what applications are running etc), or are they totally random?

Are there any error messages in /var/log/syslog, /var/log/messages or /var/log/Xorg.0.log?

What is the output of dmesg?

Is this an upgraded system or fresh install?

Are you using Compiz? If so, what plugins?

Has the machine completely frozen or is it just X? If you have another machine handy, and they're both networked, you could try SSH'ing in to the crashed box to see if it still responds. I've had X crash before where the keyboard stops responding (preventing me from restarting X or switching to a terminal), giving the illusion that the machine has completely locked up, when it hasn't (I've been able to shell in to the box remotely)

You need to give more information, else people will not be able to help. With more information, you might get the attention of more people that may be able to help. And comments like 'Well, to hell with it. I'll just use Windows.' isn't going to make people help you any quicker. Patience! People volunteer to help out on here and we all have our own lives to live.

Also, do a search on the forums. I'm sure I've seen other threads about Gutsy freezes.

---

### Post by chrisccoulson on 2007-10-26
Quick search for 'Gutsy' and 'freeze':

[http://ubuntuforums.org/showthread.php?t=585714]("http://ubuntuforums.org/showthread.php?t=585714")

[http://ubuntuforums.org/showthread.php?t=587905]("http://ubuntuforums.org/showthread.php?t=587905")

[http://ubuntuforums.org/showthread.php?t=412125]("http://ubuntuforums.org/showthread.php?t=412125") (big thread from Feisty)

---

### Post by MegaSvensk on 2007-10-26
Thanks for replying.

OS: Ubuntu 7.10 i386
CPU: AMD Athon 64 X2 4200+
Motherboard: MSI K8N Neo2-54G (nForce 3 Ultra)
RAM: 2048 MB DDR 400
GPU: Asus Geforce 7600 GS 256 MB AGP

I used Gutsy for about a week before upgrading the CPU and it never froze up then. 
The freezes are completely random as far as I can tell. So far they've happened while surfing the webb, while editing a picture in gimp and while there were no applications running at all.

---

### Post by zippy028 on 2007-10-26
I have the same problem. 
Asus m2n SLI mobo
AMD 3800 64X2
1GB Corsair mem
SATA HD Western dig not sure of nomenclature
Nvidia 7300 LE using restricted driver provided with gutsy.

I had similar freezes with Feisty as well. I did not use Beryl or Compiz with feisty. I din't notice the freezes until using Nvidia driver in Feisty. I am not sure now with gutsy; Do I have to select no desktop effects or is normal using Metacity and not Compiz?

---

