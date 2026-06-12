---
title: "Program not installing in WINE (but used to)"
date: 2005-04-09
forum: General Help
---

### Post by Syrinx on 2005-04-09
Hey all - 

   I'm not how to look for the answer on this one, because there is a few different factors here.  I did see that WINE has their own DEBs, and loaded their repositories into Synaptic and updated the program.

    The program that I am working with is an older Windows app, called Kookie Jar.  It is a random signature app, that reads from a text file of multi-line signatures, sends it to a template, and that output is appended to every e-mail I send out.

     Here's where the different factors come in.  The distro that I gave up on to come over here was Simply MEPIS 3.3.  I have also used this on Mandrake and SuSE.  For all of those, the window manager was KDE.  So, since Ubuntu defaults to Gnome, I went ahead and installed KDE.  I'm in that now, and I'm still getting the same errors.  I even tried loading it through CrossOver, in which I do have Photoshop, DreamWeaver, and Internet Explorer running.  It installed, but when I activate it - WINE comes up, and gives me: "Access violation at address 77EC37CC.  Write of address 00410063."  I also get the same thing when I try to do a new install through WINE itself.

      I've went through the Wine Config and everything looks ok.  The thing is that my .exe files are not showing up with the WINE icon.  In KDE, they are still the cog icon.  In GNOME, there were the default (foot?) icon.  

      If anybody can point me in the right direction, I would be very thankful.  Also, and this might defeat the purpose of the thead, if you a know a true Linux app that does the same thing, I'll take that to.  Kookie Jar is the only thing that I use pure WINE for.  Everything else is in CrossOver.

     Thank again.

---

### Post by Syrinx on 2005-04-09
Ok.... done more searching around....

Saw that WINE Tools replaces the other setup tool.  Went to the WINE Tools homepage, and took his advise about WINE 20041019.  It's still going through MAKE, so once it's done, I'll install WINE Tools and go from there.


I've never had it be this much work, but at least I'm learning.

---

### Post by Syrinx on 2005-04-10
Oh, you've got to be kidding me....

He clearly states on his WineTools website:  20041019	this is the recommended version

That's the version I downloaded, and went through the setup.  

I had to download WineTools from his site, because Synaptic wanted to download the newer WINE as a dependency.  I install WineTools, and it tells me: You don't have Wine installed on your computer....

Back to the drawing board.

---

### Post by Syrinx on 2005-04-10
[QUOTE=Syrinx]Oh, you've got to be kidding me....

He clearly states on his WineTools website:  20041019	this is the recommended version

That's the version I downloaded, and went through the setup.  

I had to download WineTools from his site, because Synaptic wanted to download the newer WINE as a dependency.  I install WineTools, and it tells me: You don't have Wine installed on your computer....

Back to the drawing board.[/QUOTE]
 And just because of pure insanity, I tried to load it through CrossOver again, and now it works.

That was interesting to say the least.

---

### Post by darkaudit on 2005-04-10
Whin I built this new system, I got access violation errors when I tried to install DVD Shrink. I finally took the entire .wine directory from a working system and put it on the new one. I'm missing the desktop icons, but it's working fine.

---

### Post by az on 2005-04-10
There is a current ubuntu wine repository at winehq.  You just add it to your sources.list and update and install the latest wine and wine-tools.  You do not need to compile it.

---

### Post by Dripple on 2005-05-04
[QUOTE=Syrinx]Oh, you've got to be kidding me....

He clearly states on his WineTools website:  20041019	this is the recommended version

That's the version I downloaded, and went through the setup.  

I had to download WineTools from his site, because Synaptic wanted to download the newer WINE as a dependency.  I install WineTools, and it tells me: You don't have Wine installed on your computer....

Back to the drawing board.[/QUOTE]
 where did you find wine 20041019 for ubuntu ?

---

