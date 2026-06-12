---
title: "Help me migrate!"
date: 2007-01-09
forum: General Help
---

### Post by johnwillis on 2007-01-09
Hiya guys,

THe last few times I've posted on Linux forums I have always ended up getting the help I needed.

Right, after using Linux of and on since SUSE 7.2 I have decided to go 100% Linux. However I do have a few problems that need working out...

I currently develop in Visual Studio 2005 for uni, this will not be a problem as I will use VMWARE server and a virtual copy of Windows.

Also I need to produce Gantt Charts (Like MS Project) what can I get for Linux that will do the job?

Also I need to produce UML and Graphical diagrams such as ones I have produced in MS Visio - any ideas again?

I don't want to run Visio and Project in VMWARE if I can absolutley help it as it don't really help if I keep reverting back to Big Bill every time I want a diagram.

My last query is that I need an alternative to Nero Vision Express - a program that allows be to take a file - in most my cases a DIVX held within either an AVI/MPEG file and create a normal DVD to play on my DVD Deck in my lounge. Now this is a very simple process in windows so hopefully someone somewhere knows how I can do this. I think someone mentioned something about KINO??? But when I looked at it to me it seems like it's to take footage of a DV Camcorder.

Many Thanks For Your Help Guys/Gurls.

I Look Forward To Coming To The Enlightened Side!

- JW

---

### Post by pay on 2007-01-09
> **johnwillis said:**
> THe last few times I've posted on Linux forums I have always ended up getting the help I needed.Why does that matter? It sounds like you don't think that people on this forum are capable of helping you.

Look at this guide for converting to dvd [http://forum.videohelp.com/viewtopic.php?t=242455](http://forum.videohelp.com/viewtopic.php?t=242455)
There also this more advanced guide [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html)Or for simplicity```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf \
  -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 \
  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:\
keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25 \
  -o movie.mpg movie.avi
```

---

### Post by Rabbuk on 2007-01-09
i think hes giving credit to your abilities not doubting them.

---

### Post by Phesto on 2007-01-10
And you can check this thread out for the answer to your replacement for visio to make UML diagrams
[http://ubuntuforums.org/showthread.php?t=333911]("http://ubuntuforums.org/showthread.php?t=333911")

---

### Post by johnwillis on 2007-01-10
thanks for all your help guys.

also when i meant i had always got an answer i was offering my praises, the linux community and esp the ubuntu / debian one on a whole is awesome at helping each other.

if i ever have a problem i know that someone is out there that knows the answer.

i now use Dia and Umbrello and I am also looking into the dvd options you've highlighted...


many thanks

- JW

:-D

---

### Post by randomnumber on 2007-01-10
I like eclipse and DIA. I think that maybe related

---

### Post by Delkster on 2007-01-10
> **johnwillis said:**
> Also I need to produce Gantt Charts (Like MS Project) what can I get for Linux that will do the job?

You might want to try Planner. It's available in Add/Remove Applications, and the package name is "planner". I haven't used it myself, though.

---

### Post by nix4me on 2007-01-10
Dia for diagrams.
Devede for converting files to dvd format.

nix4me

---

