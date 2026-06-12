---
title: "Gnopernicus magnifier, where art thou?"
date: 2005-09-18
forum: General Help
---

### Post by linbetwin on 2005-09-18
Hello,

What packages do I need for gnopernicus magnifier, other than gnopernicus dependencies and gnome-mag? Or what else do I have to do to get the magnifier working.

Is there any magnifer tha follows typing, like de Windows magnifier? KMag only follows mouse movement.

Ubuntu goooood! Accessibility support baaaaad!

Ubuntu, Linux for human beings... :^o

---

### Post by linbetwin on 2005-09-19
No solutions? Hasn't anybody else been having this problem?

---

### Post by linbetwin on 2005-09-19
Searching this forum I found many posts about this problem. Has anyone managed to get the gnopernicus magnifier working?

The first Linux distro I tried was Ubuntu Hoary and I was delighted, except for the fact that I am heavily nearsighted and I need a screen magnifier. In Windows there is a very good one. If you dock it under the screen, it pops up without the useless title bar. Then I click on the upper edge and drag it up until the magnifier winow covers about a third of the screen (the lower third). When I maximize a browser window or a word processor window, it only covers the other two thirds of the screen and so nothing is hidden under the magnifier window. The magnifier follows not only mouse cursor movement, but also typing, editing and caret focus. It is essential for a magnifier to follow text editing, otherwise you have to move the mouse inch by inch to the right to see what you are writing, and that takes time.

I hope accessibility developers won't mind taking into consideration suggestions from one who has been using the Windows magnifier for years. This magnifier problem is the only thing keeping me from switching to Linux.

I would appreciate any answers from anyone having the least bit of experience using Gnopernicus magnifier, KMag or any other Linux magnifiication software.

Thank you

---

### Post by jasongrieves on 2005-09-19
Hello,

I am going to be working heavily on documenting Accessibility Features in Gnome/Ubuntu.  I should hopefully have the steps to correct this soon as well as CORRECT solutions on full screen mangification, etc.  I heard some rumors of a Accessibilty Team coming together for Ubuntu and will be researching and trying to get on that.  Will post my results via Wiki and forums then.  

I am low vision and am currently working on accessibilty full time.  I plan on doing this on the side :)

---

### Post by jasongrieves on 2005-09-19
OK hopefully this can get you started
tested on Breezy (sorry all I have at the moment)

Go to 
[http://packages.debian.org/unstable/gnome/at-spi](http://packages.debian.org/unstable/gnome/at-spi)

1)download the i386 (assuming that is your version you need)
2)open up terminal (applications>terminal)
3) cd to the folder you downloaded the file (default is Desktop so cd Deskop)
4) type 'sudo dpkg -i at-spi_1.6.6-1_i386.deb' without the qoutes
5) run gnopernicus

just a bad dependency problem.  Will post better solutions later.

---

### Post by linbetwin on 2005-09-20
Many thanks, jasongrieves! I'll try that. Any I hope this bug will be fixed in the Breezy final release.

But can anyone tell me if the Gnopernicus magnifier or KMag (which I use now) can follow text editing, not just mouse movement? It's very difficult to write when you have to move the mouse an inch to the right after every word you type, to see what you actually typed.

Thanks again!

---

### Post by jasongrieves on 2005-09-21
ok well I am working on documentation for Accessibility and I notice this does NOT work for Hoary, sorry about that.  To get the magnifier working download gnome-mag from Synaptic.  This will at least allow that module to function.  As for the screen reading, there are still dependency problems with the lib6 and the ati-bridge me thinks.

---

### Post by linbetwin on 2005-09-22
The magnifier doesn't work with gnome-mag installed either, neither in Hoary, nor in Breezy Preview. There is a dependency problem here too.

---

### Post by jasongrieves on 2005-09-22
I got it to work in both releases.  In Hoary it requied the installation of the gnome-mag from the package manager.  in Breezy it required the dependencies I talked about in the first post.  Wha errors are you getting when you try to run the magnifier ONLY.  Speech is still out.

---

