---
title: "Desktop Lunix and .desktop files"
date: 2014-04-18
forum: General Help
---

### Post by deamon_knight on 2014-04-18
I'm working to move more of my compouter usage to desktop Ubuntu, specifically Lubuntu 13.10, for both regular desktop applications and gaming (yeah Steam!). I've made pretty good success (Steam and my Steam games are running properly!) and I'm going to hold off on a dist-update to 14.04 for a bit yet. Right now, I'm trying to figure out .desktop files. I'm trying to launch a game openxcom , and from the terminal 
```

openxcom -data ~/Programs/Games/XCom\ UFO\ Defense/XCOM

```

works normally. I thought I could create a .desktop file for this game with this same commandline. Example:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=OpenXcom
Comment=An open-source clone of the famous X-COM game
Exec=openxcom -data ~/Programs/Games/XCom\ UFO\ Defense/XCOM
Terminal=false
Icon=openxcom
Categories=Game;StrategyGame;

```

it seems like the aurgument "-data ~/Programs/Games/XCom\ UFO\ Defense/XCOM" is not being passed and I don't know why this should be or how to correct it. Ultimately I may want to add more games (or any other application) to my desktop, and need to pass these extra arguments. Any advice? Quick googling suggests this method should work, so I don't get it.

Thanks

---

### Post by coldcritter64 on 2014-04-18
> **deamon_knight said:**
> ...
**it seems like the aurgument "-data ~/Programs/Games/XCom\ UFO\ Defense/XCOM" is not being passed and I don't know why** this should be or how to correct it. Ultimately I may want to add more games (or any other application) to my desktop, and need to pass these extra arguments. Any advice? Quick googling suggests this method should work, so I don't get it.

Thanks

Try expanding the environment variable for your home folder (~) out to its absolute path. For example instead of ~/Programs ..., put your full home-folder address "/home/<your-username>/Programs ..." (obviously replace <your-username> with your actual username used in your install and don't include the quotes).

_*Sometimes*_ with shell scripts / desktop config files, and even some applications like cron, an absolute path is required to operate correctly.
Hope this is of some help to you, cheers.

---

