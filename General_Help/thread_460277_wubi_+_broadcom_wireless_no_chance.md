---
title: "wubi + broadcom wireless: no chance?"
date: 2007-05-31
forum: General Help
---

### Post by houdodu on 2007-05-31
I got Wubi on the system and want to install via a broadcom wireless card.

Any chance of that actually happening?

---

### Post by cantormath on 2007-05-31
> **houdodu said:**
> I got Wubi on the system and want to install via a broadcom wireless card.

Any chance of that actually happening?

What kinda of Broadcom card do you have.......?

---

### Post by minhmeoke on 2007-05-31
Does the card show up in the restricted drivers manager? To check this, go to System menu (upper-left corner of Desktop), select Administration, and then select Restricted Drivers Manager. Then just check the "enabled" box.

If there is no such option for your card, or it doesn't work, then try to see which type of card you have by opening up a terminal, and typing in
```
 lspci | grep Broadcom\ Corporation
```
Show the output here, and we can help you, or ask in the [**Absolute Beginner forum**]("http://ubuntuforums.org/forumdisplay.php?f=73"); the moderators there are probably more knowledgeable about these types of problems. If you still cannot get it working, then report the problem back here; if it is a problem with Wubi, then the developers would like to know about it.

If your card is a 43xx series, then try this Howto, it worked for me.
[**http://ubuntuforums.org/showthread.php?p=1071920&mode=linear**]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear")

Good luck!

---

### Post by houdodu on 2007-06-04
not much luck in the beginner forum.

initial install goes fine,
reboots into ubuntu installer,
card is detected properly,
card can't connect to network (even with manual ip entry), no DHCP, no nothing.

everything needs to download over wireless. card works fine in XP so i'm assuming its a driver issue and that i need to burn the full iso to install? or what should i do?

---

### Post by JoshBenner on 2007-06-04
Try this:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

I had problems with my Belkin Broadcom wireless card before I found that How To.
Easy to follow and now my card works without a hitch!
Hope it works for you like it did me!

---

### Post by houdodu on 2007-06-04
thanks, i did see that, but:

> Wired Internet access on the machine with the wireless card on it

dont have that luxury :(

---

### Post by JoshBenner on 2007-06-05
Oh I see! I should have guessed that#-o

I have attached bcm43xx-fwcutter so on stage 3 of the How To you do not need to download it.

I cannot upload wl_apsta.o as the forum won't let me but you could download it on the computer you are using to read this and transfer it over.
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

Btw you also don't need to install the network manager as it comes with Feisty (I assume you are using that).

Hope this helps you :)

---

