---
title: "Two bugs annoying me - are they fixed in the new Ubuntu release for next month"
date: 2008-03-27
forum: General Help
---

### Post by ubnewbie2 on 2008-03-27
I have read the web page on what is in the next release (I am running 7.10), and there are 2 things that I hope are fixed in the next release (8.04), but I don't know how to find out.

So can someone tell me

1. Is the nvidia black window bug that I keep seeing if I use desktop effects and open to many windows, fixed?  I know, or have heard, that it's a problem with nvidia's driver.  Does the driver in the new release work better?

2. I have to run the Windows version of Firefox under Wine to get sound in flash video (such as you tube).  I have tried every "fix" I have found, and none worked. I gave up and use the Wine/Windows version whenever I need sound now.  I am hoping the native Firefox in the new Ubuntu will be able to supply sound from flash.  Will it?

---

### Post by Ub1476 on 2008-03-27
1) Can't really answer to this (ATI user), but the development forum>[Hardy Heron]("http://ubuntuforums.org/forumdisplay.php?f=305"), should probably have ome threads about it if it's a problem.

2)I'm using latest ALSA, Flash and Firefox atm. No problem playing sound in **any** application.

I most admit that I'm not using Ubuntu now, but Arch, but they should have the same verison of packages. Except that I'm not using PulseAudio which Hardy does..

---

### Post by ubnewbie2 on 2008-03-27
> **Ub1476 said:**
> 1) Can't really answer to this (ATI user), but the development forum>[Hardy Heron]("http://ubuntuforums.org/forumdisplay.php?f=305"), should probably have ome threads about it if it's a problem.

2)I'm using latest ALSA, Flash and Firefox atm. No problem playing sound in **any** application.

I most admit that I'm not using Ubuntu now, but Arch, but they should have the same verison of packages. Except that I'm not using PulseAudio which Hardy does..

Pulseaudio was one of the possible fixes suggested for Flash sound.  I tried it, and it sort of worked sometimes, but generally not.  Maybe when it is the default under Hardy, it will be OK.  Here's hoping...

I have ONLY had problems with Flash, no other apps.  As I understand it, flash really doesn't use Alsa (in the version in Gutsy) and that was, at least partially, the problem.

Thanks for the input.

---

### Post by Tomatz on 2008-03-27
:lolflag:

1. Isnt a bug its because you dont have enough graphics memory (thus it cant hold all data on your screen)

2. Flash/firefox works fine try upgrading flash

---

### Post by danwood76 on 2008-03-27
As said 1 isnt a bug with ubuntu at all.

2.
You could try the latest alsa version (with the aditional OSS compatibility module also installed), you say you have heard flash doesnt use alsa well it does.
Ive never had any issues with flash videos and sound.

---

### Post by ubnewbie2 on 2008-03-28
> **danwood76 said:**
> As said 1 isnt a bug with ubuntu at all.

2.
You could try the latest alsa version (with the aditional OSS compatibility module also installed), you say you have heard flash doesnt use alsa well it does.
Ive never had any issues with flash videos and sound.

1. I never said it was a bug specifically with Ubuntu, in fact I called it an nvidia bug, and it IS a bug because it does not handle the issue gracefully. Presenting a black window with no error when memory runs out is not nice.


2. I have all updates as provided by Ubuntu. It does NOT work, and there's heaps of posts around from people with similar problems.  Just because it works for some, does not mean that no problem exists. 



If the problems are dismissed this way by everyone, I expect the bugs will still cause problems in the new release.  What a pity...

---

### Post by danwood76 on 2008-03-28
Both these things are proprietry software issues and arent officially supported by ubuntu.
You need to file a bug report with nvidia and with adobe flash, thats the only way these will get fixed.

---

### Post by ubnewbie2 on 2008-03-28
> **danwood76 said:**
> Both these things are proprietry software issues and arent officially supported by ubuntu.
You need to file a bug report with nvidia and with adobe flash, thats the only way these will get fixed.

Agreed,

but, all I was asking was if the new release still exhibited these problems.  You see, I expect that the new release will probably have newer nvidia drivers, and I know they have changed the audio, at least by adding pulseaudio, so maybe, the problems have gone away.

You see, there's no need for anyone to defend Ubuntu - I wasn't blaming it.  I asked "Does the driver in the new release work better?" and "I am hoping the native Firefox in the new Ubuntu will be able to supply sound from flash. Will it?"  Direct quotes from my first post.  The questions show that I know the problem is with the nvidia drivers, and Firefox/Flash.

---

### Post by danwood76 on 2008-03-28
Have you tried installing the latest nvidia driver from nvidias site to fix your first issue?

---

### Post by Tomatz on 2008-03-28
> **ubnewbie2 said:**
> 1. I never said it was a bug specifically with Ubuntu, in fact I called it an nvidia bug, and it IS a bug because it does not handle the issue gracefully. Presenting a black window with no error when memory runs out is not nice.

Lmao

What do you expect the nvidia drivers to do? Render multi colours instead of black. This is NOT a bug. Have you ever ran out of graphics memory on windows with directX? I dont want that approach in linux id rather have stability over frills. A workaround would just degrade performance and probably crash your system.

GET A BETTER GRAPHICS CARD IF YOU WANT TO RUN COMPIZ WITHOUT "ERRORS"! 


:guitar:

P.s I have a nvidia 8600 pcie and i can open about 60 windows before they start going black :)

---

