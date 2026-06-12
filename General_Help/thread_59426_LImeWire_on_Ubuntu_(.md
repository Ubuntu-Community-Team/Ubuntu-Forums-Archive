---
title: "LImeWire on Ubuntu :("
date: 2005-08-23
forum: General Help
---

### Post by Koba on 2005-08-23
ok, i have tryed at least two methods for installing limewire on Ubuntu, and still nothing, i have tryed a expert Ubuntu user's way of installing it, and nope, nothing, and then i tryed the official LimeWire installation help by Ubuntu itself, and still, nope, the most i have ever seen LimeWire do after i install it, is flash a few lines and then nothing happens... i have jre installed, and LimeWire seems to be successfully installed... so i dunno, can someone give me some advice? i just started with Ubuntu today, but i have been using other linux systems before.

---

### Post by woedend on 2005-08-24
just get gtk-gnutella from the synaptic library.  doesn't answer your question but its a lot faster to load than limewire.

---

### Post by Koba on 2005-08-24
k thanks dude, after KDE finishes with apt-get i'll try that out, does it have a ui interface like limewire or is it pure console? doesn't really matter either way.

---

### Post by woedend on 2005-08-24
[QUOTE=Koba]k thanks dude, after KDE finishes with apt-get i'll try that out, does it have a ui interface like limewire or is it pure console? doesn't really matter either way.[/QUOTE]
 no no all GUI.  May not be as 'pretty' as limewire but sure as hell will run faster, easy to install (2 clicks away).

---

### Post by Mgcross on 2005-08-24
[QUOTE=Koba]ok, i have tryed at least two methods for installing limewire on Ubuntu, and still nothing, i have tryed a expert Ubuntu user's way of installing it, and nope, nothing, and then i tryed the official LimeWire installation help by Ubuntu itself, and still, nope, the most i have ever seen LimeWire do after i install it, is flash a few lines and then nothing happens... i have jre installed, and LimeWire seems to be successfully installed... so i dunno, can someone give me some advice? i just started with Ubuntu today, but i have been using other linux systems before.[/QUOTE]

Strange. I just downloaded the Linux binary, unzipped it to my home folder, made a shortcut to runlime.sh and fired it up...works just fine.

How did YOU install it?

---

### Post by weird_c00kie on 2006-10-13
why don't you use frostwire?
i just installed it and it works perfectly fine... as it should, given that it's a limewire clone :)

you can follow this thread for it:
[http://www.ubuntuforums.org/showthread.php?t=215868](http://www.ubuntuforums.org/showthread.php?t=215868)

:)

---

### Post by drezha on 2006-10-13
weird cookie beat me.

Frsotwire is exactly the same but blue as far as I can tell...

---

### Post by zapcojake on 2006-10-31
Hello, there is a glitch with runlime.sh.  #!/bin/sh needs to be #!/bin/bash
The runlime.sh is the script that runs limewire for you.  it will most likely be in /opt/limewire/

---

### Post by ~LoKe on 2006-10-31
> **drezha said:**
> weird cookie beat me.

Frostwire is exactly the same but blue as far as I can tell...

And none of that annoying pro crap.

---

### Post by ashmew2 on 2006-11-09
1.) Check you're java version:

Code: java -version

2.) You're java should look like this:

frog@kubuntu:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
frog@kubuntu:~$

3.) If not install Sun Java JRE from the repositories both Frostwire and Limewire require Java version 1.5.0 or greater as o:

Code: sudo apt-get install sun-java5-jre sun-java5-plugin

4.On Edgy Eft 6.10 Ubuntu/Kubuntu switched to dash as the default CLI. Supposedly it's faster than Bash. Frankly I don't see much difference on my hardware. In order to make Bash the default you must type the following into the current CLI:

Code: sudo dpkg-reconfigure dash

Select &#8220;NO&#8221; when prompted in the CLI to install Dash.

5.) Next, download the deb for Frostwire or download the rpm for Limewire (basically the same as Fostwire). Should you download Limewire rpm you'll have the extra step of this writing:

Code: alien -d limewire.rpm

6.) Install the appropriate deb file:

Code: sudo dpkg -i (deb package name)

7.) This should do it with minimal of work. If you're menu selections don't appear then you should be able to get this fixed yourself.

I had installed Limewire pro and it was under my applications menu but it wont run . Whenever i clicked its icon , nothing would happen at all . But i Found these points in some thread by Tfrog (THanks Tfrog!!) so im posting these here , btw i fixed my problem of limewire Pro not running in edgy-eft by following Step number 4. Hope this helps.

PS : Am i allowed to attach a setup.rpm file for Limewire Pro ?

---

### Post by bswilson on 2006-11-10
> **woedend said:**
> just get gtk-gnutella from the synaptic library.  doesn't answer your question but its a lot faster to load than limewire.

Wow, I just downloaded **gtk-gnutella**, and am very pleased with it.  Thanks for the tip -- this is a program I didn't even know about!

---

