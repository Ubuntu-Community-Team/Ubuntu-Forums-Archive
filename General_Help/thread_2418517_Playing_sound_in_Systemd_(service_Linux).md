---
title: "Playing sound in Systemd (service Linux)"
date: 2019-05-07
forum: General Help
---

### Post by 2kbit on 2019-05-07
[COLOR=#242729][FONT=Arial]I have this service, running on Xubuntu.[/FONT][/COLOR]

[COLOR=#666600][[/COLOR][COLOR=#660066]Unit[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]Description[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#660066]Controller[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]After[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]graphical[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]target[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#666600][[/COLOR][COLOR=#660066]Service[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]ExecStart[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/usr/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]controller[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]StandardInput[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]tty[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]force[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]StandardOutput[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]journal[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]Restart[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]always[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]TimeoutSec[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]2s[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#666600][[/COLOR][COLOR=#660066]Install[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]WantedBy[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]graphical[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]target 

[/COLOR]
[COLOR=#242729][FONT=Arial]When a certain action happens in the program (controller), it must execute an audio (.mp3). I can guarantee that the application works.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now running on the service, all other program functionality works, but does not play mp3 audio. I've tried different ways to create the service, but it does not work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I make the controller program, run an audio, using a Linux service?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Sorry for my bad English.[/FONT][/COLOR]

---

### Post by 2kbit on 2019-05-08
[COLOR=#212121][FONT=arial]The controller creates a new process to play the audio. This may be the error in the systemd.[/FONT][/COLOR]

---

