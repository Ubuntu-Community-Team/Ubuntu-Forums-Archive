---
title: "poor video quality"
date: 2008-05-06
forum: General Help
---

### Post by Kaneda187 on 2008-05-06
Hey Im a total NooB just installed ubuntu hardy working great I love it! Just got one problem my video quality is very poor, avi files mpeg's you name it.... help! 
I have all my effects working perfectly and great res on my screen its its just vids

my graphics card is

ati Mobility Radeon X1400

---

### Post by Kaneda187 on 2008-05-07
someone please! i dont want to go back to bill and windows BS! thers gotta be a fix??:confused:

---

### Post by NightwishFan on 2008-05-07
Try vlc player, mplayer, or totem (xine). I personally dislike gstreamer.

---

### Post by Kaneda187 on 2008-05-07
thanks for gettin back to me but still got blocky crap quality vids!:mad: any other ideas?

---

### Post by NightwishFan on 2008-05-07
Make sure vlc is set to open gl. I never have problems with Ubuntu vid quality, epecially with xine, sure its not just the files?

---

### Post by Kaneda187 on 2008-05-07
tried loads of files
nope still same. 
i did the gears test in the terminal and its really poor quality. starting to think its the drivers but it makes no sense when all my other visuals are superb.:confused:

---

### Post by NightwishFan on 2008-05-07
Perhaps. Also try x11 output on vlc it may look better but it doesn't for me. Sorry I do not know much more. I will also ask if you have your correct monitor resolution and refresh rate, if so then it likely is not a crucial display problem.

---

### Post by Kaneda187 on 2008-05-07
ok i give up for tonight at least gotta sleep and then work but im gonna get back on it then, im determined not to craw back to windows! thanks so much for the help.

---

### Post by NightwishFan on 2008-05-07
No problem hopefully it works out for you.

---

### Post by spandanj on 2008-05-10
I have the same video card: ati mobility radeon x1400
I have the same problem: pixellated video playback when fullscreen
-->change video output OpenGl causes VLC to crash upon play. and setting to XV still shows problem

There is absolutely no problem with compiz. so, I am assuming the problem lies somewhere in video playback...

Is there any solution? please help

---

### Post by Kaneda187 on 2008-05-12
I have yet to find one:( still looking tho, thers gotta be away to fix it out there we just gotta find it! I'll let you kno if i find a fix do the same too please!:)

---

### Post by SpaceTeddy on 2008-05-12
i am running an ATI x1600  and have the same problem.

use mplayer and switch it to gl mode (vlc won't work for me in gl mode - it will always crash) - xv is not even supported on ATI cards anymore. 

the only drawback is that you cannot use the gl layer together with compiz...

---

### Post by Kaneda187 on 2008-05-13
Sorry im a bit of a n00b, how do i set vlc to open gl?:confused:

---

### Post by NightwishFan on 2008-05-13
It is under video in the vlc preferences (this is rough i currently am using kaffine)

---

### Post by spandanj on 2008-05-13
so, as of right now:

1. ati driver 8.4_, vlc video playback with compiz is pixelated.
2. compiz ON + opengl in vlc = choppy video, but not pixelated.
3. turning compiz off + selecting opengl in vlc = video not choppy or pixelated

If any of above 3 are wrong, please notify.

Also,
Q. does opengl improve video quality in mplayer, or kaffine even WITH COMPIZ ON?

---

### Post by SpaceTeddy on 2008-05-14
i cannot run vlc with gl at all - it always crashes (no matter if compiz is loaded or not). I need to use mplayer to run a movie gl mode. And with compiz on, mplayer flashes like crazy. So i always need to unload compiz an use mplayer to watch videos - still... 

ATI X1600 with restricted fglrx drivers.

---

### Post by Muffinabus on 2008-05-14
I am also experiencing bad quality video in VLC when in full screen.  The same videos I'm playing play perfectly fine in Windows VLC ( /: ).  I can't even find this opengl setting you guys are talking about, but it would seem that's no use anyways.

---

### Post by spandanj on 2008-05-17
IF this problem is not solved, I am basically willing to change back to windows man!!! this is such a serious issue. I mean, besides look at .ppt and .doc files - I WATCH movies - my third primary use of computer. THus, a very important one. and the video quality is unbearable.

_HOW can i find out who is working upon this problem at ubuntu? and WHAT is being done about it. anyone i can contact at ubuntu team?????


dell 6400, x1400 radeon

---

### Post by NightwishFan on 2008-05-17
I seriously have never encountered a similar problem though. If it occurs on different backends like xine and gstreamer it may be a hardware issue.

---

### Post by SpaceTeddy on 2008-05-18
it is not a hardware issue. I was running the same comp before with gutsy, and it worked fine. If i run mplayer in gl mode (heavy flickering with compiz enabled, so i usually need to unload all screenlets and force metacity to load again) the movie qualiyt get good. 

No, i'd put my money on either the drivers or the x-server which are not handling the video output correctly. But i am not going to compile the latest drivers into my kernel myself - that is too muck work with too little success chance. Besides, i'd need to do it every time the kernel gets upgraded.

here is what i have tested so far:
1.) Compiz + vlc + x11 output = poor quality
2.) Compiz + vlc + gl = vlc crashes
3.) Compiz + totem + x11 output = poor quality
4.) Compiz + totem + gl = option does not exist
5.) Compiz + mplayer + x11 output = poor quality
6.) Compiz + mplayer + gl = good quality, but heavy flickering causing serious damage to the brain
7.) Metacity + vlc + gl = crahses
8.) Metacity + totem + x11 = poor quality
8.) Metacity + totem + gl = does not exist
10.) Metacity + mplayer + x11 = poor quality
11.) Metacity + mplayer + gl = good quality

