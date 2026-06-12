---
title: "opera - floating point exception"
date: 2006-12-26
forum: General Help
---

### Post by decideci on 2006-12-26
EDIT: FIXED - mix ups in xorg.conf due to ati driver installs and getting openGL hardware support to work. some options got missing and that somehow screwed up some things. 
now everything seems to work as expected. the drivers are working, opera starts. :) 


hey there!
i just recently installed ubuntu 6.1 on a spare HD i had lying around and am loving it so far. 
i figured lots of stuff out already, i am pretty experienced with computers but never got into linux until now. i love and use opera on my windows system and was really happy to find out that it is available for linux too. but it just refuse to work on my system!

i tried both versions (shared QT, static QT) of the latest build of opera, tried the TAR archive install, even an older version. checked my installed packages. i also followed all the opera tutorials i found on the ubuntu help sites. 
it installs fine. when i click on the opera icon _nothing_ happens!
starting opera in a terminal window results in:

Floating point exception (core dumped)

some additional infos: 
x: gnome
kernel:  2.6.17-10-generic
cpu: amd athlon 2600+
gpu: ati radeon 9600


it is a pretty clean install. i just configured the xorg.conf to run with my gpu and monitor (1280*1024@real100hz - with modelines settings) and also had to install alsa tools with envy24control to support my staudio dsp24 soundcard (the standard volume control simply does not work with the soundcard). but all that is working perfectly now. 
only opera seems to hate me :(

if anyone can maybe give me insights on what i did do wrong or what to do to fix this, i would be very thankful! 

with best regards,

deci.

---

### Post by decideci on 2006-12-26
it seems that i narrowed down the problem.
reconfiguring xserver-xorg did the trick. but! 
now (of course) my custom settings with the ati driver stuff are gone and my monitor switched back to 85hz and no openGL support! 
there must be a way to get both: 100hz and openGL hardware usage AND using opera! 

i will try fiddling around with the xorg.conf a bit more. if someone have any insights, i still appreciate any help :)

---

### Post by me4oslav on 2007-12-04
I am having the same problem with opera and when i make dpkg-reconfigure xserver-xorg the only effect was that i was lucky having a backup of it so i can copy it to /etc/X11/ from recovery mod,because i wasn't having a GUI.I am also having few more problems.My kaffeine give me a line instead of a picture,my xine doesn't start neither my totem does(he is with gstreamer engine)I have tried compiling and reinstaling kaffeine,xine-ui,libxine( 1.1.7 and 1.1.8 ),totem but there is no effect.Please help me,because this problems is are very annoying and i am not keen on formating my hard disk again,and even more-my father want to install Feisty Fawn and wait to April for the 8.04 Hardy Heron,i have tried to explain him that the feisty will update to gutsy and there will be no effect,but he doesn't list.He is stubborn as a donkey.
So please help me.
:confused:

---

### Post by treris on 2007-12-07
me4oslav

Recently there have been some problems with firefox and floating point exception, have you recently updated a package called libcairo2?

---

### Post by me4oslav on 2007-12-09
well,my libcairo2 is installed and it is version: 1.4.10-1.The problem appeared after i have set my monitor to IBM 6445 G72(it is the model of my monitor) and i should use recovery mod to copy the original xorg.conf from ~/VeryImportant(i have copied it before i changing my monitor) to /etc/X11/ because my GUI disappeared.Opera was working with the original xorg.conf but after the copy opera screwed up.Any ideas?

---

### Post by treris on 2007-12-09
Excuse me for probing but is the installed version of libcairo2 1.4.10-1ubuntu4 or 1.4.10-1ubuntu4.1?

The problems with firefox I've recently come across were caused by the update from the ubuntu4 to the ubuntu4.1 version. If you are still having problems with floating core exceptions you could try downgrading libcairo2 to the previous version using synaptic, see if that helps.

---

### Post by me4oslav on 2007-12-11
well,i have installed the old version of the libcairo,but there is no effect.Other ideas?

---

### Post by treris on 2007-12-12
if that doesn't work it must be something completely different from the problem I had in Firefox, I'm afraid I'm out of ideas, you might want to check launchpad to see if there are any bugs posted there.

---

### Post by me4oslav on 2007-12-13
i am pretty sure that my monitor is the problem.It is very old and when i have installed ubuntu gutsy it doesn't recognise my resolution like the feisty did.I have installed ubuntu on a pc with brand new LG LCD 17 and there were no problems.The opera worked fine,it recognise the resolution avaivable for him's monitor the xine which he installed by typing: sudo apt-get install xine* was working perfectly,too.No problems.

---

### Post by me4oslav on 2007-12-16
well,i have fixed the problem.I bought myself a new monitor and everything works just fine.Thanks for the help.

---

