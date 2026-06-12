---
title: "Can't start emerald or compiz"
date: 2008-07-01
forum: General Help
---

### Post by YellowSnot on 2008-07-01
I've been through everything on the "Great Desktop Effects FAQ of 2008" including running the compiz-check script, which said everything was ok. The system I am having trouble with runs an ATI radeon X850XT video card. When I try to apply one of the visual effects settings in the appearance dialog, everything disappears (except my background) for about 15 seconds, then everything comes back to the original settings. from the terminal I have ran the following commands:

compiz --replace

which gives the following output:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:5d52 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Couldn't find a perfect decorator match; trying all decorators
Starting emerald

from there everything disappears (except my desktop background)

I have also ran the command:
emerald --replace

but it just hangs, and does nothing. In the process manager it says the emerald process is sleeping.

It would seem to me that the system is having trouble starting emerald. If you think this is the case, are there any logs or anything to look through to see what the problem may be. What else do you think could be causing this? All my other computers run compiz w/out a problem, and its always seemed quite straight forward to me until trying to get it to run on this system.

---

### Post by YellowSnot on 2008-07-02
Well, I just spent an hour compiling emerald from source, hoping that might fix my problem, but it didn't. Does anyone know whether compiz or emerald keep log files I could look through?

---

### Post by isaacj87 on 2008-07-02
Hey,

How did you install you ATI drivers and could you try installing the fusion-icon and seeing if that helps? I know it sounds strange, but sometimes it helped me.

```
sudo apt-get install fusion-icon
```

It'll be located under Applications->System Tools

---

### Post by YellowSnot on 2008-07-02
I installed the ati driver with the ubuntu restricted driver manager gui.

after installing fusion-icon it does basically the same thing that running compiz --replace did. (makes everything disappear but my background)

the output of the command run from command line is:

Couldn't find a perfect decorator match; trying all decorators
Starting emerald
 * Detected Session: gnome
 * Searching for installed applications...
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp

any more ideas?

---

### Post by walker9010 on 2008-07-02
I'm having the exact same problem...with a Radeon X1600

I'm pretty sure when the background disappears there is a timer counting for a revert--as you can't see anything, you aren't hiting "accept" in time so the display reverts.

Not that that really helps, but just FYI.

One thing you could try would be to run Envy and make sure your drivers are up to date... it will query and install them for you.

```
sudo apt-get install envyng-core
```

and then run it from Applications/System Tools.

Introduction to Envy here: [http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

---

### Post by YellowSnot on 2008-07-02
Well, it's nice to know I'm not alone here! I was guessing that the reason my screen came back when I used the gui was because of a timer. The computer is now back with the rightful owners, but I should have a chance to install envy on it tomorrow. I just upgraded this machine to hardy a couple days ago, and installed the driver then, so unless envy has a driver that is newer than that in the current ubuntu repository I'm not sure this is going to do much. Do you know whether this is the case? This isn't a new issue with Hardy, I wasn't able to get compiz working in gutsy on this machine either, but gave up w/out digging very deep into the issue.

---

### Post by walker9010 on 2008-07-03
I was having the same thought (as I just installed Hardy as well) yet before I ran Envy I was having a complete white screen (ever see something similar?) and after I...upgraded...if you will, to being able to see the desktop background only.

Clearly something was being updated, but I'm not entirely sure what (and since it didn't fix the problem, I'm not that inclined to go out and figure out what it was. Only so much time in the world...

Just for kicks, I installed KDE to see if the same thing, and it went back to whitescreening when I tried to enable desktop effects there (no auto-revert though, so I had to end the session to get out)

---

### Post by walker9010 on 2008-07-03
bump

---

### Post by Timemaster on 2008-07-04
I think the problem is that you don't have a good enough graphics card. what you might want to try (if you have the money and think it's worth it) get a better graphics card. I'm not completely sure but every computer can use a better graphics card anyway.

---

