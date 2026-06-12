---
title: "Astrology: Astrolog, Kastrolog, Maitreya, Skylendar, Cenon/Astro"
date: 2007-02-07
forum: General Help
---

### Post by altonbr on 2007-02-07
[SIZE=4]**WHAT I AM RUNNING**[/SIZE][LIST]
[*] Ubuntu Dapper 6.06.1 and,
[*] Windows XP[/LIST][SIZE=4]**ASTROLOG**[/SIZE]
**[COLOR=Red]*repository, .tar.gz, .exe*[/COLOR]**
url: [http://astrolog.org/astrolog.htm](http://astrolog.org/astrolog.htm) / [http://astrolog.offline.ee/astrolog/changed/changed.shtml](http://astrolog.offline.ee/astrolog/changed/changed.shtml)
version: **[COLOR=Red]*5.40*[/COLOR]** (Ubuntu repository); **[COLOR=Red]*5.41g*[/COLOR]** (Windows)[LIST]
[*] Great program, installed it from the repository
[*] The Linux version is considerably less advanced than the Windows version, and they're both out of date
[*][LEFT]Great log though [COLOR=SeaGreen]*[see attached]*[/COLOR]
[/LEFT]
[/LIST][SIZE=4]**KASTROLOG**[/SIZE][I]
**[COLOR=Red].rpm, .tar.gz[/COLOR]**[/I]
url: [http://www.paganlink.org/library/astrology/kastrolog.html](http://www.paganlink.org/library/astrology/kastrolog.html)
version: [COLOR=Red]***5.4-1.1***[/COLOR][LIST]
[*] Looks great...
[*] Installed by converting .rpm to .deb and,
[*] Installed from source
[*] Couldn't get either working[/LIST](Saravali) [SIZE=4][B]MAITREYA
[/B][/SIZE][COLOR=Red]***.tar.gz, .exe***[/COLOR]
url: [http://www.saravali.de/maitreya/index.html](http://www.saravali.de/maitreya/index.html)
version: [COLOR=Red]***4.1***[/COLOR][LIST]
[*] Looks great...
[*] Installed Windows version (didn't try Linux version)
[*] Mainly East Indian astrology
[*] Does have many Western charts, and not as advanced as I had hoped [but at least it worked][/LIST][SIZE=4]**SKYLENDAR**[/SIZE] [I]
**[COLOR=Red].tar.bz2[/COLOR]**[/I]
url: [http://skylendar.kde.org/frame.html](http://skylendar.kde.org/frame.html)
version: [COLOR=Red]***1.6.2***[/COLOR][LIST]
[*] Looked promising...
[*] Couldn't install from source[/LIST][SIZE=4][B]CENON/ASTRO module
[/B][/SIZE]**[COLOR=Red]*.tar.gz, .rpm*[/COLOR]**
url: [http://www.cenon.info/astro/index_gb.html](http://www.cenon.info/astro/index_gb.html)
version: [COLOR=Red]***3.82***[/COLOR] (Cenon); [COLOR=Red]***1.11 ***[/COLOR](Astro module)[LIST]
[*] Looks fantastic...
[*] NO idea what happened when I converted the program from .rpm to .deb and then ran them; I can seem to find the Linux exectutables anywhere
[*] No Windows version either[/LIST][SIZE=4]**LATITUDE/LONGTITUDE finder**[/SIZE]
url: [http://www.satsig.net/maps/lat-long-finder.htm](http://www.satsig.net/maps/lat-long-finder.htm)


So in conclusion, does ANYONE know of an advanced (Western) Astrological/Zodiac program that will work with Debian/Ubuntu???

---

### Post by altonbr on 2007-02-08
bump.

---

### Post by merlinus on 2007-04-23
Hi.  Hopefully you can help.

I used synaptic to download and install astrolog.  I can find the icon in /usr/games, but nothing happens when I click on it.

I can run it in a terminal window, input data, and get text-based results, but what about graphical charts?

No doubt I am spoiled, as I have been using WinStar Plus for years!

Many thanks!

-merlin

---

### Post by altonbr on 2007-04-25
> **merlinus said:**
> Hi.  Hopefully you can help.

I used synaptic to download and install astrolog.  I can find the icon in /usr/games, but nothing happens when I click on it.

I can run it in a terminal window, input data, and get text-based results, but what about graphical charts?

No doubt I am spoiled, as I have been using WinStar Plus for years!

Many thanks!

-merlin

I've been wondering the same thing myself, but no one seems to have any answers :S

---

### Post by eternal0void on 2008-01-15
Astrolog has a lot of command line options, and you have to use a couple of command line options to get graphical wheel charts.

If you just want the graphical chart onscreen, use -X.  For a reversed colors chart (black on white, saves ink when you print it) use -Xr.  To save the chart as a Windows bitmap, use -Xb.

Also, if you want to do some serious astrology [you should get the Ephemeris files]("http://www.astrolog.org/ftp/ephem/ephemall.zip").  Personally I don't know where to put the ephemeris files, but if you stick all of them in a folder, cd into that folder in a terminal window, and run astrolog from there, astrolog finds the ephemeris files.  Use the -b switch to use the Ephemeris files, though be sure to set the command line switches as "-X -b" rather than as "-Xb", as the combinations have different meanings.  If you want to use the Ephemeris files and save as a bitmap, use "-Xb -b".

---

### Post by altonbr on 2008-01-15
> **eternal0void said:**
> Astrolog has a lot of command line options, and you have to use a couple of command line options to get graphical wheel charts.

If you just want the graphical chart onscreen, use -X.  For a reversed colors chart (black on white, saves ink when you print it) use -Xr.  To save the chart as a Windows bitmap, use -Xb.

Also, if you want to do some serious astrology [you should get the Ephemeris files]("http://www.astrolog.org/ftp/ephem/ephemall.zip").  Personally I don't know where to put the ephemeris files, but if you stick all of them in a folder, cd into that folder in a terminal window, and run astrolog from there, astrolog finds the ephemeris files.  Use the -b switch to use the Ephemeris files, though be sure to set the command line switches as "-X -b" rather than as "-Xb", as the combinations have different meanings.  If you want to use the Ephemeris files and save as a bitmap, use "-Xb -b".

Never knew. Thank you for the tips!

---

### Post by Ariondys on 2008-03-17
I'm not going to be satisfied with astrolog 5.40 from the terminal.  I'm a ubuntu and linux noob, but that's totally weak.  Astrolog is sourced in C, can't we get astrolog 5.41g which I vastly prefer to astrolog32 to compile and then run it.  And how frustrated will I be after I try to do that?  I could barely even get ubuntu installed on my machine.

---

### Post by altonbr on 2008-03-17
> **Ariondys said:**
> I'm not going to be satisfied with astrolog 5.40 from the terminal.  I'm a ubuntu and linux noob, but that's totally weak.  Astrolog is sourced in C, can't we get astrolog 5.41g which I vastly prefer to astrolog32 to compile and then run it.  And how frustrated will I be after I try to do that?  I could barely even get ubuntu installed on my machine.

I can run Astrolog 5.41g through wine by right-clicking the .exe file and stating "Open with Wine Windows Emulator". Give that a try.

To install wine, you can find it in Applications > Add/Remove or by typing in:

```
sudo aptitude install wine
```

in a terminal (Applications > Accessories > Terminal).

Or, as eternal0void stated, run astrolog as 'astrolog -X' in the terminal to create a graphical output.

I've learned a lot since I made that original post, Wine is just a small bit.

Good luck!

---

### Post by Ariondys on 2008-03-18
I used Applications > Add/Remove -- I had to change it to Show "All Open Source applications", since wine was not in the list originally.  Then it installed itself no problem.
Retrieved the folder of astrolog I zipped and stuck in my email, extracted it and right clicked the .exe to open with the wine emulator, less than 5 minutes.  It doesn't behave identically of course, but considering this was my only goal for once I abolished my Windows XP to the void, I've got success.  Now I just have to see about this "fake" C: drive concept, because that's where the ephemeris file were supposed to sit c:/sweph/ephe I think.

---

### Post by altonbr on 2008-03-18
> **Ariondys said:**
> I used Applications > Add/Remove -- I had to change it to Show "All Open Source applications", since wine was not in the list originally.  Then it installed itself no problem.
Retrieved the folder of astrolog I zipped and stuck in my email, extracted it and right clicked the .exe to open with the wine emulator, less than 5 minutes.  It doesn't behave identically of course, but considering this was my only goal for once I abolished my Windows XP to the void, I've got success.  Now I just have to see about this "fake" C: drive concept, because that's where the ephemeris file were supposed to sit c:/sweph/ephe I think.

Wine's fake C: drive is in '/home/$USER/.wine/drive_c'. To view your hidden files (and therefore '.wine'), hit Alt + H on your keyboard. Then you can navigate from there.

Hope that helps!

---

