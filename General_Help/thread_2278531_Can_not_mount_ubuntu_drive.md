---
title: "Can not mount ubuntu drive"
date: 2015-05-17
forum: General Help
---

### Post by fmha on 2015-05-17
[COLOR=#000000]hay,[/COLOR]
[COLOR=#000000]I have both win7 & ubuntu on my system using the ubuntu boot loader as defualt. It was working good for long time, one day it just showed an error that there is a boot problem.[/COLOR]
[COLOR=#000000]I made live USB and tried to fix the boot using Boot-Repair, thinking that its requires only boot fix only, as once before happend to me. Nothing happend with that, I booted live ubuntu so I can copy some files in the partition of ubuntu to reinstall it fully, but I could not mount it, i searched and tried to fix mount problem using many terminal commands but no hope.[/COLOR]
[COLOR=#000000]and yes, when Boot-Repair was doing its work, it showed some kind of error which i do not remember.[/COLOR]
[COLOR=#000000]Can some one help me here [/COLOR]:smile:[COLOR=#000000] I just want to copy files from the partition.[/COLOR]
[COLOR=#000000]Appreciating you help.[/COLOR]
[COLOR=#000000]see these screenshots for more info: [/COLOR][picture1]("http://s30.postimg.org/8630x9wa9/Screenshot_from_2015_05_16_11_51_43.png")[COLOR=#000000] [/COLOR][picture2]("http://s7.postimg.org/8mthez7pn/Screenshot_from_2015_05_16_11_59_57.png")

---

### Post by dino99 on 2015-05-17
if you search 'oldfred' posts mainly into 'general' subforum you'll find lot of threads about dual boot issues with windows8. As you does not tell us if you boot with with bios or uefi with /without gpt, then its hard to say what to do. My own solution, in such a case, is to purge the grub* packages then doing a grub-install /dev/sda; but again with your system it can be different, better to get 'oldfred' answers/examples

---

