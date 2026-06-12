---
title: "Open .max file in Ubuntu?"
date: 2013-03-23
forum: General Help
---

### Post by SMOKE14 on 2013-03-23
Anyway/program to do this? I have some Autodesk 3DS Max files that I need to open in Ubuntu, and appearently 3DS Max doesn't work with Wine. I can try installing it, but it probably won't work.


Also mods, move this if need be.

---

### Post by SMOKE14 on 2013-04-06
I guess it's not possible? Darn. I've found a program that can open .3ds and just about everything except .max, which I need.

---

### Post by GameX2 on 2013-04-06
They won't open, with Blender. :/
Unfortunately, 3DS Max probably won't be usable in Linux in a long time.  Along with Adobe Premiere Pro and AfterAffects, it's the only program that force me to reboot into Windows.  Despite the 3DS Max 2009 Wine App dB rating, I never managed to install the 2009 version (I work with 2013 version.).

The 2013 version require NET Framework 4.0, which won't install under Wine 64-Bit.  You can fake the installation of NET Framework 4.0 on Wine 32-Bit, but the setup display an error, later on (And 4GB of RAM to work with 3DS Max is low !).

Even worse, I can't even use it in a Windows virtual machine properly.
With 8GB of RAM, it still lags.  But the lack of memory is not the only problem: Both VMware Workstation and VirtualBox do not have high compatibility with 3D acceleration, so you have to force the use of the OpenGL driver - which will make the "Realistic" display mode unavailible.

There is also a really annoying bug with the zoom: you know when you do a zoom, or an extrude for example?  When the mouse reach the side of the screen, it reappear on the opposite side?  Well, this is incompatible with virtualisation.  With virtualisation, when you zoom and your mouse reach the edge of the screen, 3DS Max kind of make a Zoom x1000 - which make the software really hard to use on a virtualisation software. :(

Sorry to say that. :(  Glad I could simply share that I would like 3DS Max usable on Linux, as well!
I don't know a program to open the .MAX files, sorry. ;(

---

### Post by SMOKE14 on 2013-04-13
Sorry for the late response been busy... yeah, it sucks! The only thing that's keeping me from using any Linux distro permanently and getting rid of Windows is Photoshop and 3DS Max. I've tried Gimp, and it's OK, but I prefer PS. Then, the 3DS Max issues. Ugh. :/ Thanks for the help, though!

---

### Post by benawhile on 2013-05-07
Hello

I have some old .max files that were created by paperport. I found a program called maxview [URL="http://sourceforge.net/projects/maxview/"]http://sourceforge.net/projects/maxview/
[/URL]that claims it can read them and convert them to .pdf. They are just image files. I don't know about all this 3D stuff.
Anyway I downloaded it and ended up with one of those debian icons on my desktop that look like a cardboard box with a red squiggle, and titled maxview_0.7-1_i386.deb. I haven't sussed those debian icons out yet. When I clicked on it it asked me if I wanted to open it with Ubuntu software centre so I said Yes, and the software centre says it has been downloaded, but how do I run it? I can't see it under "applications" and when I click on the .max file it doesn't present me with "maxview" in the list of options.

Incidentally I left this page before posting to write a signature and when i came back this text had been wiped and I had to start over again. Can anyone explain why some pages retain the text if you leave the page, and otheres don't? And I couldn't find anywhere to create a signature, is that because of spammed signatures? I don't have 25 posts yet.

Anyway I have Ubuntu 12.04 XP Dual Boot. Which has been working perfectly from the word go, which was last September. And a twin core Athlone AMD processor. Does that mean I should opt for AMD 64 and not i386 when downloading?

---

### Post by imon.glass on 2013-12-14
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]This has actually moved to github here, and renamed to paperman.[/COLOR]

[https://github.com/sglass68/paperman](https://github.com/sglass68/paperman)

[COLOR=#000000]The latest version can remember folders that you add, so you don't need any arguments when running it.[/COLOR]

Suggest you build from source as the binaries are old.

[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Simon[/COLOR]

---

