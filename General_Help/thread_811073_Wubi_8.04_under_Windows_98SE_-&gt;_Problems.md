---
title: "Wubi 8.04 under Windows 98SE -&gt; Problems"
date: 2008-05-28
forum: General Help
---

### Post by Mulderx on 2008-05-28
I used Wubi 8.04 to install Kubuntu under Windows 98SE this is all I got:

```
WUBI caused an invalid page fault in
module METADL.DLL at 0167:6869c141.
Registers:
EAX=7803b670 CS=0167 EIP=6869c141 EFLGS=00010202
EBX=00000011 SS=016f ESP=018eab80 EBP=018eaba4
ECX=007b92d0 DS=016f ESI=006a4240 FS=349f
EDX=007b9620 ES=016f EDI=007b92a0 GS=18e6
Bytes at CS:EIP:
8b 03 50 ff 15 14 10 6c 68 89 1c 24 ff 15 14 10 
Stack dump:
00000018 00000000 00000000 00000000 0000d4c0 018eabb4 007b9620 006a4240 00000000 018eabd4 6868b8a2 007b9620 00000016 00000000 007b92d0 00000001 
```

All I have from this install is a boot loader that is useless. Worse, I could not remove it.

---

### Post by inportb on 2008-05-28
I'm not sure if Win9x even does Wubi. AFAIK, Wubi uses the NT loader to loop-mount an image and boot from it.
(I could be wrong, though.)

### EDIT ###
Yep, I am. Wubi advertises that it works with Win98. Hm. I don't know, then.

---

### Post by tinybit on 2008-05-28
Try once more and start the installation in safe mode of the win98 desktop. Also you may try to install in "safe mode command prompt only".

---

### Post by Mulderx on 2008-05-29
@ inportb,
Yes, they say it works, but they add it was not tested tough... what a shame!

@ tinybit,
Thanks, but I will assuringly not retry installing with Wubi anymor.

Wubi requires a connection to Ubuntu's server to make an iso checkup,using md5 values that already are stored in the iso file itself... where's the point?

I had checked the iso integrity right after I downloaded it from Ubuntu and I wanted to try it on a PC that does not connect to the Web... it failled connecting, thus aborted install.

Then I tried on a second machine and all I got is a sore taste in my throat.

I will partition **/boot** in ext2 ; **/** in ReiserFS ; and **swap** in Linux Swap ; and install Kubuntu directly (without a crappy installer that should be labelled as *Beta*.)

---

### Post by Dave2k6 on 2008-05-29
To remove items from boot menu, edit the c:\boot.ini file and remove the Ubuntu line

---