I Possibly have tried more options and settings, but these are all i can remember. If this was a hardware issue (which hardware is responsible for interlacing movies ?) then test 11 should not have worked.

And sorry, i don't even know yet what is causing the problem... and i don't know who is working on it, and if people are working on it. But by now i am also seriously consodering going back to gutsy...

---

### Post by danwood76 on 2008-05-18
The issue you guys are having is to do with openGL output and compiz.
The two simply cant run together atm.

You either use X11 output (as I do), which IMO the quality with the X11 layer is fine and looks great if sat back a foot from the screen (do you actually watch videos up close?)
Or Switch off compiz and use OpenGL output which does a good job of the interpopulation.

At some point you will have to draw the compromise, or just watch stuff in HD where no interpopulation/anti-aliasing is needed.

---

### Post by SpaceTeddy on 2008-05-18
mhm... if this had always been an issue, i would agree with you. The thing is, it has worked before. Acctually, it had worked with gutsy just fine. So why is the NEW version NOT working anymore ? I guess that is the real question here. Furhtermore, Gutsy is an LTS - why does the LTS bring so many problems that did NOT exist in the normal, previous release ?
btw, why does x11/XShm/Xv not work anymore ? (i have compiz off now).

Also, i want to apologize if my earlier comments may seem agressive or rude. That was not my intention.

---

### Post by danwood76 on 2008-05-18
I had the same issue in gutsy, its to do with compiz using the OpenGL layer and the ati drivers not being able to handle 2 opengl threads.
I believe people have the same issues with 3D gaming and compiz.

I am running compiz + fglrx + vlc w/ X11 and I see no issues with video playback.
I can see slight pixelation if I hold my head 2cm from the screen but seriously I dont watch videos from there or even use my PC from there.

With hardy I have had no problems, and I prefer it to gutsy. Most of the issues I have read about have been caused by the upgrade process as opposed to hardy itself.

---

### Post by SpaceTeddy on 2008-05-18
i canot say anything about 3D gameing, since i don't have any games running in ubuntu. The only thing i use my laptop for is to work and watch movies. For the work, i need compiz (rather, the widget layer, as it hold open terminals and management screenlets for ssh-servers)and for the movies i cannot use compiz.

As for gutsy - i had the xgl server x-server running, which has was handling the graphics card, and anything else used the xgl server to do the rest. For that setup, there was no problem at all to have movies and compiz enabled. With gutsy, the xgl server does NOT hand down the gl support anymore (i.e. when i load xgl the graphics driver go from fglrx to mesa for everything else) thus rendering everything through the CPU - which basicially kills everything. 

