---
title: "[Ubuntu 18.04] Thai Characters not display in Notepad++"
date: 2019-02-16
forum: General Help
---

### Post by jubsa132 on 2019-02-16
Hi all,

I just new to Ubuntu 18.04, I've installed Notepad++ and trying to type Thai Characters which I already added Keyboard layout to support Thai (can switch between Th/En) via Super + Space bar.

But when I type Thai Characters in Notepad++, it showed unreadable characters as per images below.
[ATTACH=CONFIG]282543[/ATTACH]
[ATTACH=CONFIG]282542[/ATTACH]
Please kindly advice or provide any suggestion so that I will try it out.

Thank you!

---

### Post by Impavidus on 2019-02-17
Notepad++ is a Windows application, so I assume you used wine to get it installed. That's a workaround for Windows applications you can't live without, but it's far from ideal. Apparently, [some versions of Notepad++ should work pretty well]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=2983"), but it appears yours cannot find some fonts. I've never used wine myself. It's better to find a Linux alternative. There are many text editors.

---

### Post by Holger_Gehrke on 2019-02-17
To expand on what Impavidus wrote: if you installed Notepad++ through the "Software" application you got a snap that bundles Wine and Notepad++. There have been problems with snap packages not being able to use fonts installed on the system but I don't know if that's still so. The workaround for those situations was to install fonts you need to the personal hidden font directory '.fonts' in your home directory.
There is an editor that is meant to look and work like Notepad++ named [Notepadqq]("https://notepadqq.com/"). It's available both as a snap and from a PPA in classic '.deb' packages. While the developers recommend the snap, a lot of the comments on their blog are about all the problems users who follow that recommendation have, so I'd advise to use the PPA.

Holger

---

### Post by jubsa132 on 2019-02-17
Hi Impavidus and Holger

 
 
 Thank you very much for your advice.


 I searched and found that there are several useful applications that similar to notepad++.
I installed ‘Notepadqq’, and it displayed Thai characters properly!
I liked it! It has lot of similar features that I commonly used in 'Notepad++'.

[ATTACH=CONFIG]282549[/ATTACH]

 By the way, for the 'notepad++' that I installed previously, I go to **Ubuntu Software** (GUI) -> **type 'Notepad++'** -> **Search** -> **Install** -> **Launch**. I am not sure that it using Wine or not (but I guess it is).

 
 Thanks again and really appreciated both of your kind advice.

---

