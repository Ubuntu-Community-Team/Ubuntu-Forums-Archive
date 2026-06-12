---
title: "amarock"
date: 2008-07-07
forum: General Help
---

### Post by jkid on 2008-07-07
every time i play a music the player freezes:confused:

---

### Post by L337_K3y5 on 2008-07-07
I have slight problems with it every now and then, if it gets bad, just install a different media player.

---

### Post by jkid on 2008-07-07
help with amarock every  time i play a song it freezes

---

### Post by barbedsaber on 2008-07-07
amarok aint that good, all I can suggest is that you install everything with xine in the name, (worked for me, before I switched ti banshee, but I think I will try rhythm box now)

---

### Post by p_quarles on 2008-07-07
Moved to General Help. 

> **jkid said:**
> help with amarock every  time i play a song it freezes
Can you be a little more specific about what you've done so far? What format is the song, and what codecs do you have installed?

> **barbedsaber said:**
> amarok aint that good,
Untrue. Perhaps you've had a bad experience, but it's popular for a reason. In any case, the answer you gave is fairly counterproductive.

---

### Post by cyclobs on 2008-07-08
> **barbedsaber said:**
> amarok aint that good, all I can suggest is that you install everything with xine in the name, (worked for me, before I switched ti banshee, but I think I will try rhythm box now)

i use amarok here and i find it quite good, tho i don't like the on screen display so i turn that off :)

---

### Post by mc4man on 2008-07-08
i think Amarok is great, very flexible in how you use it. 
Make sure you have medibuntu as a software source, to ck. go system -> administration -> software sources -> third-party software. If it's not listed and checked then go here and follow dir. for ver. of ubuntu you're using.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then run ```
sudo apt-get install w32codecs 
```
Because you didn't mention what ver. of ubuntu you have i didn't include in above but open synaptic and search libxine1 - install the plugin package (libxine1-misc-plugins in hardy)
if still having trouble try going home dir. (show hidden files) -> .kde/share/config and delete the amarokrc file. Then restart Amarok and see.

---

### Post by daleus on 2008-07-08
Go into Ubuntu Sound options, set everything to Alsa. Amarok won't work if you don't change it and have another program that uses sound open (basically most programs).

---

### Post by jkid on 2008-07-10
[COLOR="Blue"]**hardy....and any song format that i play it crashes ....when i re-installed it works like for a couple hours but then it crashes again **[/COLOR]

---

### Post by bapoumba on 2008-07-10
Threads merged.

---

### Post by Elfy on 2008-07-10
You say you reinstalled, but did you remove the folder in your home as advised?

Do that and try again with it - if you still get problems run it from a terminal with

```
amarokapp
```

leave the terminal alone and if amarok crashes post what the terminal has regarding the error

---

### Post by funnypanks on 2008-07-10
its a pulse problem. i dont know why they make us use that when its obviously not ready.

to fix ur prob (if its the same one i had)
open amarok
click setting
click configure amarok
on the left pane click engine
then change output plugin from "autodetect" to "alsa"
click ok
then close amarok and reopen it, u should be good

---

