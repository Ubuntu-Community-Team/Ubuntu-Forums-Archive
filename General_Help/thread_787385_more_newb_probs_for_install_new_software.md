---
title: "more newb probs for install new software"
date: 2008-05-08
forum: General Help
---

### Post by danman on 2008-05-08
I have installed 8.04 and I'm still not getting a few aspects of this OS after searching and some help I have had on this forum. Don't get me wrong some help is better than no help.
 The first issue I am still having is installing software that is not in add/remove or package manager, and I have no idea how to in the terminal either.
Unfortunately I need adobe for books I get from school that have be password verified when I open them. If that can be configured in KPDF great but how? I did not see the option to configure that. (something tells me KPDF is not big on DRM;)

The other software is Mambo which has a tar.gz extension. 

is this a mater of adding it to synaptic?

Next is the graphics issue. I got the nvidia driver installed easy enough. My question is if I adjust the settings on the monitor it self when I boot back to windows will I have to adjust them again? (the black area around the edges)

Then there is the sound problem. I have a sound Blaster 24 bit Live! card. Creative labs has no Linux driver for it. any thoughts? Yes I could plug back into the mother board I would rather not though.

 Next question is can I have both XP and ubuntu booted and quickly switch back between them? That would work around the adobe/sound problem. 

then what is shell? can I get to it by typing su in the terminal? When I do type that my authentication fails every time. I saw that for the beginning of installation instructions somewhere on here.

---

### Post by garyedwardjohnston on 2008-05-08
> **danman said:**
> I have installed 8.04 and I'm still not getting a few aspects of this OS after searching and some help I have had on this forum. Don't get me wrong some help is better than no help.
 The first issue I am still having is installing software that is not in add/remove or package manager, and I have no idea how to in the terminal either.

THERE ARE ONLY 3 WAYS NOOBS SHOULD INSTALL SOFTWARE IN UBUNTU, ADD/REMOVE, SYNAPTIC PACKAGE MANAGER, AND DOWLOADING AND INSTALLING .deb FILES.

OTHER INSTALLATION PROCEDURES ARE MORE ADVANCED.  INSTALLING THROUGH WINE AND COMPILING FROM SOURCE, ETC.

THERE ARE MANY APPLICATIONS THAT DEAL WITH PDF'S TRY THEM ALL THEN CONTACT ME IF STILL NONE SUIT YOUR NEEDS.

Unfortunately I need adobe for books I get from school that have be password verified when I open them. If that can be configured in KPDF great but how? I did not see the option to configure that. (something tells me KPDF is not big on DRM;)

The other software is Mambo which has a tar.gz extension. 

MAMBO?  THIS IS A WEB SERVER APPLICATION, NOT A DESKTOP APPLICATION.  IF YOU ARE TRYING TO CREATE A WEBSERVER AND WEBSITE ON YOUR DESKTOP PC, YOU HAVE A LOT MORE TO LEARN.  IT IS POSSIBLE, BUT NOT EASY.  I DO IT BUT USE JOOMLA (THE BETTER VERSION OF MAMBO)

is this a mater of adding it to synaptic?

Next is the graphics issue. I got the nvidia driver installed easy enough. My question is if I adjust the settings on the monitor it self when I boot back to windows will I have to adjust them again? (the black area around the edges)

THIS IS A BUG.  IT HAPPENS TO ME TOO.  ONLY WAY IVE FOUND AROUND IT IS TO PERFORM A FRESH INSTALL, THEN IMMEDIATELY INSTALL THE RECOMMENDED DRIVER, THEN RESTART, THEN AND ONLY THEN START PLAYING WITH SCREEN RESOLUTIONS.

Then there is the sound problem. I have a sound Blaster 24 bit Live! card. Creative labs has no Linux driver for it. any thoughts? Yes I could plug back into the mother board I would rather not though.

TRY ENVY

 Next question is can I have both XP and ubuntu booted and quickly switch back between them? That would work around the adobe/sound problem. 

IT IS POSSIBLE TO RUN THEM AT THE SAME TIME (NEEDS A GOOD COMPUTER THOUGH).  TRY VIRTUALBOX.

then what is shell? can I get to it by typing su in the terminal? When I do type that my authentication fails every time. I saw that for the beginning of installation instructions somewhere on here.

IT APPEARS THAT YOU ARE A NOOB AND SHOULD TRY TO AVOID THE TERMINAL FOR A WHILE.  YOUR PASSWORD FOR THE ROOT IS THE SAME AS YOUR USER PASSWORD.  THE ONE YOU SIGN IN WITH.

GOOD LUCK AND WELCOME TO LINUX.

:)

---

### Post by gimfred on 2008-05-08
Adobe distributes their reader so it is available for ubuntu... I was surprised to find it isn't in add and remove... but then kpdf has been good enough to me...

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html) is direct from Adobe and make sure you choose the .deb file... the others won't work.

The evince pdf reader apparently allows you to read password protected files... I'm assuming that a screen pops up once the file is opened... and I would have thought the same for kpdf. Sorry i don't have any password protected pdfs...


I don't know about either mambo or the creative driver... but tar.gz suggests that the files inside will need to be compiled and installed manually. To install on Ubuntu, try download a file that has the .deb extension. .deb is best for Ubuntu unless you are willing to learn to compile and install your software which is very manual, though not as hard as some do make, no pun intended, out.

For all intents and purposes, the terminal is the shell. 

su is for super user, and it requires a work-around to use in Ubuntu. when they tell you to use su, try sudo or gksudo for graphical apps.

and don't mind the former poster, I believe they had good intentions just forgot to install tact and diplomacy which depends on libcourtesy.

---

### Post by eriqjaffe on 2008-05-09
> **danman said:**
> The other software is Mambo which has a tar.gz extension. 

is this a mater of adding it to synaptic?Nope.  If it's a .tar.gz file, it's usually source code that's been compressed (think of it as a Linux .zip file).  You need to extract it and then compile and install it yourself.  Not for the faint of heart, but there's at least [one thread]("http://ubuntuforums.org/showthread.php?t=128511") around here that may help you out.

> **danman said:**
> Next is the graphics issue. I got the nvidia driver installed easy enough. My question is if I adjust the settings on the monitor it self when I boot back to windows will I have to adjust them again? (the black area around the edges)The settings on the monitor itself should be OS-agnostic, as long as the monitor is getting the same resolution and refresh rate sent to it.

> **danman said:**
> Next question is can I have both XP and ubuntu booted and quickly switch back between them? That would work around the adobe/sound problem.Yes, but again, it's not for the faint of heart.  See [here]("http://ubuntuforums.org/showthread.php?t=769883") for details.

---

### Post by ryanhaigh on 2008-05-09
The mambo tar.gz file isn't really source code, well at least you won't need to compile it its just an archive (like a zip file) of the mambo CMS. A little off topic, but I thought mambo had been superseeded by joomla, I was going to check when the latest mambo was released but their website isn't working.

If you have to adjust the monitor then ubuntu and windows are not using the same res/refresh so you will need to readajust if you are using a CRT, lcd monitors should have autoadjust to address this.

Using virtualbox will NOT address your sound issue because your xp instance will be using the virtualbox sound device which just passes sound to your linux sound server/driver. Virtualbox is however a great solution for running windows apps, I would recommend a fresh install into the VM though.

This is something you should probably have a look at 
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

