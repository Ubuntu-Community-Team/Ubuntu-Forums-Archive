---
title: "Unable to log in to Ubuntu account after changing graphics interface"
date: 2023-06-22
forum: General Help
---

### Post by pepyachka on 2023-06-22
[COLOR=#000000][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I'm experiencing an issue with logging in to my Ubuntu account after changing the graphics interface to Xorg(or Cinnamon). Every time I try to log in, I'm redirected back to the login page without any error message. This problem started occurring after switching from the default Wayland session to Xorg (or Cinnamon) in order to resolve compatibility issues.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I have attempted various troubleshooting steps, including checking the Xorg log files and verifying the correctness of my login credentials. However, none of these actions have resolved the issue.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I'm wondering if this problem could be related to my hardware configuration. My system specifications are as follows:[/FONT][/COLOR]

[LIST]
[*]cpu: Intel® Core&#8482; i5-7400 CPU @ 3.00GHz × 4
[*]graphics: Mesa Intel® HD Graphics 630 (KBL GT2)
[/LIST]
[COLOR=#000000][FONT=&amp]I would greatly appreciate any assistance or suggestions on how to resolve this login problem and successfully access my Ubuntu account with the Xorg (or Cinnamon) desktop environment. Thank you in advance for your help![/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Best regards[/FONT][/COLOR]

---

### Post by pepyachka on 2023-06-26
Resolved. Install KDE Plasma

---

### Post by MAFoElffen on 2023-06-26
??? What you were describing was a "login loop". All that probably needed was to recreate your user ~/.Xauthority file.

---

