---
title: "Can I run 1990s MS Dos program (i.e. exe)?"
date: 2022-01-19
forum: General Help
---

### Post by seeker.k3 on 2022-01-19
In the mid-1990s I was using MS Windows 3.11, and I used to run a program in MS DOS (I think it was DOS 6.0), but it stopped working under later Windows versions. I've been using Xubuntu for several years and I recently found I can still download that program as an exe file from a university server, and I'm wondering if I could get it to work in Xubuntu. Yes, no, not likely, possibly? How would I do that? Could someone please point me at it?

Cheers.

---

### Post by yetimon_64 on 2022-01-19
It may be possible with "dosbox". I run old win 3.11 dos games like "Prince of Persia" and "Crystal Caves" etc with it on Xubuntu 20.04. It may possibly work for you, no guaranties though with such old programs. I have had a couple of the many old games I've tried running under dosbox fail miserably, most have worked fine though.

To install ...```
sudo apt install dosbox
```

**Edit:** you may also need to install "wine" as well. I just checked my "Prince of Persia" launcher exec line ...
```
env WINEPREFIX="/home/yetiman/.wine" wine-stable start /unix /home/yetiman/.wine/drive_c/Games/PoP/PoP1_10/Prince.exe megahit
```
This runs in dosbox but seems I installed all my old games in the windows path within wine. You may also need to install "wine" as well. when I launch the game I see the "dosbox" splash screen first then the game launches.

Good luck, yeti. :-)

---

### Post by CatKiller on 2022-01-19
As well as Wine and DOSBox, which are great suggestions, DOSEmu would be another one to try. DOSBox is mostly geared towards games, and DOSEmu is geared towards accuracy for generic programs. If it *is* a game that you're trying to run, there may be a reimplementation of it that would work better - for example ScummVM for old adventure games, or the many modernised Doom engines.

---

### Post by guiverc on 2022-01-19
I created a program *long ago* under OS/2 that would also work on CP/M & PC-DOS 5.02 (*multiple compiled executables were created*) and kept it running on a really old *80286*, till it died & was replaced by a *80486* which likewise died & is currently an early *pentium* (*I think*).  These boxes are old & used coax networking.

My old DOS box is still there, but I years ago setup an old thinkpad t42p next to it that runs Ubuntu 18.04 (Xubuntu, Lubuntu & Ubuntu-MATE & maybe more desktops will be installed; but not GNOME), and I've been using that instead to run the DOS .exe program.  I used this instead as it can copy the updated files to my server(s) without me needing to power up network hubs to convert the coax cables connection into ethernet cable I use today..

I run my app using `**dosbox**` as already mentioned in prior replies.  I started using dosbox around Ubuntu 10.10 & it still runs my .exe even today on *jammy* (*or what will be 22.04 on release*) which has allowed me to be lazy & not re-write that prehistoric code written very mid/late 80s if not early 90s.

---

### Post by seeker.k3 on 2022-01-20
dosbox :P

Thank you to all who have offered suggestions here. I didn't get dosemu to work (actual dosemu didn't work), probably related to paths, but I didn't spend too much time with it before I tried dosbox, which worked straight away, and from there was able to run the program I wanted. It worked perfectly for me. I didn't need to install wine.

My program was written in 1992, and it is a collection of quizzes to help me learn Japanese kanji. It's called ktutor (from Johns Hopkins). I haven't studied Japanese language for 25 years, but I want to pick it up again, and I remembered that little program, which was particularly helpful. I am extremely pleased to get it going again, with a little help from you---thanks again. It was surprisingly easy.

---

### Post by Dennis N on 2022-01-20
Although this question is marked solved, it's worth noting that there is also **DoxBox-X**:

> DOSBox-X emulates a PC necessary for running many DOS games and applications that simply cannot be run on modern PCs and operating systems, similar to DOSBox. However, while the main focus of DOSBox is for running DOS games, DOSBox-X goes much further than this. Started as a fork of the DOSBox project, it retains compatibility with the wide base of DOS games and DOS gaming DOSBox was designed for. But it is also a platform for running DOS applications, including emulating the environments to run Windows 3.x, 9x and ME and software written for those versions of Windows.


---

### Post by dragonfly41 on 2022-01-20
> [COLOR=#000000]I haven't studied Japanese language for 25 years, but I want to pick it up again[/COLOR]
If the goal is to study Japanese language then I suggest trying latest AntConc in Ubuntu,

[https://www.laurenceanthony.net/software/antconc/](https://www.laurenceanthony.net/software/antconc/)

Professor Laurence Anthony is developer based in Japan.

---

### Post by seeker.k3 on 2022-01-20
Thanks for these further suggestions. Both of these could be helpful---I have a couple of other old programs that I'd like to resurrect.
Cheers.

---

