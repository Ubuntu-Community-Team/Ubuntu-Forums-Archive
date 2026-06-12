---
title: "Will Recovering Vista Delete Ubuntu"
date: 2008-06-26
forum: General Help
---

### Post by UBGrooven on 2008-06-26
Hello I run a Windows Vista Home Basic with a 139 GB hard drive, 1.60GHZ processor, and 1015 MB of ram. I am currently thinking about installing Ubuntu using Wubi and possibly transferring it later to a partition using LVPM. Now I have two questions the main one is if something was to happen to my windows files and it was destroyed. If I used my recovery tool a.k.a Drive D(it came with my computer and is on a separate partition)to recover the files and fix would this in anyway effect Ubuntu before and after I transfer it to a partition. Also I heard Grub has an error of not recognizing your Windows vista boot is this true, has it been fixed, and should I switch from Grub to something else. As you can tell I'm, very new to this :confused: and help would be appreciated.

---

### Post by bodhi.zazen on 2008-06-26
wubi installs Ubuntu into a file in windows and users the windows boot loader to boot Ubuntu. This is "easier" in that you do not have to partition your hard drive. It is easier to un-do as well.

If you install Ubuntu in the traditional way (or convert) you will need to partition your hard drive. This too can be undone, but it is an additional step.

GRUB will boot anything and there is no need to 'fear" GRUB. As with partitioning it adds ad additional step if you want to remove Ubutnu, but it is easy.

IMO a lot of new users make life difficult by not going with the defaults (which include installing GRUB into the MBR). This makes it more difficult, IMO at least, in that they then need to configure BIOS or GRUB.

When you install Ubuntu in the traditional method GRUB will be set up for you.

---

### Post by UBGrooven on 2008-06-26
Thanks for the reply but I'm still wondering will recovering windows effect ubuntu in anyway.

---

### Post by change_mode on 2008-06-26
Can't tell what exactly the recovery program does, because different companies use different recovery methods, but I'd say the risk of losing Ubuntu is very high, because in many cases the whole Windows partition will be reset.

---

### Post by UBGrooven on 2008-06-26
Thanks for you reply I just installed ubuntu and have some issues getting my wireless receiver card to be read its a HP 802.11b/g Wireless Network Adapter. Ubuntu recognizes the card as proprietary or something. And I don't know if I can use ndiswrapper tool because it needs the .inf driver file and I only seem to have a .sys file. Anyhelp would be appreciated.

---

### Post by bodhi.zazen on 2008-06-27
> **UBGrooven said:**
> Thanks for you reply I just installed ubuntu and have some issues getting my wireless receiver card to be read its a HP 802.11b/g Wireless Network Adapter. Ubuntu recognizes the card as proprietary or something. And I don't know if I can use ndiswrapper tool because it needs the .inf driver file and I only seem to have a .sys file. Anyhelp would be appreciated.

Do a google search on your exact wireless card and linux and you should find a link to the proper .INF

Otherwise you will have to look on your windows CD and see if you can find the .INF (in general user the windows XP driver).

---

