---
title: "Wine issues..."
date: 2007-04-05
forum: General Help
---

### Post by nerdman978 on 2007-04-05
Hello. I would like to get wine so that I can play some of my favorite old games on Ubuntu (Warcraft 3) so that I can finally delete the Windows partition that had been on my hard drive just so I could play that game. 

I went to this site and followed the instructions to get Wine.

http;//www.winehq.org/site/download-deb

And I added the repository and then installed it. But then where did it go? I looked under programs but I have no idea where it is. Help please?

---

### Post by garybrlow on 2007-04-05
The WineHQ version doesn't place shortcuts in the Applications Menu only the Debian/Ubuntu Repo version does. When the Ubuntu version updates it will replace the WineHQ version eventually and bring back the menus. :)

Cheers!!!


GaryBrlow :biggrin:

---

### Post by nerdman978 on 2007-04-05
Thanks I just noticed that the install software button on the top right was blinking! I installed the update, but I still have no idea of how to actually start wine!

---

### Post by MikeDX on 2007-04-05
have you tried running an exe?

either by double clicking one, or by going to a terminal and typing wine and then dragging your exe file into the terminal.

another way of doing it, right click the exe file and choose "open with other application" and then in the "use a custom command", type "wine" (without quotes) and press open

---

### Post by nerdman978 on 2007-04-05
Dee dee dee, I thought Wine had a GUI, turns out all you do is right click an exe file (my installation disk setup) and hit open with Wine. And huzzah! It works. That pwns :lolflag:

---

### Post by garybrlow on 2007-04-05
Run winecfg via terminal to set default configuration, you can also tweak it via the winecfg gui depending on your needs. You cans set-up shortcuts or run windows executable via terminal like this: wine utorrent.exe and using the file manager right click on an exe file and choose from the menu: Open With Wine or something similar like what MikeDX said. :p

Cheers!!!


GaryBrlow :biggrin:

---