As for the quality - i have a default screen resoltion of 1680*1050. The normal video is 720*576. With an Average of 2.3 video pixels per real pixel, i can very well see the difference even from a meter or two away (mind you, this is a 15,4" screen, and i usually watch movies in bed with the laptop on my... lap :) ). The worst of all is writing, since that has sharp edges and just looks shotty.
Anything put a 1080p movie (which my cpu probably cannot handle) is too small for my screen and needs to be recalcualted to fit the screen. And as soon as i am not 1:1, the movies start look shotty...

---

### Post by Kaneda187 on 2008-05-18
I ran mplayer with compiz off the quality is good but could still be better its still slightly and i agree with the whole if you sit back from the screen a bit, but we shouldn't have to!

If this is a driver issue, which it seems to be and it worked fine in gutsy why cant the drivers just be rolled back to the ones that worked?! 

another question...are the current drivers open source or are they from ATI?

---

### Post by spandanj on 2008-05-18
I reported this as a bug for hardy.

please take a look at: [https://bugs.launchpad.net/ubuntu/+bug/231519](https://bugs.launchpad.net/ubuntu/+bug/231519)

---

### Post by SpaceTeddy on 2008-05-18
> **Kaneda187 said:**
> another question...are the current drivers open source or are they from ATI?

afaik the driver from ati are propertary - meaning only ati has the source and can acctually work on them... or so i think it is. Not sure really :(

cheers :)

---

### Post by danwood76 on 2008-05-18
If you use the restricted drivers manager to install the graphics driver then it is the closed source proprietry one from ATI.

At the moment for the R5xx/R6xx based cards this is the only way (I think) to get compiz working as the RadeonHD driver (in its current release state) doesnt support DRI.

Using the Xgl server is a bit of a backwards approiach as XGL is messy and unstable, also puts a lot of stress on the CPU and so decreases performance.

I think you guys will either have to wait for the RadeonHD driver to progress or have a moan at ATI, though apparently something big is going to be fixed in the next release (8.05) but I highly doubt it as we've had those promises for the last few months :)

On my system with an X1950pro sat back on my desk chair at my normal distance from the screen I dont see any noticable pixelation, or at least nothing im going to complain about, I have to get really close to see it properly.
This is using the X11 filter on a 19" screen (1280 x 1024), its the same on my laptop also which has an ATI Xpress 200M so I dont think its GPU dependant.
I suppose you guys are just more fussy than me :) or maybe you have bigger screens ;).

---

### Post by Kaneda187 on 2008-06-03
Anything good news with this problem lately? Im kinda sick of just putting up with bad quality vids!:mad:

---

### Post by Kaneda187 on 2008-06-03
C'mon!!  gotta be something:confused: how do i find out if anything is being done?

the bugs been reported! is anything being done? 

this is a massive issue ther are hundreds of threads about this! there must be a solution!!?:confused:

---

### Post by Kaneda187 on 2008-06-04
still nothing??:confused::mad:

---

### Post by danwood76 on 2008-06-04
The improvement in video quality will come when the graphics drivers get updated.
Asking in the thread every 12 hours isnt going to speed things up.

You just gotta be patient.

---

### Post by xXZeroXx on 2008-08-13
Well, I don't know if you have already solved it, but here's what I did, I installed smplayer and changed the output thing to X11.
It worked perfect!
I have compiz on, and a video with great quality, I couldn't get it to work on vlc, I don't know why.
If this is useful or if you have any questions please ask.
Now I'm going to relax and watch a movie :popcorn:

