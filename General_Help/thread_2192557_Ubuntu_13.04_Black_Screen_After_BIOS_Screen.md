---
title: "Ubuntu 13.04 Black Screen After BIOS Screen"
date: 2013-12-08
forum: General Help
---

### Post by derbydash on 2013-12-08
[SIZE=1][FONT=verdana]Hi, I have a[FONT=arial] Dell Latitude D620[/FONT] laptop.
Upgraded from [FONT=arial]**Ubuntu 12.10**[/FONT] to [FONT=arial]**13.04**[/FONT].
[B]
MAIN ACCOUNT:[/B][/FONT][/SIZE][FONT=verdana]
[LIST]
[*][SIZE=1][FONT=verdana]Login Screen > Password > Enter > Blinks to a TTY terminal with some words[FONT=arial] [*very quickly*][/FONT] > Blinks to purple screen > Blinks to Login screen [FONT=arial][lightdm][/FONT][/FONT][/SIZE]
[*][SIZE=1][FONT=verdana]Can change the session options: [FONT=arial]Gnome, Cinnamon, Ubuntu, etc.[/FONT][/FONT][/SIZE]
[*][SIZE=1][FONT=verdana]Same thing[FONT=arial] (first bullet)[/FONT] happens with each kind of session listed above.[/FONT][/SIZE]
[/LIST]
[SIZE=1][FONT=verdana]**SECONDARY ACCOUNT:**[/FONT][/SIZE]
[LIST]
[*][SIZE=1][FONT=verdana]Can login[/FONT][/SIZE]
[*][SIZE=1][FONT=verdana]Can change session but *only* runs in [FONT=arial]Gnome Fallback Mode[/FONT][/FONT][/SIZE]
[/LIST]
[/FONT][SIZE=1][FONT=verdana]

[FONT=arial] - The screen is in 800x600 resolution, not native resolution.
 - Takes a while to load things.[/FONT][/FONT][/SIZE]

---

### Post by derbydash on 2013-12-08
[B]UPDATE:
[/B][SIZE=1][FONT=arial black][FONT=verdana]Well, I managed to work around this problem A BIT.
[LIST]
[*]Searched for some help on other forums[COLOR=#2F4F4F] [*Don't remember the things I searched for; it was just basic searches. keywords such as: [SIZE=2][FONT=courier new]ubuntu 13.04 black screen, updating ubuntu 13.04[/FONT][/SIZE]*][/COLOR]
[*]Uninstalled cinnamon
[*]Updated/Upgraded[COLOR=#2F4F4F] [*sudo apt-get update && sudo apt-get upgrade*][/COLOR]
[*]Reinstalled cinnamon
[*]Went into the GRUB [COLOR=#2F4F4F][**UPDATE: ***for me, GRUB no longer works for me. It loads to a black screen after choosing to go to the "recovery mode."*][/COLOR]
[*]Enable network
[*]dpkg files
[*]Reboot
[*]Update cinnamon > broken packages [*oh wells....[COLOR=#2F4F4F]ignored this problem[/COLOR]*]
[*]Went into the GRUB again
[*]All options tested
[*]Reboot after each option in GRUB
[*]Rebooted
[*]> Loaded BIOS screen
[*]> Black screen for 5-10 seconds+
[*]> Loaded "Ubuntu Loading" screen
[*]> Black screen for 5-10 seconds+
[*]Loaded Login Screen [*lightdm*]
[*]Tried to log into MY main account > Refreshes back to the login screen.[COLOR=#2F4F4F] [**UPDATE:*** Made secondary account the main account, removed first main account.*][/COLOR]
[*]Tried to log into secondary account > Success [COLOR=#FF0000]ONLY[/COLOR] when "Cinnamon" is chosen for the session.[COLOR=#2F4F4F] [**UPDATE:*** ^*][/COLOR]
[/LIST]
- Screen resolution is still 800x600. [[COLOR=#2F4F4F]**UPDATE: ***Look in the link in the post below for how to get my screen resolution back to 1024x768.*][/COLOR]
- Backing up stuff. [COLOR=#2F4F4F][**UPDATE: ***Backed up with Ubuntu One and transferred some smaller files to USB.*][/COLOR]

Any ideas on how to help?? [COLOR=#2F4F4F][**UPDATE: ***Pretty much figured stuff out by searching keywords related to my problem.*][/COLOR][/FONT][/FONT][/SIZE]

---

### Post by derbydash on 2014-01-20
[SIZE=1][FONT=verdana]If you went to my other thread, **[here]("http://ubuntuforums.org/showthread.php?t=2144614&amp;p=12645437")**, look at post** #3**.

**NOTE TO SELF/FUTURE REF, JIC:**[/FONT][/SIZE]
[FONT=courier new]```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove
```
```
sudo apt-get clean && sudo apt-get autoclean
```[/FONT]

[SIZE=1][FONT=verdana]Also, *uninstalled* cinnamon and *reinstalled *it, just in case:
*Even if I have Ubuntu 13.04, I still enter the following commands in terminal:*[/FONT][/SIZE]
[FONT=courier new]```
[SIZE=2]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable[/SIZE]
```[SIZE=2]
```
sudo apt-get update
```
```
sudo apt-get install cinnamon
```[/SIZE][/FONT]

[SIZE=3][FONT=verdana](Take [/FONT][COLOR=#ff0000]**[FONT=arial black]NOTE [/FONT]**[/COLOR][FONT=verdana]that on [FONT=arial black]**[noobslab.com]("http://www.noobslab.com/2013/04/install-cinnamon-in-ubuntu-1304-raring.html")**[/FONT], it says that if you already have[/FONT] [FONT=arial black]Gnome 3.8[/FONT], [FONT=arial black]do[COLOR=#ff0000]** NOT** install cinnamon[/COLOR][/FONT][FONT=verdana]!)[/FONT][/SIZE]

---

