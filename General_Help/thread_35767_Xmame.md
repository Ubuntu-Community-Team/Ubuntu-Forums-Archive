---
title: "Xmame"
date: 2005-05-20
forum: General Help
---

### Post by shador on 2005-05-20
Anyone knows how i can get Xmame to work. 

I installed the files Xmame-common, Xmame.sdl, xmame.svga, xmame-tools and xmame-x.

When i run the program in the terminal i get this.

info: trying to parse: /etc/xmame/xmamerc
error: /etc/xmame/xmamerc(71): unknown option joyusb-calibrate, ignoring line
info: trying to parse: /home/shador/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /home/shador/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /home/shador/.xmame/rc/pacmanrc
I386 joystick interface initialization...
OSD: Warning: No joysticks found disabling joystick support
loading rom 0: pacman.6e
loading rom 1: pacman.6f
loading rom 2: pacman.6h
loading rom 3: pacman.6j
loading rom 4: pacman.5e
loading rom 5: pacman.5f
loading rom 6: 82s123.7f
loading rom 7: 82s126.4a
loading rom 8: 82s126.1m
loading rom 9: 82s126.3m
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.

I haven't downloaded any games yet so i can't understand why it tries to load pacman. 
So. anyone knows how i can get it to work?

---

### Post by Sniffer on 2005-05-20
[QUOTE=shador]Anyone knows how i can get Xmame to work. 

I installed the files Xmame-common, Xmame.sdl, xmame.svga, xmame-tools and xmame-x.

When i run the program in the terminal i get this.

info: trying to parse: /etc/xmame/xmamerc
error: /etc/xmame/xmamerc(71): unknown option joyusb-calibrate, ignoring line
info: trying to parse: /home/shador/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /home/shador/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /home/shador/.xmame/rc/pacmanrc
I386 joystick interface initialization...
OSD: Warning: No joysticks found disabling joystick support
loading rom 0: pacman.6e
loading rom 1: pacman.6f
loading rom 2: pacman.6h
loading rom 3: pacman.6j
loading rom 4: pacman.5e
loading rom 5: pacman.5f
loading rom 6: 82s123.7f
loading rom 7: 82s126.4a
loading rom 8: 82s126.1m
loading rom 9: 82s126.3m
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.

I haven't downloaded any games yet so i can't understand why it tries to load pacman. 
So. anyone knows how i can get it to work?[/QUOTE]

1st - you only need Xmame-common and ONE of the others, you need to choose wich one works better for you, SDL, X or SVGA

2nd - I think pacman is a default game that comes pre installed..just for testing.

3rd - you need the bios most of the times to run a game...for instance neogeo

4th - to launch game you need to xmame nameofthegame.zip

5th - Gxmame don't work..so don't even try it.

Hope it helps
Sniff.

---

### Post by shador on 2005-05-20
[QUOTE=Sniffer]1st - you only need Xmame-common and ONE of the others, you need to choose wich one works better for you, SDL, X or SVGA

2nd - I think pacman is a default game that comes pre installed..just for testing.

3rd - you need the bios most of the times to run a game...for instance neogeo

4th - to launch game you need to xmame nameofthegame.zip

5th - Gxmame don't work..so don't even try it.

Hope it helps
Sniff.[/QUOTE]


I assume that the bios are avalible via synaptics to. If not then where?

---

### Post by Sniffer on 2005-05-20
[QUOTE=shador]I assume that the bios are avalible via synaptics to. If not then where?[/QUOTE]

Nope, Ofcourse NOT..it isn't legal....

But google is your friend :-# 

search for neogeo bios for example and check xmame info to see what plataforms are supported and wich of them need the bios to run the games.

---

### Post by darkaudit on 2005-05-20
[QUOTE=Sniffer]5th - Gxmame don't work..so don't even try it.[/QUOTE]I respectfully disagree. Gxmame is back in development with a beta @ [http://sourceforge.net/projects/gxmame/](http://sourceforge.net/projects/gxmame/). There's even a Debianized package all ready to go. Hasn't given me any trouble.

---

### Post by Sniffer on 2005-05-20
[QUOTE=darkaudit]I respectfully disagree. Gxmame is back in development with a beta @ [http://sourceforge.net/projects/gxmame/](http://sourceforge.net/projects/gxmame/). There's even a Debianized package all ready to go. Hasn't given me any trouble.[/QUOTE]

Hmmm, the last time i tried...it didn't make the list of the games.....

Maybe there is hope at the end of the tunel.

Thks for the link.

---

### Post by NeoChaosX on 2005-05-20
[QUOTE=Sniffer]Hmmm, the last time i tried...it didn't make the list of the games.....[/QUOTE]
Well, the older versions are incompatible with the versions of XMAME that Ubuntu has. The 0.35beta of GXMAME manages to build the game list just fine, though.

---

