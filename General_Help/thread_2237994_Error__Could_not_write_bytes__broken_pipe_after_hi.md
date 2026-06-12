---
title: "Error : Could not write bytes : broken pipe after hibernation"
date: 2014-08-05
forum: General Help
---

### Post by AAEIV on 2014-08-05
[FONT=arial][COLOR=#333333]Suddenly, after "turning on" my ubuntu 12.04 from hibernation, there was an error[/COLOR]
> [COLOR=#333333]Could not write bytes:broken pipes[/COLOR]

[COLOR=#333333]which led to a black screen so I had to reboot. After rebooting, I got the same error message but my screen was working fine. I hibernated again my laptop, just to check and there wasn't any error at that time, but I am experiencing something weird.[/COLOR]
[COLOR=#333333]I type my password, only to see a black screen with a mouse pointer, which obbeys every movement I do. I also increased/decreased the volume and I was able to hear the sound effect.[/COLOR]
[COLOR=#333333]What I did was the trying to "reinstall" nvidia drivers(my graphics card is nvidia 8600m gs) using[/COLOR][/FONT]

[LIST=1]
[*][FONT=arial]CTRL-ALT-F1 (to get a CLI)[/FONT]
[*][FONT=arial]sudo apt-get update[/FONT]
[*][FONT=arial]sudo apt-get purge[/FONT]
[*][FONT=arial]nvidia-* sudo apt-get install invida-current-updates[/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]but when I reach step 4, I get sth about dependencies on nvidia 304 or something similar.[/COLOR]
[COLOR=#333333]Any idea on why this is happening only after hibernation and how to fix it?
Thank you very much in advance![/COLOR][/FONT]

---

