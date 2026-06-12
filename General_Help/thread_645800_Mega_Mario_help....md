---
title: "Mega Mario help..."
date: 2007-12-20
forum: General Help
---

### Post by Moonfrost on 2007-12-20
Does anybody know how to install Mega Mario on Gutsy? because there's a debian package for Ubuntu on the official site (piece of cake) but it tells me that it's not compatible with my version of Ubuntu (7.10)!!!...so I downloaded the source and asked everywhere and nobody answers me how the hell do I compile it? I try all the time and it always comes up with some error!!...anyway, I really want to play this if anybody know how to install it that would be awesome!

---

### Post by jocko on 2007-12-20
> **Moonfrost said:**
> Does anybody know how to install Mega Mario on Gutsy? because there's a debian package for Ubuntu on the official site (piece of cake) but it tells me that it's not compatible with my version of Ubuntu (7.10)!!!...so I downloaded the source and asked everywhere and nobody answers me how the hell do I compile it? I try all the time and it always comes up with some error!!...anyway, I really want to play this if anybody know how to install it that would be awesome!

[COLOR=Black]I just had to try it out... This is how I got it running (figured it out from the "linux.txt" file included in the source) :
First you need to install some dependencies:
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev
```(I don't know if you need all of these, and I may have missed some that I already had installed before)
Unpack the .zip file to your desktop (or wherever you want it) then install with these commands:
[/COLOR]```
[COLOR=Black]cd ~/Desktop/MegaMario_v1.5_w32_linux/
make PREFIX=/usr/local
sudo make PREFIX=/usr/local install[/COLOR]
```

---

### Post by Moonfrost on 2007-12-20
> **jocko said:**
> [COLOR=Black]I just had to try it out... This is how I got it running (figured it out from the "linux.txt" file included in the source) :
First you need to install some dependencies:
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev
```(I don't know if you need all of these, and I may have missed some that I already had installed before)
Unpack the .zip file to your desktop (or wherever you want it) then install with these commands:
[/COLOR]```
[COLOR=Black]cd ~/Desktop/MegaMario_v1.5_w32_linux/
make PREFIX=/usr/local
sudo make PREFIX=/usr/local install[/COLOR]
```


Ok...these are the same instructions I got from somewhere else...the libraries are all there and installed no problem but for example...make PREFIX=/usr/local does not work if I don't specify anything (sorry but I'm kinda new to Ubuntu and never had the opportunity of compiling anything on SUSE) so I put the folder's name (just Mega Mario without the version number or anything) and it tells me make: *** No targets specified and no makefile found.  Stop.

cd ~/Desktop/MegaMario_v1.5_w32_linux/, this command (by changing MegaMario_v1.5_w32_linux) to Mega Mario still doesn't work at all...it says "No such file or directory" even though it exists right there on the Desktop...

---

### Post by jocko on 2007-12-20
> **Moonfrost said:**
> Ok...these are the same instructions I got from somewhere else...the libraries are all there and installed no problem but for example...make PREFIX=/usr/local does not work if I don't specify anything (sorry but I'm kinda new to Ubuntu and never had the opportunity of compiling anything on SUSE) so I put the folder's name (just Mega Mario without the version number or anything) and it tells me make: *** No targets specified and no makefile found.  Stop.

cd ~/Desktop/MegaMario_v1.5_w32_linux/, this command (by changing MegaMario_v1.5_w32_linux) to Mega Mario still doesn't work at all...it says "No such file or directory" even though it exists right there on the Desktop...

Do you mean you renamed the folder to "Mega Mario" (with a space in the name)?
Then rename the folder to something without a space and try again.
Or type the path like this:
```
cd ~/Desktop/Mega\ Mario/
```

Spaces in names of files and folders will confuse the command line.
It interprets "cd ~/Desktop/Mega Mario" as "cd ~/Desktop/Mega" followed by some nonsense text "Mario" that it ignores.

---

### Post by Moonfrost on 2007-12-21
> **jocko said:**
> Do you mean you renamed the folder to "Mega Mario" (with a space in the name)?
Then rename the folder to something without a space and try again.
Or type the path like this:
```
cd ~/Desktop/Mega\ Mario/
```

Spaces in names of files and folders will confuse the command line.
It interprets "cd ~/Desktop/Mega Mario" as "cd ~/Desktop/Mega" followed by some nonsense text "Mario" that it ignores.

No I never changed it...it came like that inside the .zip...but yeah, I just renamed it to lower caps without a space in the middle and it worked but when I start the game it just crashed the whole computer and can't even get out of X...anyway, thanks for the help

---

### Post by disturbedite on 2007-12-21
apparently the ubuntu deb package has disappeared from getdeb.  (where the official mm site links to for the deb download).

if you have it Moonfrost, could you post it?  i'd like to try it, but i'm feeling a little lazy as far as compiling it is concerned...

---

### Post by Moonfrost on 2007-12-21
> **disturbedite said:**
> apparently the ubuntu deb package has disappeared from getdeb.  (where the official mm site links to for the deb download).

if you have it Moonfrost, could you post it?  i'd like to try it, but i'm feeling a little lazy as far as compiling it is concerned...

Me too...I hate compiling because all the packages seem to have different commands...unfortunately I don't have the .deb package since I just found out about this specific Mario clone a few days ago and when I checked the .deb package was gone too...I think I'll wait and see if they upload it again...I compiled the thing successfully but I must have done something wrong because I get to the main menu and then freezes...around 10 minutes later it comes back but when I try to start a game the whole PC freezes and I have to force it off...

---

