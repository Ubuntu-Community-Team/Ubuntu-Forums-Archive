---
title: "WINE help required."
date: 2006-11-20
forum: General Help
---

### Post by _simon_ on 2006-11-20
I am following this guide:

> 
To get it to play in Wine

1) install the game
2) add this to your config

[AppDefaults\\\\sc3.exe\\\\x11drv]
; Sim City 3000
"Desktop" = "800x600"
"Managed" = "N"

[AppDefaults\\\\sc3.exe\\\\Version]
"Windows" ; = "win2k"

3) cd to ~/.wine/drive_c/Program\\ Files/Maxis/SimCity\\ 3000/Game

4) wine sc3

5) Now the game will load and there will be a 800x600 black box and
you should hear the sound playing. All you have to do now is click in the center of this black box and the game should start.


The problem is I haven't got a clue how to add that to my config or where to even find it. I can't see anywhere in winecfg for that.

---

### Post by CatKiller on 2006-11-20
> **_simon_ said:**
> The problem is I haven't got a clue how to add that to my config or where to even find it. I can't see anywhere in winecfg for that.

I think that must be an old guide, from when Wine just had a file for configuring settings. The equivalent section would be the Applications tab - you'd add your SimCity 3000 executable, and then set particular settings for that application in the usual way. If it's the only game you've installed with Wine, you could set global settings accordingly instead.

I couldn't even get SimCity 3000 to install. Stupid broken copy protection.

---

