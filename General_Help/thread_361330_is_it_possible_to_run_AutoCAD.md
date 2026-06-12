---
title: "is it possible to run AutoCAD?"
date: 2007-02-14
forum: General Help
---

### Post by error404 on 2007-02-14
I'm very new to ubuntu or anything besides windows...

Until now, I'm very happy surfing online in ubuntu... but in order for me to get ridof windows, I need to be able to run Autocad and other win-only programs like skecthup.

Does anyone have any experience doing it? 

leo

---

### Post by maxamillion on 2007-02-14
[http://www.codeweavers.com/](http://www.codeweavers.com/) .... it costs money, but if its worth it to you this is probably the best software to get AutoCAD (among other windows apps) running smoothly with confidence of little to no random spastic functionality .


Other than that you can try [wine]("http://www.winehq.com") which is free, open sourced, and community based.

---

### Post by error404 on 2007-02-14
> **maxamillion said:**
> [http://www.codeweavers.com/](http://www.codeweavers.com/) .... it costs money, but if its worth it to you this is probably the best software to get AutoCAD (among other windows apps) running smoothly with confidence of little to no random spastic functionality .


Other than that you can try [wine]("http://www.winehq.com") which is free, open sourced, and community based.

what is the difference between codeweavers and VMWare? I try using VMWeaver but I couldn't figure out how to use it... Anyway, I just found this topic that could be helpful
[http://ubuntuforums.org/showthread.php?t=183209&highlight=autocad](http://ubuntuforums.org/showthread.php?t=183209&highlight=autocad)

I try runing wine.. but no luck

---

### Post by graigsmith on 2007-02-14
how many programs are you trying to run that are only on windows? 

it can be a pain to get some programs running in linux.  and i mean, if your trying to run like more than 1-2 things in wine or crossover office, you might as well stick with windows.  

plus switching to linux takes alot of learning new stuff.  Ubuntu may be easy, and easy to pick up.  But it's different than windows. And if you aren't prepared to spend time relearning how to do something that may have been easy for you in windows.  Then you shouldn't switch to linux.

you can look in the appdb section at winehq.com to see what programs are easy to get running.

A short glance at the page for autocad shows that it barely runs. 
[http://appdb.winehq.org/appview.php?iAppId=86](http://appdb.winehq.org/appview.php?iAppId=86)

---

### Post by maxamillion on 2007-02-14
> **error404 said:**
> what is the difference between codeweavers and VMWare? I try using VMWeaver but I couldn't figure out how to use it... Anyway, I just found this topic that could be helpful
[http://ubuntuforums.org/showthread.php?t=183209&highlight=autocad](http://ubuntuforums.org/showthread.php?t=183209&highlight=autocad)

I try runing wine.. but no luck

[VMWare]("http://en.wikipedia.org/wiki/VMware")  == Virtualization to run an OS on another OS
[CrossOver]("http://en.wikipedia.org/wiki/CrossOver") == Virtualization to run another OS's application on your OS

---

### Post by error404 on 2007-02-14
well, for work.. I do need a lot of "demanding" programs.

Photoshop
SketchUp
Autocad
Maxwellrender (although I'll wait until they release their linux version)


leo

---

### Post by maxamillion on 2007-02-14
> **error404 said:**
> well, for work.. I do need a lot of "demanding" programs.

Photoshop
SketchUp
Autocad
Maxwellrender (although I'll wait until they release their linux version)


leo

CrossOver will run all those with ease, but like I said ... you gotta pay for it.

---

### Post by error404 on 2007-02-14
> **maxamillion said:**
> CrossOver will run all those with ease, but like I said ... you gotta pay for it.

are you talking from experience? $40 is not that much... but I don't want to get my hopes up :D

---

### Post by pebkac on 2007-02-14
> **error404 said:**
> are you talking from experience? $40 is not that much... but I don't want to get my hopes up :D

Another thing you can try is to run Linux version of some of those programs. For example:

Photoshop -> GIMP
Stetchup -> I don't know what this is but if it's a vector drawing program, try Inkscape.
I don't think there is an alternative for CAD.
Microsoft Office -> OpenOffice.org

I can't get Ubuntu up on my system, but my Mandrake distribution came with GIMP already installed. If you have it, you can see if you like it.

I have never been able to get anything other than solitaire and notepad to run in wine, but I have heard good things about CrossOver Office.

---

### Post by reclusivemonkey on 2007-02-14
> **pebkac said:**
> 
I don't think there is an alternative for CAD.


Maybe not anything exactly like AutoCAD but there are CAD applications for Linux;

[http://www.tech-edv.co.at/lunix/CADlinks.html](http://www.tech-edv.co.at/lunix/CADlinks.html)

---

### Post by DtJee on 2007-02-14
What about Medusa4 we use it at work .. and its working nativ in linux.. I think it reads dwg and dxf files. Perhaps you should take a look at the personal license... [www.cad-schroer.de](www.cad-schroer.de) or com.. can't remeber.. not at work right now... 

So give it a try..

---

### Post by Tosa on 2007-02-14
It's been a while since I searched the web to make acad working, and I don't remember where I got it... Anyway Acad 2000 works with wine quite nice. Not perfect, but it works.
The general idea was to have dual boot and to install acad  both in windows and ubuntu.  After that  you should copy the whole installation from windows to ubuntu.  In wine you should set windows path:
"windows"="c:\\windows"
"system"="c:\\windows\\system"
"temp"="x:\\"
"path"="c:\\windows;c:\\windows\\system;c:\\program files\\common files\\autodesk shared"
That's about it if I'm not wrong.
HTH

---

### Post by Sonic Reducer on 2007-02-17
heres a difficult question though: can it run on x64 using CrossOver?

---

### Post by hodad on 2007-02-24
I've been using Qcad for two years, and find it to be pretty good, but it'll take you a few days to relearn your keystrokes/commands/etc.  Also, of course, it's not as refined as acad. I used Autocad for many years, but now work for myself (and use Linux) so can't afford acad.  Qcad can import acad files (I think -- haven't tried). 

Lots of other products on the link listed in previous reply in this thread that I haven't tried.  At the time, Qcad seemed best.  Hope this helps!

---

### Post by emrextreme on 2007-08-05
Here is howto; 

Autocad on Ubuntu

[http://doctus.net/showthread.php?t=17006](http://doctus.net/showthread.php?t=17006)

---

### Post by MichaelSM on 2007-08-13
Thanks emextreme. How to translate that page?
Michael.

---

