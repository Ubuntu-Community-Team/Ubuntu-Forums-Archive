---
title: "Battery management best practice: TLP+TLPUI vs Slimbookbattery"
date: 2020-09-30
forum: General Help
---

### Post by ayamaros on 2020-09-30
[COLOR=#878A8C][FONT=IBMPlexSans][SIZE=3][COLOR=#1A1A1B][FONT=inherit]I am confused in terms of which combination is best to install. I am running Kubuntu 20.04 on a Thinkpad X230. In the beginning, I have installed TLP and then have added the TLPUI to have the graphical easy access.
[/FONT][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=&amp][SIZE=3]I then installed Slimbookbattery since it was recommended by this article: [http://ubuntuhandbook.org/index.php/2020/06/improve-battery-life-ubuntu-20-04-lts/](http://ubuntuhandbook.org/index.php/2020/06/improve-battery-life-ubuntu-20-04-lts/)[/SIZE]
[SIZE=3]Does Slimbookbattery go hand-in-hand with TLP +TLPUI or is it going to present a conflict if they are installed together?  I understand that Slimbookbattery is a graphical tool based on TLP so my initial thought is that installing both will be redundant.
[/SIZE]
[SIZE=3]In addition, Kubuntu 20.04 has its own Power Management built-in software. Do I disable this completely or can it run with the combination of TLP and/or Slimbookbattery?[/SIZE]
[SIZE=3]Thanks.[/SIZE]
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by blackbird34 on 2020-10-09
I'd say pick one, or the other, but not both as they might conflict with each other. I'd say they're roughly equivalent.

You don't need to touch Kubuntu's own built-in power management, just configure the settings you want in it.

---

### Post by &amp;wP*!) on 2020-10-09
More than one Power management software on Linux might conflict with each other. Please google and find it out. TLPUI might be graphical front-end of TLP. I have Lubuntu and disabled LxQt power management tool to remedy such conflict. I recommend you to use only one of them. TLP seems to be the best one (and TLPUI as well).

---