### Post by JettCRX on 2008-04-16
I have an NVidia 6800 GT with 256MB of memory.  It's kind of silly that I can't run WoW and open another window.  If I know BEFORE I start WoW that I'm going to want Firefox, Amarok, Konsole and Kopete running, I can open them all and THEN start WoW.  But heaven help me if one of those has to open a DIALOG box or GASP... someone actually sends me an IM.

If my Powerbook G4 with a 64MB GeForce4 MX can run WoW in a window and still be able to draw other windows, why is it ridiculous to expect it to work on a much more powerful desktop?

---

### Post by Tomatz on 2008-04-16
> **JettCRX said:**
> I have an NVidia 6800 GT with 256MB of memory.  It's kind of silly that I can't run WoW and open another window.  If I know BEFORE I start WoW that I'm going to want Firefox, Amarok, Konsole and Kopete running, I can open them all and THEN start WoW.  But heaven help me if one of those has to open a DIALOG box or GASP... someone actually sends me an IM.

If my Powerbook G4 with a 64MB GeForce4 MX can run WoW in a window and still be able to draw other windows, why is it ridiculous to expect it to work on a much more powerful desktop?

[edit] Its early here ;)

---

### Post by danwood76 on 2008-04-16
Do you have compiz running on your 6800?

Compiz is a real strain on graphics cards and it doesnt quite integrate properly with the proprietry graphics drivers yet.
Try turning compiz off (killing compiz.real in system monitor) and see if you get better results.

---

### Post by jocko on 2008-04-16
> **Tomatz said:**
> Lmao

What do you expect the nvidia drivers to do? Render multi colours instead of black. This is NOT a bug. Have you ever ran out of graphics memory on windows with directX? I dont want that approach in linux id rather have stability over frills. A workaround would just degrade performance and probably crash your system.

GET A BETTER GRAPHICS CARD IF YOU WANT TO RUN COMPIZ WITHOUT "ERRORS"! 


:guitar:

P.s I have a nvidia 8600 pcie and i can open about 60 windows before they start going black :)

Do you really mean you should accept that windows start going black when you run out of graphics memory? So why does it only affect nvidia cards? With my 5 year old ati radeon 9600 Pro w. 128 mb memory I can open an unlimited number of windows with no such effect (ok, I haven't really tried more than about 100, but I am absolutely sure I ran out of graphics memory long before that). This is with compiz running, and it's still working (albeit very sluggish) with 100 windows open.

**[COLOR=Blue] Edit[/COLOR]**: I just tried on my laptop (nvidia 7600 Go w. 512 Mb dedicated graphics memory, running hardy heron). After opening up a little bit over 300 gnome-terminals X pretty much freezes up (I can still move the mouse, but can't click anything and not even ctrl-alt-backspace works). But no black windows. Don't know if this is better or worse, but who in their right mind would open up 300+ windows?:biggrin:

---

### Post by ubnewbie2 on 2008-04-16
> **jocko said:**
> Do you really mean you should accept that windows start going black when you run out of graphics memory? So why does it only affect nvidia cards? With my 5 year old ati radeon 9600 Pro w. 128 mb memory I can open an unlimited number of windows with no such effect (ok, I haven't really tried more than about 100, but I am absolutely sure I ran out of graphics memory long before that). This is with compiz running, and it's still working (albeit very sluggish) with 100 windows open.

Yeah I know.  When I got those silly replies I just walked away from this thread.

---

### Post by Tomatz on 2008-04-16
> **jocko said:**
> Do you really mean you should accept that windows start going black when you run out of graphics memory? So why does it only affect nvidia cards? With my 5 year old ati radeon 9600 Pro w. 128 mb memory I can open an unlimited number of windows with no such effect (ok, I haven't really tried more than about 100, but I am absolutely sure I ran out of graphics memory long before that). This is with compiz running, and it's still working (albeit very sluggish) with 100 windows open.

**[COLOR=Blue] Edit[/COLOR]**: I just tried on my laptop (nvidia 7600 Go w. 512 Mb dedicated graphics memory, running hardy heron). After opening up a little bit over 300 gnome-terminals X pretty much freezes up (I can still move the mouse, but can't click anything and not even ctrl-alt-backspace works). But no black windows. Don't know if this is better or worse, but who in their right mind would open up 300+ windows?:biggrin:


Seems like they have "fixed" it but id rather have black windows (no graphics rendered) than crashing which is what i said in the first place. ;)

---

### Post by jocko on 2008-04-16
> **Tomatz said:**
> Seems like they have "fixed" it but id rather have black windows (no graphics rendered) than crashing which is what i said in the first place. ;)

My crash was the result of only one single test, so I can't be sure it's not just a coincidence (and I don't know if it was the driver, Xorg or compiz that caused it). But as ati can produce drivers that does not crash or stop rendering new windows, I'm sure nvidia can too, if they just set their mind to it. I rather have a a gradual slow-down as the graphics memory run out instead of crashing or black windows.
But as I also said, this happened when I had about 300 windows open, which is a lot more than the 60-70 (if I remember correctly) I could open before getting black windows in feisty (did not try this in gutsy, so I don't know if it was better or worse).

---

### Post by JettCRX on 2008-04-22
Well, the 169.12 version of the drivers seems to have fixed the black windows bug for WoW + Compiz for me.  

/knockOnWood

---

### Post by ubnewbie2 on 2008-04-23
Well that's great news - thanks.

---

