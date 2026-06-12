---
title: "How do you install .tar.gz files?"
date: 2014-01-03
forum: General Help
---

### Post by d-wall08 on 2014-01-03
I'm wondering if theres a program I can download to install some .tzr.gz games i downloaded.

---

### Post by papibe on 2014-01-03
Hi d-wall08.

A tar.gz file is like a zip file. First you need to uncompress it. Open it on Nautilus (file manager) and extract the files.

After that, there's no rule. Looks for files that detail the instructions. They are usually named like:
```
README
Instructions
ReadThisFirst
```
or alike.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by d-wall08 on 2014-01-06
Didn't work, the install, or in this case paintball2 file wouldn't open. I uncompressed it and tried looking for some installation.

---

### Post by Yellow Pasque on 2014-01-06
A link to what you're trying to install could prove helpful...

---

### Post by d-wall08 on 2014-01-06
[http://sourceforge.net/projects/paintball2/?source=dlp](http://sourceforge.net/projects/paintball2/?source=dlp) Theres the download link. I have the .tar.gz file. when i uncompressed it and clicked on the paintball2 file, nothing happened. Is there a program I can get to install .tar.gz files? Please help. Thanks.

---

### Post by Yellow Pasque on 2014-01-06
No, you can't get a program to install .tar.gz files. You can only uncompress them and then you have to figure out what to do with the files inside. Luckily for you, this one's a pre-compiled binary that's ready to run.
I find the command line easier when dealing with tarballs.
```
tar xzf paintball2_build040_linux_full.tar.gz
cd paintball2/
./paintball2
```

---

### Post by d-wall08 on 2014-01-06
didn't work. how bout installing wine and downloading an .exe

---

### Post by mc4man on 2014-01-06
> **d-wall08 said:**
> didn't work. how bout installing wine and downloading an .exe
"didn't work" is so informative
It may work thru wine, may not
As far as on ubuntu 12.04 should work ok, at least on 32 bit install
You need libjpeg8 installed & if wishing sound then libsdl1.2 also installed

Then at the prompt of the extracted folder - 
```
./paintball2 +snd_driver sdl
```
The first time opening may take up to 30 sec while it finds the correct libGL.so
For 64 bit you may need to install some i386 libs

(on 14.04 64 bit can get the game to run but sound isn't going to happen, libsdl1.2debian, (i386 package) will just crash the game

---

### Post by monkeybrain20122 on 2014-01-06
The tarball is just an archive, like a zip file. It can contain anything: source codes, binary, install scripts, none of the above. You don't "install a tarball" unless there is something to be installed in the archive. In this case there is nothing to be installed. Just unzip the file (right click, extract here) and click the file "paintball" it would open (if not right click > Properties > Permission and make sure that it is executable.

It runs but there is no sound and if you start it with the command line as Temujin you get 

```
LoadLibrary("./snd_oss.so")
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.
```

[http://dplogin.com/forums/index.php?action=profile;u=11760;sa=showPosts](http://dplogin.com/forums/index.php?action=profile;u=11760;sa=showPosts)

Edited: there is still no sound and same error with
```
./paintball2 +snd_driver sdl
```

---

### Post by d-wall08 on 2014-01-06
i installed it with wine, when I open it I get an error, "Error during installation, make sure you have an open GL capable video card and that the latest drivers are installed" Not sure what to do. I'm actually having alot of trouble installing any game on here. Nothing seems to work and the Terminal commands don't work either.

---

### Post by Yellow Pasque on 2014-01-06
maybe try it with padsp
```
padsp paintball2
```

---

### Post by mc4man on 2014-01-06
I happen to have a 32 bit 12.04 install (nvidia 8400m using nouveau) & the game runs fine with sound using what I posted.

(the padsp paintball2 or padsp ./paintball2 will not work with this app, sdl will

---

### Post by mc4man on 2014-01-06
Did get sound to work thru alsa - for that it needs libasound2-plugins, if on 64 bit then the 32 bit package needs to be installed
( a start command that use a + for audio only needs to be used once. After that is written to the config file which by default would be in the extracted paintball2 folder, ie. - 
/paintball2/pball/configs/config.cfg

line is - (for alsa
seta snd_driver "alsa"

---

