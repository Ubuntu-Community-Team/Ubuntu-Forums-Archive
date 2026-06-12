---
title: "ATI, Google Earth, Beryl, and the opensource driver"
date: 2007-04-23
forum: General Help
---

### Post by inigmatus on 2007-04-23
I need help confirming what I tested it out:


With the opensource ATI driver, Beryl works, and other 3d rendering works; however Google Earth renders very very very slow.

With the new ATI proprietary driver Google Earth works, and other 3d rendering works (even better and faster), however Beryl of course does not - at least not without adding an Xgl desktop which is buggy, runs slow a bit, and totally can kill x-sessions at the drop of a hat...er window.

So then,

what to do? As an ATI owner, is this really a choice then between deciding in participating in a stable ATI opensource-Beryl marriage without the Google Earth, or an unstable ATI proprietary-Xgl-Beryl threesome, with the potentional of also seeing Google Earth in action whenever I wish to logout and log back in?

Do I have to make a decision between Google Earth and Beryl?

Or should I just wait for Beryl to mature?

and please, we ATI owners don't need NVIDIA users adding their two cents into this convo. As a former Windows user, saying to me to "dump the ATI hardware" is like saying that Linux isn't ready unless I "dump the hardware." Thanks. 

NVIDIA owers need not respond. :P

---

### Post by SishGupta on 2007-04-23
> **inigmatus said:**
> I need help confirming what I tested it out:


With the opensource ATI driver, Beryl works, and other 3d rendering works; however Google Earth renders very very very slow.

With the new ATI proprietary driver Google Earth works, and other 3d rendering works (even better and faster), however Beryl of course does not - at least not without adding an Xgl desktop which is buggy, runs slow a bit, and totally can kill x-sessions at the drop of a hat...er window.

So then,

what to do? As an ATI owner, is this really a choice then between deciding in participating in a stable ATI opensource-Beryl marriage without the Google Earth, or an unstable ATI proprietary-Xgl-Beryl threesome, with the potentional of also seeing Google Earth in action whenever I wish to logout and log back in?

Do I have to make a decision between Google Earth and Beryl?

Or should I just wait for Beryl to mature?

and please, we ATI owners don't need NVIDIA users adding their two cents into this convo. As a former Windows user, saying to me to "dump the ATI hardware" is like saying that Linux isn't ready unless I "dump the hardware." Thanks. 

NVIDIA owers need not respond. :P

This is old hat. If you read the forums most of this is already talked about.

For beryl/desktop effects to work well it requires the GLX_from_pixmap extension.

The open source ATI drivers have this extension, but they are slow drivers because they are not official.
The closed source ATI drivers do not have this extension, but they render faster because they are official.

Truly, and I know you do not want to hear it, your best option is to vote with your money. If you want ATI to listen you can try writing them (but they likely don't care), or you can stop buying their products (which they definitely do care about).

Another option is to learn the necessary development skills, join the open source ATI movement and make some drivers that don't suck.

IMHO this isn't a beryl/3d desktop maturity problem, but an ATI one. They need to start treating their customers better, with more respect, and stop ditching old users or users on the margin.

I am an ATI and Nvidia user, but I will never buy an ATI card again simply because drivers for windows and for Linux are utter trash and ATI will write off users with old cards or users on other OS's faster than you can say ATI.

Your "what to do" question is very personal. If you use 3d apps like google earth a lot, use the official drivers. If you don't and would rather see desktop effects, use the OSS driver.

---

### Post by WHICKS on 2007-04-23
I had problems with my 9200 ATI card, and I did a google search, and found this excellent tutorial.  I followed it step by step and my card is working great with beryl, google etc.  I haven't got emerald working yet, but all the other eye candy is working great.  Maybe try re-installing beryl as suggested by FALKO here:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by inigmatus on 2007-04-24
Thanks. I followed that guide to use the opensource driver during one of my tests - and I even did the unstable ATI- Xgl way just for good measure. The opensource that it installs makes Beryl run good, but GoogleEarth just crawls. The ATI-Xgl makes Google scream, but Beryl is so unstable as to make it unusable for production (and besides I have to swich to Xgl desktop every time to just use it).

I installed the proprietary driver last night for ATI since I use a lot of 3D modeling programs. Too bad. Beryl could have been useful in my development work.

I too own both NVIDIA and ATI, and I won't buy ATI ever (in fact the ATI I am using was given to me for free - 128MB vs my 16MB NIVIDA, kinda hard not to choose using the ATI card at the moment).

---

### Post by eode on 2007-06-28
Well, this isn't the best solution, but:

```
DISPLAY=:0.0 ./googleearth
```

will run google earth above the XGL xserver.  The problem is that it isn't managed, so without some weird tweaking, it's a pain to deal with.  If you have the time/care to do it, the basic concept is that XGL (currently an unmanaged window) becomes a managed window, and Google Earth runs on the same display that XGL is in, rather than running inside the one XGL provides.

1) have a very basic and very configurable window manager run *before* XGL.
2) Set XGL to be a borderless window
3) Set a hotkey in your hidden window-manager that allows you to switch between non-XGL windows (I.e., XGL itself, Google earth, and anything else you run on display 0).  Make sure it doesn't conflict with a key combo you already use (try, for example, CTRL-Alt-Tab, if you're not using that in beryl).
4) Get rid of any other hotkeys your base window-manager has, so that they don't interfere with your XGL session either.

The Ratpoison window manager might be a good choice.

---

### Post by tepidarium on 2007-08-06
I am having the same problem. I have an Ati x1400 128 mb video card.  I can run Beryl fine in XGL session.  I cannot run Google Earth (or, I fear, other 3d rendering apps).  

For me to run Google earth, I need to shut down my computer and restart and not use an xgl session.  

It seems that it is a choice between running Google Earth or having desktop effects - can't do both at the same time.

Will ATI ever release better drivers?!

---

### Post by tlacuache on 2007-08-07
For my laptop I finally decided that I'd rather have my other 3d apps work and forget beryl for now. I worked on it forever, too, but finally gave up.

My next laptop will definitely have an NVidia card in it, like in my desktop. Everything works out of the box.

---

### Post by daWsOn_s on 2007-08-12
Hi I have the exact same problem with Compiz :( I have now decide what to do, google earth or desktop effects? :confused:
Anyway it's not only that because with the open drivers and compiz enabled I'm not able to see videos (in vlc for example) and the video output doesn't "follow" the effects like 3d cube, it just doesn't show in any movement.
Of course in Xgl compiz and video works fine together but Google Earth won't start or crashes 

What can we actually do?

I have ati radeon 9600 pro.

---

