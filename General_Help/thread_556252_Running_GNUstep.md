---
title: "Running GNUstep"
date: 2007-09-21
forum: General Help
---

### Post by RocketBoy on 2007-09-21
Alright, this is going to sound very newbish. I've installed all of the packages via synaptic that I think I needed to install and I just can't figure out how to actually **start** GNUstep. Nothing new showed up in any menu's or in my boot screen. I just don't think I know what I'm looking for.

---

### Post by Mark Grice on 2007-10-30
From the GNUStep Users FAQ:

>  1.1.7 How do you run GNUstep?

You are presumably under the misapprehension that GNUstep is some sort of program or window manager.

It isn't.

GNUstep is a whole load of things -- primarily a set of libraries for developing software.

At present, it's those libraries, plus various command-line based support tools and service providing daemons, plus various GUI development tools, a GUI desktop/workspace application, etc.

At no stage will you ever 'run' GNUstep -- you will run applications and tools and will make use of it's services. At some point you may well find packages distributed as 'GNUstep' systems in the way that you get 'GNU/Linux' systems packaged today. Look at Simply GNUstep [http://simplygnustep.sourceforge.net/](http://simplygnustep.sourceforge.net/) for instance.

If you want to see a sample GUI application running you need to build GNUstep and look at the example applications in the gnustep-examples package. Build 'Finger' or 'Ink' and start it with 'openapp Finger.app' or 'openapp Ink.app'

To look best, use WindowMaker (the currently preferred GNUstep window manager) as your window manager. 

---

