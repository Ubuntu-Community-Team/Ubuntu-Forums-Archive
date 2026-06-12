---
title: "SDL Help"
date: 2007-12-06
forum: General Help
---

### Post by KBenk on 2007-12-06
Ok. I've installed SDL, but apparently not the right way, because everytime I try to run a game that use SDL I get this: Couldn't initialize SDL: No available video device. So, I have now decided, after many nights of searching for answers, to completely start over with SDL to see if I screwed up the install. Problem is... I don't know how to uninstall all of it or where to start to begin reinstalling the correct way. Can anyone help me out?? SDL is really messing with my head.

~Benk

---

### Post by PeterJS on 2007-12-06
How did you install the SDL libraries in the first place?

---

### Post by KBenk on 2007-12-06
I downloaded SDL-1.2.12.tar.gz from libsdl.org. Then worked my way through the readme's to help myself out. Kind of a hit and miss thing. Please show me an easier way.

---

### Post by PeterJS on 2007-12-06
Oh, yeah that's rough. You can install things manually but that should really only be a last resort. Do you still have the extracted tar ball that you built and installed it from? In the same folder that you ran, make and all the other build commands try:
```

make uninstall

```


The thing about Debian (and Ubuntu by extension) is that it's got a package management system. Furthermore the Ubuntu repositories are huge and have most everything you'd ever want in them. In the future to install something open the Synaptic Package Manager (System > Administration > Synaptic Package Manager), search for what you're looking for and then mark it for installation and then apply changes. The nice thing about the Ubuntu package manager is that it will automatically install all the libraries and other things the program needs.

What games were you trying to install that needs SDL? They're probably in Synaptic.

And here's the classic guide on installing stuff:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by KBenk on 2007-12-06
Ok. I ran the make uninstall and it worked. Now, what should I choose to install in synaptic, anything with sdl?

I am trying to play daimonin, and I've also tried a few other games. I haven't had much luck getting anything to play. I had Nexuiz working once, but now that doesn't even run. I get the same error with that.

---

### Post by PeterJS on 2007-12-06
Nexuiz is in the universe repository, installing that will automatically install all the SDL libraries it needs. 

And Get-Deb.net has a Deb installer for Daimonin
[http://www.getdeb.net/search.php?search_distro_id=5&keywords=Daimonin](http://www.getdeb.net/search.php?search_distro_id=5&keywords=Daimonin)

Given that it's a Deb installer it will have the meta data nessicary to install any additional dependacies that Nexuiz didn't cover.

---

### Post by KBenk on 2007-12-06
I knew there was an easier way. I'm downloading the Deb for Daimonin right now. I'll let you know how the install goes. Thanks for the help.

---

### Post by KBenk on 2007-12-07
Ok, install went well. But I tried to run Daimonin from Applications->Games->Daimonin and it acted like it was going to run, changed to a black screen, then went back to my desktop but changed my resolution. So I ran it in terminal and got this:

kyle@kyle-laptop:~$ daimonin
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
List Video Modes
Available Modes
  1024 x 768
  800 x 600
  640 x 480
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no
VideoInfo: video memory: 0KB
ERROR sprite.c: Can't load sprite bitmaps/palette.png
load_bitmap(): Can't load bitmap bitmaps/palette.png
ERROR sprite.c: Can't load sprite bitmaps/font7x4.png
load_bitmap(): Can't load bitmap bitmaps/font7x4.png
ERROR sprite.c: Can't load sprite bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap bitmaps/font6x3out.png
ERROR sprite.c: Can't load sprite bitmaps/font_big.png
load_bitmap(): Can't load bitmap bitmaps/font_big.png
ERROR sprite.c: Can't load sprite bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap bitmaps/font7x4out.png
ERROR sprite.c: Can't load sprite bitmaps/font11x15.png
load_bitmap(): Can't load bitmap bitmaps/font11x15.png
ERROR sprite.c: Can't load sprite bitmaps/intro.png
load_bitmap(): Can't load bitmap bitmaps/intro.png
Segmentation fault (core dumped)

Can you make any sense of that?

---

### Post by PeterJS on 2007-12-07
> **KBenk said:**
> Ok, install went well. But I tried to run Daimonin from Applications->Games->Daimonin and it acted like it was going to run, changed to a black screen, then went back to my desktop but changed my resolution. So I ran it in terminal and got this:

kyle@kyle-laptop:~$ daimonin
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
List Video Modes
Available Modes
  1024 x 768
  800 x 600
  640 x 480
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no

Looks normal so far, that's all just informational output
> 
VideoInfo: video memory: 0KB
This may or may not be bad, what graphics card do you have? and do you have the right drivers for it?
> 
ERROR sprite.c: Can't load sprite bitmaps/palette.png
load_bitmap(): Can't load bitmap bitmaps/palette.png
ERROR sprite.c: Can't load sprite bitmaps/font7x4.png
load_bitmap(): Can't load bitmap bitmaps/font7x4.png
ERROR sprite.c: Can't load sprite bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap bitmaps/font6x3out.png
ERROR sprite.c: Can't load sprite bitmaps/font_big.png
load_bitmap(): Can't load bitmap bitmaps/font_big.png
ERROR sprite.c: Can't load sprite bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap bitmaps/font7x4out.png
ERROR sprite.c: Can't load sprite bitmaps/font11x15.png
load_bitmap(): Can't load bitmap bitmaps/font11x15.png
ERROR sprite.c: Can't load sprite bitmaps/intro.png
load_bitmap(): Can't load bitmap bitmaps/intro.png
That is no good, that's a big block of it saying it can't images that the program needs.
> 
Segmentation fault (core dumped)
And here's where things go from bad to worse. A core dump happens when a program runs in to such a critical error that it can not recover in anyway so rather than trying to recover it just dumps all of it's memory to a file so hopefully a human (ie a programmer) can make of what went wrong.
> Can you make any sense of that?Yeah I don't know, it might be problems from the old SDL install, might be related to the images that it can't load, can't really say conclusively.

---

### Post by KBenk on 2007-12-07
alright, well I have an ATI Radeon mobility 9000 graphics card and according to Screen and Graphics Preferences I am using the ati driver for the mach and rage cards. Now there is an ati driver for the radeon/mobility but when I select that and hit ok then reopen the Screen and Graphics Preferences it goes back to the first driver. Why would it do that?

---

### Post by PeterJS on 2007-12-07
I don't remember how the screen and graphics preferences app works does it ask you for your password before it loads up? If not it doesn't save the changes because it isn't running with the privileges to do so. That explains the lack of VRAM. You might try running the restricted driver manager to install the fglrx driver and see if that helps any.

---

### Post by KBenk on 2007-12-07
No, it doesn't ask for my password when I open it. The driver it is using is the fglrx driver, but I don't think that driver actually supports my card. My card isn't listed under it's supported cards.

---

### Post by PeterJS on 2007-12-07
Sorry man, I don't know what to tell you, I'll see if I can flag somebody else down to take a look at this.

---

### Post by KBenk on 2007-12-07
Ok. thanks for the help. I'll keep checking things out and checking this thread so if you find someone who could help just send them here or pm me. Thanks again.

~Benk

---

