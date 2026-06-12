---
title: "cannot install 13.04 on my samsung system"
date: 2013-05-08
forum: General Help
---

### Post by su:bhatta on 2013-05-08
I am having a samsung 305e5z laptop with AMD A4 processor, Radeon Graphics, 500GB HDD, 4GB DDR3 RAM. I have windows 7 installed. I had an old boot dvd of 10.10(Maverick Meerkat) which I installed by partitioning my HDD in 2 equal parts. I wanted to install 13.04 by formatting the Meerkat partition. 

I have downloaded both AMD64 desktop version as well as i386 desktop iso's. But when I am booting the live CD, after the first screen of Ubuntu with 5 orange dots underneath it nothing else is happening.
No error message or anything is showing.

Please help.

---

### Post by grahammechanical on 2013-05-08
Hi, welcome to the forum. Here is something that you can try. Load the 13.04 Live DVD

1) at the first purple screen with the icons of the human and the keyboard press Enter.
2) at the next screen select the language. English is the default. Pressing Enter will accept English.
3) at the TRY UBUNTU - INSTALL UBUNTU screen press F6
4) scroll down the menu that appears and select nomodeset and press Esc to get back to the TRY - INSTALL screen.
5) Select Try Ubuntu and press enter.

See if that gets you to a live session. That are other F6 options. You may need to experiment. You may need a combination of F6 options.

F6 Options - acpi=off; noapic; nolapic; nodmraid; nomodeset.

Regards.

---

### Post by su:bhatta on 2013-05-10
grahammechanical, thankx a ton for the sugesstion.... it worked like a breeze.... i set it to nomodeset, i hav no clue what it meant but did the work...
last i used Ubuntu was 10.10 Maverick, the Unity i am hating and have already downloaded Gnome as well as xfce...Unity just sitz in that side!!! me no like...

Thanx for your help tho'....

---

