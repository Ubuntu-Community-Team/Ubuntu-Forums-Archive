---
title: "A Problem With Alien Arena"
date: 2008-06-10
forum: General Help
---

### Post by Funky91 on 2008-06-10
Hello, here's the problem. Alien Arena is listed in the Add or Remove Applications list however it is the old version. There is a newer version advertised for download on the Alien Arena website. It is annoying because before I can join an online game i have to download all the textures and maps to play. 

I have downloaded the latest version and am struggling to install it. I have extracted it to the games folder as the readme recommended however when I tried the command it said would work it didn't. It just came up with the following and would not go any further. 

This is what I did and what it said. 

```

hugh@hugh-desktop:~$ cd usr/games/alienarena2008
bash: cd: usr/games/alienarena2008: No such file or directory
hugh@hugh-desktop:~$ cd /usr/games/alienarena2008
hugh@hugh-desktop:/usr/games/alienarena2008$ ./crded
using /home/hugh/.codered/data1/ for writing
using /home/hugh/.codered/arena/ for writing
execing default.cfg
Unknown command "unbindall"
couldn't exec config.cfg
------- Loading game.so -------
LoadLibrary (./arena/game.so)
==== InitGame ====
------- Server Initialization -------
name is not a field
name is not a field
name is not a field
name is not a field
0 entities inhibited
0 teams with 0 entities
-------------------------------------
======== CRX Initialized ========

Unknown command "clear"
Sending heartbeat to 69.143.100.63:27900
Sending heartbeat to 69.143.100.63:27900
Ping acknowledge from 69.143.100.63:27900
Sending heartbeat to 69.143.100.63:27900
Ping acknowledge from 69.143.100.63:27900

```

Anyone know how to install it?

---

### Post by Rhubarb on 2008-06-10
You could try installing it to your home directory somewhere, such as:
/home/hugh/games/alienarena2008

Another thing I picked up is that it looks as if you're trying to execute the alien arena dedicated server, not the client.
I could be wrong, as I've never tried alien arena before, but usually a game that ends with "ded" stands for dedicated server.
So try and find the executable to run the client (the game).

---

### Post by Funky91 on 2008-06-10
ah, i wasn't really reading the readme. yea, I was trying to install the game so it shows up in the applications menu.

The readme says,
Simply unzip the archive in your /usr/local/games folder or wherever you wish to place the game.



Type ./crx to run the game, or ./crded to start a dedicated server or use the shortcuts installed in the menu.



Source files are included, so you may compile the binaries yourself if neccessary.  Please visit the forum if you have any questions regarding this.



How do I install it so it shows up in the menu?

---

### Post by Rhubarb on 2008-06-10
System --> Preferences --> Main Menu
(or right click on Applications --> Edit Menus)

Click on Games, then click on "New Item"
Name: Alien arena
Command: /usr/games/alienarena2008/crx
(or try "sh /usr/games/alienarena2008/crx")
Comment: Alien Arena 2008

If you have a nice icon for alien arena, click on the spring icon there, and navigate to the directory to where the icon is, press ok, then select the icon you wish to use, press ok.
It should then appear in your Games menu.

If the game still doesn't work, you may have to create a simple bash script to run the game).

---

