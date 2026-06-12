---
title: "need help!"
date: 2007-04-25
forum: General Help
---

### Post by SimpliciTy on 2007-04-25
Hey everyone so just today i decided to update from 6.10 edgy to 7.04 all updates went fine (i used ubuntu update manager) and rebooted.
when i turned on comp i chose to boot from the first item on the list (most recent ubuntu) and i get my nvidia splash screen (using nvidia drivers since i have nvidia card) then i blackscreen for two seconds (normally happens) but then i jest get the little spinning cursor on a plain black screen when i should be getting a login form.
any help would be very apreciated!
thanks,
Simplicity
p.s if you need any info just post what info you need

---

### Post by zvacet on 2007-04-25
```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv** and update your drivers

---

### Post by SimpliciTy on 2007-04-25
> **zvacet said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv** and update your drivers

how am i suposed to do that when i can't even load up ubuntu?
i can't even get to login screen therefor i have no acces to Konsole(Terminal)

---

### Post by ashz on 2007-04-25
when grub starts up u will have the option to select it!!

---

### Post by zvacet on 2007-04-25
Boot in recovery mode,that is what **ashz** told you.in recovery mode you don´t need sudo ,cause you are root allready.

---

### Post by SimpliciTy on 2007-04-25
> **ashz said:**
> when grub starts up u will have the option to select it!!

could you tell me how to do this then?
becuase all i get is the dual boot screen and when i select the linux ubuntu kernel i get a nvidia splash scrren, black screen, another nvidia splash screen, then a black screen with the loading cursor that after some time just turns into a plain bsod.
> **zvacet said:**
> Boot in recovery mode,that is what **ashz** told you.in recovery mode you don´t need sudo ,cause you are root allready.

i have tried recovery mode it just like imediatley turns into a black screen of death.

aslo i tried booting from a live cd and that didn't work.

---

### Post by SimpliciTy on 2007-04-25
ok thanks guys i finally got the reconfigurer working except for one problem....
when i try selcting the color mode i will press spacebar to select it, then hit enter and all the sudden terminal pops up at the bottom and says warning your about to overwrite a custom configuration file make back up at user/bin/blah blah blah.
but then IT WONT LET ME GO BACK TO THE RECONFIGURER!!!!
OMFG!
FFS!
JESUS CHRIST!
So does anybody know how to bring the reconfigurer back up?
thanks,
Simplicity

---

### Post by ashz on 2007-04-26
lol i understand ur upset lol, it can get frustrating, this is why i always do a fresh install instead of updating, i backup everything i want makes things a lot easier..anyways back to ur problem..

do the reconfigure thing but select vesa instead of nvidia, then when u have ur system up then reinstall the drivers u need!

im not to hot on nvidia stuff so sorry m not to much help...if any :P

cheers
ash

---

