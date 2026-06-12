---
title: "Installing Programs"
date: 2007-09-19
forum: General Help
---

### Post by tsumiro on 2007-09-19
hey, ive been trying to install multiple linux programs, and all of them end up needing to be manually compiled, which is a pain, because the instructions that are sent never seem to work when i use them, the commands never work, or "dont exist"

plz. i need some help

im usin feisty...


thx.

---

### Post by kaamos on 2007-09-19
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by tsumiro on 2007-09-19
i dont have internet on my linux box... do you need the internet to use the add/ remove thing?.... ugh, its embarrasing asking these questions, but i dont use linux that much. (its mostly embarrassing cuz i know some unix, /coding, etc)

anyway, ive been downloading programs off of sites, using my mac, and then usin a thumb drive to transfer the files (files with names like: lmms-0.3.0.tar.bz2) which seem to end up having all this source stuff thats not compiled. (im begging to miss the neat .exe... heh, like mcdonalds vs. a resturant... lol...)

---

### Post by ijason on 2007-09-19
yep. all of the various apt-get and package manager programs require internet access to be successful.  

what you'll usually get in tarballs is files that need to be compiled somehow. but if you look for .deb files they can usually be installed in single steps, often with a nice GUI by double-clicking them in the file manager. so, try searching for .deb :)

---

### Post by aysiu on 2007-09-19
Yes. Linux without an internet connection is crippled, especially if you want to install programs.

---

### Post by tsumiro on 2007-09-19
NOOOOOOOOOOO!!!!!!


ah well....


heres an example of one of the howto install txts that usually come with these things...

this one happens to be for compiz

it says type in autogen.sh

then "standard build procedures"

make
make install

I DONT UNDERSTAND.

i wanna cry a lil bit.

---

### Post by aysiu on 2007-09-19
It's a shame you didn't see [Is Ubuntu for You?](http://ubuntuforums.org/showthread.php?t=63315) before you tried it. Here's an excerpt: > P.P.S. If you don't have internet access (or have dial-up and little patience with hours of downloading), then please don't use Ubuntu. Software installation and updates will be painful if not impossible.

---

### Post by tsumiro on 2007-09-19
the reason i dont have internet on my linux box is that my wireless card doesnt have drivers for linux... so no internet.


WAH>>>

ubuntu has the drivers for an airport extreme card tho right? cuz im installing ubuntu on my g4 mac.

---

### Post by aysiu on 2007-09-19
> **tsumiro said:**
> the reason i dont have internet on my linux box is that my wireless card doesnt have drivers for linux... so no internet.


WAH>>>

ubuntu has the drivers for an airport extreme card tho right? cuz im installing ubuntu on my g4 mac.
It can be done as a workaround, but I don't think native Ubuntu will have the proprietary drivers necessary to work with Airport Extreme.

A search like [this](http://www.google.com/search?hl=en&q=howto+airport+extreme+g4+site%3Aubuntuforums.org&btnG=Google+Search) may help you, though.

---

### Post by Shazaam on 2007-09-19
Cable or DSL? Both modems should come with an ethernet port on the back. Could do a hardwire to your pc's ethernet port if it has one to get your updates.
Unless your sitting in an internet cafe :)

---

### Post by tsumiro on 2007-09-19
> **aysiu said:**
> 
A search like [this](http://www.google.com/search?hl=en&q=howto+airport+extreme+g4+site%3Aubuntuforums.org&btnG=Google+Search) may help you, though.


sorry, i feel like a total *** for just asking without doing a whole lotta research, i just really wanna get started with linux, but it means erasing everything on my computer, and backing up my stuff, and i just need to know quickly whether or not, the time im gonna spend preparing my stuff is worth it.

ill see what i can find...

---

### Post by tsumiro on 2007-09-19
well, looks like ill never be able to become a proper linux user. i cant use wires cuz of my positon in my house, so i use wireless, and it seems that linux doesnt support either of my wireless cards, so i guess thats it. im not gonna redo my entire computer, so i can use a workaround to get my wireless card working on my mac, so i guess this is goodbye.

maybe when i see that there's support for my cards, or when i can wire my computers, ill come back. ill do somemore research and hope, but i highly doubt ill ever really be able to use linux.

its a shame cuz i really wanted to use linux.

sorry if this sounds depressing:):):), but i am kinda depressed.... :(

---

### Post by tsumiro on 2007-09-19
very very happynow.

found out about reverse engineered drivers for the airport extreme card.

maybe linux will come sooner than i thought...

---

### Post by tsumiro on 2007-09-20
apparently, for some reason, when i run configure in the progams i download, the c compiler cannot make the executeable...

---

### Post by Maestro23 on 2007-09-20
> **tsumiro said:**
> apparently, for some reason, when i run configure in the progams i download, the c compiler cannot make the executeable...

Do you have build-essential installed?

> sudo apt-get build-essential

Might need gcc (C compiler) installed as well.  Can do it thru Synaptic (GUI) or command line.

Compiling from source in Feisty Guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code)

---

### Post by tsumiro on 2007-09-20
where can i download those two apps???

as i said before, i have no internet for this box......

---

### Post by Maestro23 on 2007-09-20
> **tsumiro said:**
> where can i download those two apps???

as i said before, i have no internet for this box......

Didn't see the post where you said no internet.  You can download the programs from Ubuntu packages.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

*Make sure you get all the dependencies as well.  It will let you know what is needed.

---

### Post by aysiu on 2007-09-20
*build-essential* should be on the installer CD. In the terminal, type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
``` Ordinarily, you'd copy and paste commands instead of retyping them, but you don't have an internet connection right now...

---

### Post by Maestro23 on 2007-09-20
> **aysiu said:**
> *build-essential* should be on the installer CD. In the terminal, type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
``` Ordinarily, you'd copy and paste commands instead of retyping them, but you don't have an internet connection right now...

Wasn't sure if build-essential was on the CD.  Thanks aysiu. :smile:

---

### Post by aysiu on 2007-09-20
> **Maestro23 said:**
> Wasn't sure if build-essential was on the CD.  Thanks aysiu. :smile:
Well, I think it still is.

It's only *ndiswrapper* they took off the CD for whatever reason.

---

### Post by dark_harmonics on 2007-09-20
I was just goint to suggest that he try ndiswrapper to get his card working. I know it helped my dad install his wireless card. Checking your hardware for compatibility before migration is always a headache saver. You should focus on fixing your internet because compiling everything is just going to make you either very smart or make you very angry at your computer. :lolflag:

---

