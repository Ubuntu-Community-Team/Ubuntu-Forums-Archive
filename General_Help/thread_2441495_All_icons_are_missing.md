---
title: "All icons are missing"
date: 2020-04-24
forum: General Help
---

### Post by dorpapst on 2020-04-24
[FONT=&amp][FONT=&amp]Hey,[/FONT][/FONT]
[FONT=&amp][FONT=&amp]After a restarted Ubuntu after the upgrade from 18.04 to 20.04, I cannot see any icons any more. Moreover, nautilus is not opening any more (it just does not show up longer).
Reinstalling Nautilus via Terminal did not help at all, so I guess there is another thing being wrong.
[/FONT][/FONT]
[FONT=&amp][FONT=&amp]If you have a look on the screenshot here:[/FONT][/FONT]
[FONT=&amp][ATTACH=CONFIG]285590[/ATTACH][/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp][FONT=&amp]the three dots on each window are not existing anymore, the "9 points" in the upper right corner to open the program overview is missing, there are no symbols on the desktop any more and on the upper right corner, the wifi symbol any other things are missing.[/FONT][/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp][FONT=&amp]It is quite difficult for me to google solutions for it, because I don't really know what to search for "icons missing" does not really give me solutions.[/FONT][/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp][FONT=&amp]Does anyone know how to solve this?[/FONT][/FONT]

---

### Post by dino99 on 2020-04-24
I can see many icons at the bottom on the screenshot :confused:
After a dist-upgrade, clean the system via:
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Then , if required, install: gnome-shell-extensions & gnome-tweaks
Next step: open tweaks to set your prefs

Finally, after a reboot, glance at warnings/errors logged into 'journalctl -b' from a terminal  :guitar:

---