EDIT:
I was using smplayer but then suddenly the audio accelerated so the video and the audio were out of sinch, I noticed this doesn't happens in vlc.
I discovered that with compiz off and just using metacity, with video output set to X11 the video quality is great, no pixelated image, so I think is a compiz problem.
Anyway, if someone knows how to use compiz and vlc witout sacrificing video quality please comment, please. :(

---

### Post by ellalan on 2008-08-13
Hi
I couldn't make vlc and mplayer work in my PC and I tried gxine and everything works perfect.

---

### Post by xXZeroXx on 2008-08-15
> **ellalan said:**
> Hi
I couldn't make vlc and mplayer work in my PC and I tried gxine and everything works perfect.

Hi, do you know how can I change the output because I see nothing, the only output that works on my computer is X11, but I can't find where to change it. (gxine)

---

### Post by brendanpiater on 2008-08-15
Seems it's compiz settings, this great post fixed (better any way, not perfect) it for me;

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

ATI X700

---

### Post by ellalan on 2008-08-16
> **xXZeroXx said:**
> Hi, do you know how can I change the output because I see nothing, the only output that works on my computer is X11, but I can't find where to change it. (gxine)
I am sorry I do not know how to change the output in gxine, I am sure one of the more experienced in this forum will come up with a solution.

---

### Post by xXZeroXx on 2008-08-16
> **brendanpiater said:**
> Seems it's compiz settings, this great post fixed (better any way, not perfect) it for me;

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

ATI X700

Well, I think it is almost solved, I uninstalled my ATI X700 PCI-E drivers (which I installed with envy), and installed the ati homepage drivers, following the instructions on the unofficial wiki, a lot of problems,then I folowed your instructions finally I did it, now, I changed vlc's output to Default, and, I can't see anything if it is in normal size, but if I zoom it with double click, I can see it, and the image is not pixelated,now the problem is that I can't see anything if it is in normal size unless I change the output to X11, but then, the pixels come back, so, that's why I think it's almost solved.

---

### Post by tarniak on 2008-10-06
I've got the same problem on my kUbuntu. Compiz is disabled by default and the pixelation problem in VLC is still occuring. OpenGL causes VLC to chrash instantly. I've managed to make a workaround, istalling KMplayer, using Xine output and OpenGL module that, eventually, fixed the problem for now. I'm using Radeon 9500 Pro card with restricted drivers. Still, I would appreciate the update.

---

### Post by danwood76 on 2008-10-06
In the latest Intrepid Ibex (Ubuntu 8.10) I have 3d acceleration and openGL in VLC with the latest open source radeonHD (X1950pro), this gives a much smoother image.
I think the restricted drivers just dont work with openGL/X11 very well.

I still have pixelation on Hardy Heron.

---

### Post by fatriff on 2009-04-26
Why don't you use XINE as mentioned at the start of this thread? Mine worked fine in that.

I had rubbish playback, Movie Player and VLC, then I tried Xine and it was as tight as Jessica Alba's *** in a pair of leathers :)

---

### Post by fletcher5634 on 2009-08-07
I am having the same problem. Compiz works very well which makes me also wonder where the problem actually is. I still tried turning down all the appearance settings but have found this does not seem to affect the issue. My sound is often out of time with the video. It does not seem to matter which application I am using to play video with either, even when on youtube the videos have very bad refresh rate and out of sync sound. At times the problem seems to fix itself for a short while. All very confusing. I also have vista installed on another drive and have never had this problem with video.

I have a GeRorce 8500 GT

Any help would be greatly apriciated. I am very new to Ubuntu.

---

### Post by NightwishFan on 2009-08-08
It might be a graphics driver issue. Try setting gstreamer to use x11 video.

[LIST=1]
[*]Press alt+f2, and in the box that comes up type: gstreamer-properties
[*]On the video tab, set the video to x11 instead of xv.
[*]Test a movie in Totem (Movie Player).
[/LIST]

---

### Post by dummiebeginner on 2009-11-16
> **Kaneda187 said:**
> C'mon!!  gotta be something:confused: how do i find out if anything is being done?

the bugs been reported! is anything being done? 

this is a massive issue ther are hundreds of threads about this! there must be a solution!!?:confused:

Add me to the list. Very poor quality videos. Linux is desperating, really. And trying to find the solution even more.

---

### Post by danwood76 on 2009-11-16
> **dummiebeginner said:**
> Add me to the list. Very poor quality videos. Linux is desperating, really. And trying to find the solution even more.

Well the video quality (using X11/Xvideo) is perfect for me in the latest Ubuntu and playback of x264 1080p videos (x264).

Quite often poor video playback is caused by hardware, VLC should be your best bet to get the best quality as it is very lightweight.
Also totem (default player) is very good now too.

This thread is old, my last post was over a year ago.
If you are having issues I would start a new thread as a lot changes in the space of a year in linux.

Starting a new thread specifying your hardware and exact issues will help in troubleshooting your problem.

---

### Post by hivar on 2009-12-22
im having problem a see a "horizontal lines" when playing videos. Someone are good but someone bad. Im using Karmic, nvidia nvidia 8400GS. I think that the problem is in nvidia driver. I have try a lot of seting: xv, gl, gl2..


:D Ok im just figured it out, at least for me helped:

in terminal gstreamer-properties

and in Video tab change Plugin to : X Window System (not Xv)

---

### Post by kirbyboy on 2010-01-03
Hi, i'm having the same problem in karmic, i have an ATI Mobility Radeon HD 4650 in a hp pavilion 1270 ss, and the video quality is very bad.  If i disable the drivers, the quality is good, but the vertical refresh is very bad, changing the gstreamer options only affects to totem, at least for me.  With the drivers enabled, in frames where there is some movement apears like horizontal lines making almost imposible to see a video.

---

