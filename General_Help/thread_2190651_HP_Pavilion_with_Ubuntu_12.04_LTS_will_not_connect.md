---
title: "HP Pavilion with Ubuntu 12.04 LTS will not connect to wifi"
date: 2013-11-28
forum: General Help
---

### Post by dwarfminer42 on 2013-11-28
Hello ubuntu forums--
I recently got an HP Pavilion (model number possibly p6000 but I am still researching) from a friend. It did not have an internal hard drive, and I am running Ubuntu 12.04 LTS off a Maxtor OneTouch 120 GB external drive. Install went fine, Ubuntu runs fine, but something strange occurs when I attempt to connect to wifi.

Under my available connections list, my wifi network "CenturyLink1827" appears.
I click on it and enter my WPA2 key as normal.
The empty wifi logo changes to a scrolling one, and this continues for about 2 minutes or so.
Then it pops up the security credentials dialog with my WPA key still entered. 
If you click continue, it tries again and loops back.
The key is entered correctly, I have checked it against the router and my personal logs.

I have run lshw and lpci as super-user.
lpci doesn't return any sort of network card.
lshw returns one: it doesn't list a manufacturer or a model number, and uses "Driver version: 3.8.0 generic"

From what I can find, the p6000 doesn't have an external network card plugged into a motherboard slot, it has an integrated "wireless ethernet solution" within the motherboard itself.

I have the laptop I am currently writing this on available to download driver updates and the like.
I found someone with an HP pavilion with the same problem, but they have a network card appear when using $lshw, and troubleshoot it beyond that.

Any help is greatly appreciated.

savag3

---

### Post by mikewhatever on 2013-11-30
Why don't you add the outputs to the original post, even if you don't think they are useful.

---

