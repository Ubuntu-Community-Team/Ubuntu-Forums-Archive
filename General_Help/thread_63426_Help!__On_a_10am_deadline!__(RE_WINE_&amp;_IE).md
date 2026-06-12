---
title: "Help!  On a 10am deadline!  (RE: WINE &amp; IE)"
date: 2005-09-07
forum: General Help
---

### Post by orev on 2005-09-07
I love ubuntu.  I really enjoy working with it.  I am however, having a  devil of a time getting IE running.  (I need IE for business portals)

I have searched quite a bit on the forums for methods of installing wine, winetools, sidenet, ie4linux, Crossover office.

I would like to avoid the use of Crossover office if I can...not because I don't think people should be able to make money off of open source...  (for reference, how do I install the .sh file for Crossover office?  I thought I would be able to run it directly from the terminal, but I didn't have any luck...?)

I have not able to find a HOWTO that has got wine or winetools up and running on my system.  I would love some advice in this area...  (I seem to have got wine going, but I can't seem to install IE via winetools or any other method!!??)

I understand that alot of people prefer sidenet to winetools for wine config, but I am not sure what to do with the file I download from the sidenet site...?

ANY HELP HERE WOULD BE GREATLY APPRECIATED.  I WILL BE AT THE OFFICE TONIGHT UNTIL I FIX THIS PROBLEM....

THANKS!!!

---

### Post by John.Michael.Kane on 2005-09-07
[http://www.von-thadden.de/Joachim/WineTools/index.html#install](http://www.von-thadden.de/Joachim/WineTools/index.html#install)

hope this helps

---

### Post by arnieboy on 2005-09-07
[QUOTE=orev]I love ubuntu.  I really enjoy working with it.  I am however, having a  devil of a time getting IE running.  (I need IE for business portals)

I have searched quite a bit on the forums for methods of installing wine, winetools, sidenet, ie4linux, Crossover office.

I would like to avoid the use of Crossover office if I can...not because I don't think people should be able to make money off of open source...  (for reference, how do I install the .sh file for Crossover office?  I thought I would be able to run it directly from the terminal, but I didn't have any luck...?)

I have not able to find a HOWTO that has got wine or winetools up and running on my system.  I would love some advice in this area...  (I seem to have got wine going, but I can't seem to install IE via winetools or any other method!!??)

I understand that alot of people prefer sidenet to winetools for wine config, but I am not sure what to do with the file I download from the sidenet site...?

ANY HELP HERE WOULD BE GREATLY APPRECIATED.  I WILL BE AT THE OFFICE TONIGHT UNTIL I FIX THIS PROBLEM....

THANKS!!![/QUOTE]

try doing a 
```
chmod 755 crossoverinstallerfile.sh
```
and then running it again from terminal as:
```
./crossoverinstaller.sh
```

---

### Post by mlomker on 2005-09-07
I tried Crossover office and it's nothing more than a well scripted version of wine.  Even at that it only supports old versions of IE...assuming you can make that work.  I could never manage to do it.

If you need IE on your machine and it has some horsepower then you could get a copy of VMWare  Workstation and simply have a copy of Windows running on Ubuntu.  If you have a new PC then VMWare runs quite fast...especially if you install one of the older versions of Windows on it.  They have a 30-day demo that can be downloaded online.  You do need kernel headers and it is installed from the command line, but it's not too bad.

---

### Post by ltmon on 2005-09-07
The first half of my howto here: [http://ubuntuforums.org/showthread.php?t=54971](http://ubuntuforums.org/showthread.php?t=54971) deals with getting wine and IE to work on hoary.

There seem to be many ways to do it... but this one worked for me.

L.

---

### Post by orev on 2005-09-14
[QUOTE=ltmon]The first half of my howto here: [http://ubuntuforums.org/showthread.php?t=54971](http://ubuntuforums.org/showthread.php?t=54971) deals with getting wine and IE to work on hoary.

There seem to be many ways to do it... but this one worked for me.

L.[/QUOTE]


I was able to use this to get WINE up and running great - and even IE.  However, I could not get some websites to work properly, or at all.  In particular, database driven websites where I input data into a popup (not sure what the server side language is).  IE also crashed alot - when adding favorites, navigating, and just for fun (apparrently).

Unfortunetly, I have had to reinstall WinXP on one of our office boxes just for these websites.  (It sucks, I don't even own a copy of Win. - WinXP took over 45 min. to install on a new Dell, and then about another 2 hrs of updates and rebooting...and some people think ubuntu is HARD!)

I emailed the IT departments of both companies websites to let them know that standards compliant sites might be in thier interest....

---

