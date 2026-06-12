---
title: "Install 32 bits program in winetrick?"
date: 2020-05-17
forum: General Help
---

### Post by LMH1 on 2020-05-17
Hi try to install 32 bits program on 64 bits operatingsystem kubuntu 20.04 but get error:
 D-Fend-Reloaded-1.4.4-Setup.exe


Tryed as root 
WINEPREFIX="$HOME/prefix32" WINEARCH=win32 wine wineboot


But still get:
[ATTACH=CONFIG]285911[/ATTACH]

I also tryed:[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
Ubuntu 20.04  sudo add-apt-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main' 
 sudo apt install --install-recommends winehq-stable

But its fail apt-secure(8) its set to dissable by default?

---

### Post by mastablasta on 2020-05-18
as user not as root. clearly base don the message you haven't created the 32bit prefix or you haven't installed to it. also make sure you have 32 bit libraries installed in ubuntu.

also you can try Playonlinux - it might be easier to manage wineprefixes there.

---

### Post by LMH1 on 2020-05-21
Playonlinux is poor i have tested it, its look like its hard to make old dos games or 16 bits app to works in linux.
[https://earthgaming.com/games/e-g-chess/eg-chess-pc-2/](https://earthgaming.com/games/e-g-chess/eg-chess-pc-2/)

[https://en.wikipedia.org/wiki/Witchaven_II:_Blood_Vengeance](https://en.wikipedia.org/wiki/Witchaven_II:_Blood_Vengeance)
How will you do to get this works with linux?

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
i have installed wine HQ but only icon works, not install so its works better with fedora 23 is it bug on ubuntu?

---

### Post by monkeybrain20122 on 2020-05-21
There are many chess games that run natively in Linux. [https://www.linuxlinks.com/chess/](https://www.linuxlinks.com/chess/)

---

### Post by Holger_Gehrke on 2020-05-21
For DOS-games like Witchaven II you don't use wine. There's dosbox for that. Since - unlike wine - dosbox **is** an emulator and emulates all the hardware of a PC up to the mid to late 90s (it can even be made to emulate the first generation of 3D-graphics boards, but not with the standard build found in the repositories) it can be rather sluggish unless you have a powerful machine. Since Witchaven is using the BUILD engine (the same engine as Duke 3D) it should *in theory* be possible to use eduke32 (a modern source port of that engine) to run it.

16 bit windows apps have the same problem in wine as all windows programs: some run great, some mostly work and some crash and burn. An example of a 16 bit app that runs just fine - even in a 64bit prefix - is the "know-how computer", a small VB program written for windows 3.1 that simulates a pen, paper and matches simulation of a simple CPU.

The chess program you link to is not a 16 bit app (at least not in the version available for download on that page) and runs just fine with playonlinux. Click on "Install a program" in the "actions" sidebar, click on the link "Install a non-listed program", select "Install a program in a new virtual drive", enter a name for the new virtual drive, leave the boxes in the next form unchecked (the Ubuntu default wine (3.0 on my XUbuntu 18.04) works fine and no unusual config or libraries were needed on my system), select "32 bits windows installation", wait a moment for the virtual drive creation, browse to the downloaded egchess.exe, run the installer, don't let the installer run the program, create a shortcut, and run it:
[ATTACH=CONFIG]285953[/ATTACH]

The great thing about PlayOnLinux is that you can use it to have multiple different version of Wine installed at the same time. This is a good thing because some programs only work with a very specific version of Wine and can't be made to run with any other.

Holger

---

### Post by mastablasta on 2020-05-22
for dos games i found DBGL to be helpful: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
if oyu are into old games, many old games have opensource ports that install in linux and let you run games natively. for example 
Doomsday engine (or Zandronum and few others) for Doom, Heretic, Hexen,
OpenMW for Morrowind,
OpenRA for Command and Conquer and Red Alert
OpenTTD  for transport tycoon deluxe
eduke32 was mentioned...

etc.

there are also some remakes available - like Oolite, Privateer Remake...

---

