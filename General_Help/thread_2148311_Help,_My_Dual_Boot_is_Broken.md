---
title: "Help, My Dual Boot is Broken"
date: 2013-05-24
forum: General Help
---

### Post by ipowell on 2013-05-24
Hey i'm having trouble with booting to ubuntu. And please bare with me its my first time posting anything on these forums.

I was going threw a couple of tutorials on speeding up your system and edited one of the values in the grub file located [FONT=Verdana][COLOR=#333333]/etc/default/grub[/COLOR][/FONT]

[FONT=Verdana][COLOR=#333333]Now the GRUB_TIMEOUT is set to '0' and when I start up my laptop it goes to the default os boot menu which is ubuntu. But it boots to windows instead of ubuntu which makes it very difficult to fix from windows.

I have downloaded ext2explore to change the value which I can do but I can't update the grub so it doesn't work.

Thanks for any help or suggestions.[/COLOR][/FONT]

---

### Post by grahammechanical on 2013-05-24
I think that pressing left shift should bring up the Grub menu.

> [COLOR=#333333][FONT=Ubuntu]Holding down the SHIFT key early in the boot process until the menu displays.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]
[LIST]
[*=left]GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.
[/LIST]


[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

