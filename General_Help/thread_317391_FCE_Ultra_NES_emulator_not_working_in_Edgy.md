---
title: "FCE Ultra NES emulator not working in Edgy"
date: 2006-12-12
forum: General Help
---

### Post by Athanasius on 2006-12-12
I am not able to get the FCE Ultra NES emulator to load a rom.  I downloaded the one from the repos.  The GFCE front-end loads but it won't execute any .nes files.  Help.

---

### Post by Athanasius on 2006-12-12
is there maybe a better NES emulator for Linux?

---

### Post by Fibonacci on 2006-12-27
There should be, but I don't know about it since I've always used FCEU.
FCEU **does** work on Edgy (just tested it), it's gFCEU that doesn't - no idea why. You should be able to load .nes roms from the command line as follows:
```
fceu -sound 1 /path/to/rom.nes
```
But, since FCEU uses OSS sound output, it hogs the sound device (just as Flash and Skype did until recently); so I think it should be better to run instead:
```
aoss fceu -sound 1 /path/to/rom.nes
```

Hope this helps,

-Fibo

---

### Post by Fibonacci on 2006-12-29
Okay, I think I found and fixed the problem. Download the attached Python script, gunzip it, and put it on /usr/bin. However, I don't know Python so I can't be trusted - I advise backing up the original /usr/bin/gfceu before replacing it with this script.

---

### Post by punkrockguy318 on 2007-01-01
Download and install the latest version of GFCEU to solve these bugs
[http://s189529521.onlinehome.us/gfceu/](http://s189529521.onlinehome.us/gfceu/)

---

### Post by punkrockguy318 on 2007-01-01
Argh!  That problem has been fixed for ages in svn, but it never made it to a release.  I'll release a new version tonight with these problems fixed.  Sorry.

---

### Post by punkrockguy318 on 2007-01-01
Fixed in 0.6.0

---

### Post by punkrockguy318 on 2007-01-05
The URL has moved.  You can now download the latest version of gfceu at [http://dietschnitzel.com](http://dietschnitzel.com)

---

### Post by Athanasius on 2007-01-24
The new version works wonderfully, Thank you!

---

### Post by punkrockguy318 on 2007-01-24
good to hear

---

### Post by Athanasius on 2007-01-29
now they should have something like this for dgen (Sega Genesis emulator)

---

