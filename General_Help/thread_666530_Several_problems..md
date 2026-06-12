---
title: "Several problems."
date: 2008-01-13
forum: General Help
---

### Post by cfsporn on 2008-01-13
I am having several problems with Ubuntu. My first is that ghosts of windows past keep appearing. For example, if I close a window, sometimes an outline remains. My next problem is that flash stutters. This happens in every web browser, but not in vlc. My last item is a request. Is there any media conversion program for ubuntu? I have an AVI and want to make it an mpeg-4. Thank you. 
A picture that shows that window problem is attached. 
My configuration:
Dell Dimension 8100
1.3 ghz pentium 4
512 MB RAM
32 MB Nvidia Graphics card
Latest version of Ubuntu.

---

### Post by mccorkle on 2008-01-14
Both of your problems are due to the new-fangled visual stuff that Linux distros come with (I can't believe what this world is coming to).  The only possible thing to look into is to make sure you are running hardware acceleration on your nvidia card.  If you are already hardware accelerated, then your options are to 1) turn off the compiz/beryl/whateveritscalled pretty window features 2) pass all your hardware info  and your screenshot up to the compiz/beryl/whateveritscalled project maintainers and see if they have a fix for it.  

As for a movie encoder, that's a tricky one to answer.  AVI is a container format and can contain a LOT of different codecs, if I recall correctly.  What that means is that you have to have a program with a decoder for all of those codecs installed to be able to just "read" your AVI, much less encode it.  

With that said, use [ffmpeg ]("http://ffmpeg.mplayerhq.hu/").

Hope that helps.

::Mark McCorkle

---

### Post by cfsporn on 2008-01-14
First, how would I know if hardware acceleration is on? Also is there a version of ffmpeg with a gui?

---

### Post by Drakkenfyre on 2008-01-15
One way is to run glxgears. If the gears spin fast, it's hardware acceleration, if they spin slow, it's software rendering.

But please, make sure you don't have any unsaved work or important programs running. Glxgears simply makes X stop working for me. But it will most likely work just fine for you--but why take the risk?

---

### Post by TidusBlade on 2008-01-15
Ive looked in a bunch of places, theres no GUI for ffmpeg though, but "man ffmpeg" should give all the info you need to start converting, after all, it's only a simple command, but I used to be scared of terminal once...

---

### Post by cfsporn on 2008-01-17
It is not so much that I am scared of the terminal, it is just for ease of use.

---

