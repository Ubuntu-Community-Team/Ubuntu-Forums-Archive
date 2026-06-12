---
title: "How to install ttf-mscorefonts-installer and fontconfig  offline"
date: 2024-07-03
forum: General Help
---

### Post by sd1036770 on 2024-07-03
Hello,I hava an offline ubuntu server24.04, I want to install some windows fonts, I copy fonts to the /usr/share/fonts/winfonts,  run [COLOR=#191B1F][FONT=Menlo]mkfontscale&#65292;[/FONT][/COLOR][COLOR=#191B1F][FONT=Menlo]mkfontdir&#65292;[/FONT][/COLOR][COLOR=#191B1F][FONT=Menlo]fc-cache 3 commands but it shows command not found.
So how to install the [/FONT][/COLOR]ttf-mscorefonts-installer and fontconfig offiline?
Thanks

---

### Post by vanadium on 2024-07-03
If you have a message "command not found", then it means the command is not installed onto your system. If you do not want to connect to internet, you will need to have an installation CD that can serve as repository for commands/applications you want to install on the server.

Just copying valid font files to subdirectories under dedicated font folders like /usr/local/share/fonts and then running `fc-cache -f -v` should work to install the fonts and include them in the font cache.

---

