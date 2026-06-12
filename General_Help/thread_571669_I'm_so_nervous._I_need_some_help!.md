---
title: "I'm so nervous. I need some help!"
date: 2007-10-09
forum: General Help
---

### Post by Masterj15 on 2007-10-09
I know I've made three threads (including this one) but I have agood problem that I need some help with. I have two computers:

Master computer:
384 ram 
nvidia card (old but I have new one wich I'm about to mention)
cd-rw drive
sound card
bla bla bla

Guest computer:
128 ram
ati card (very old but replaceing with old nvida card which I'm about to mention)
dvd drive
intergrade stuff.



I want to change my graphic card on the computers. The master computer will have my brand spanking new E-Geforce 7300 GS with 256 mb on it. This means ubuntu ultimate with beryl!!!! or compiz fusion!!!

The guest computer with have my old nvidia card which has 3d driect rendering!!!!. 

I tried changing the very old ati graphic card with the old nvidia and the creen didn't come up!! I don't want this to happen to my master computer. I am willing to erase everything on my master computer as long as this new geforce works.


Any ideas, thoughts, coments, bla bla bla will be greatly appreatiacted

---

### Post by FuturePilot on 2007-10-09
I'm taking it when you say the screen doesn't come up you mean you're stuck at a terminal login right?
You'll need to reconfigure xorg then.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by JBAlaska on 2007-10-09
I beleive if you change to the vesa driver **before** you swap video cards, it should boot up, then you can install the new card's drviers.

This is a old windoze trick that should work with Linux

---

### Post by Masterj15 on 2007-10-09
> **FuturePilot said:**
> I'm taking it when you say the screen doesn't come up you mean you're stuck at a terminal login right?
You'll need to reconfigure xorg then.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I'm sorry I should be more specific! I mean when I start up the computer it makes a sound and goes on, but the monitor is black.(as in the light is brown and not green. This mean the monitor thinks the computer is not on.)

---

### Post by rsambuca on 2007-10-09
I would personally upgrade your RAM before spending money on a new videocard.  Also, would you kindly make your thread titles more descriptive of your question in the future?

---

### Post by Masterj15 on 2007-10-09
> **JBAlaska said:**
> I beleive if you change to the vesa driver **before** you swap video cards, it should boot up, then you can install the new card's drviers.

This is a old windoze trick that should work with Linux

Thats what I was going to do with my master computer but I don't what to try anthing on that computer before I do this one. (This one is like a test)

---

### Post by Masterj15 on 2007-10-09
> **rsambuca said:**
> I would personally upgrade your RAM before spending money on a new videocard.  Also, would you kindly make your thread titles more descriptive of your question in the future?

I have two more ram chips I can use. Also Yes I can and I will.

---

### Post by JBAlaska on 2007-10-09
Try putting the ati card back in, boot to your BIOS, make sure Plug and play OS is set to no, if you have a setting to "reset configuration data" set that to yes

Make sure you assign a IRQ for the graphics card. Now save and exit. DO NOT let the computer restart, install the new (old) card and try to boot.

If it lights up your monitor cool, if not remove the card and clean the gold contacts with a pencil eraser (prolly you should do this in the first step) and try putting the card in a different slot if it's PCI or ISA.

---

### Post by Masterj15 on 2007-10-10
> **JBAlaska said:**
> Try putting the ati card back in, boot to your BIOS, make sure Plug and play OS is set to no, if you have a setting to "reset configuration data" set that to yes

Make sure you assign a IRQ for the graphics card. Now save and exit. DO NOT let the computer restart, install the new (old) card and try to boot.

If it lights up your monitor cool, if not remove the card and clean the gold contacts with a pencil eraser (prolly you should do this in the first step) and try putting the card in a different slot if it's PCI or ISA.

It works! awsome!

---

