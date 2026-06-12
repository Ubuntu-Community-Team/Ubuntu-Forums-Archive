---
title: "Desktop Zoom: Percentage instead of Pixels for Mouse Restrain Margin"
date: 2008-06-24
forum: General Help
---

### Post by GraysonPeddie on 2008-06-24
Hi. Will there be an option that allows me to change from pixels to percentage for Mouse Restrain Region? I wanted to make the mouse restrain act as a Sync Mouse, because with Sync Mouse enabled, it makes it very hard to get around the screen when interacting with a graphical user interface as the arrow doesn't stay centered. 

For example, in ZoomText for Windows (a magnifier/screen reader tool that installs a "driver hook" (I hated "driver hooks" as it's not compatible with 64-bit version of Windows Vista that I currently have)), when "centered alignment" is chosen, it centers the screen to the mouse except when the zoom window touches the edges of the desktop, which then when I move the mouse to the bottom of the desktop, for example, the vertical screen movement stays there, but the horizontal screen movement can be moved depending on mouse position. So when my zoom window senses my mouse movement moving back to the center of the zoom window, as I continue to move the mouse, the zoom window will stay centered. So I wanted that behavior in Desktop Zoom (in Compiz Fusion). If I set the mouse tracking mode so that ZoomText only moves the zoom window depending on where the mouse pointer touches the sides. that's the effect of having Desktop Zoom's Sync Mouse disabled, but with restraining mouse enabled and restraining margin set to 0 pixels. But in ZoomText, I can specify the margins by percentages.

Let me describe it in ASCII:

```

/------------------------+------------------------\
|                        |                        |
|                        |                        |
|                        |                        |
|                        A                        |
|                        |                        |
|                        |                        |
|                        |                        |
|----B----C----D----E----F----E----D----C----B----|
|                        |                        |
|                        |                        |
|                        |                        |
|                        A                        |
|                        |                        |
|                        |                        |
|                        |                        |
\-------------------------------------------------/

A = X: 50%; Y: 25%
B = X: 10%; Y: 50%
C = X: 20%; Y: 50%
D = X: 30%; Y: 50%
E = X: 40%; Y: 50%
F = X: 50%; Y: 50%
```

As you can see, If I set a restraint margain to 45%, then the zoom area will not move unless the mouse pointer tries to move out of 5% away from center of the zoom area. If the mouse pointer goes over the bounds of the restrained margin area, the zoom area will move depending on the mouse direction, but it won't stay centered all the time due to the set restraining margin.

Now that's out of the way, it'd be great if Desktop Zoom supports input focus/tracking. Or how about integrating features from plug-ins into Orca, a screen reader/magnifier program, on which the magnifier portion of Orca will handle the input focus/tracking by moving the Desktop Zoom's zoom window. For example, a "negative" feature that gets selected in the Orca's magnifier property will enable Compiz Fusion's Negative plug-in.

If Orca can communicate with Compiz Fusion's accessibility plug-ins, tha'd be great for the visually impaired.

I couldn't find a "feature request" forum, but I hope this will be the best place to post in here.

---

### Post by GraysonPeddie on 2008-07-13
Nobody? :(

ZoomText (only magnifier) for Windows seems to be the best (even though subjective) alternative to Compiz Fusion's Enhanced Desktop Zoom, since there's no keyboard focus/tracking that works with Desktop Zoom in Compiz.

I don't mean to be biased toward ZoomText (propriety), but it's nice to be able to have greater accessibility for Linux.

Note that I did use gnome's magnifier (great when working with Orca together), but gnome's magnifier is painfully slow on a 1920x1080 resolution.

So, in the meantime, Compiz Fusion with no keyboard tracking/focus will not make users of ZoomText for Windows to switch to Linux.

Sorry to bump up this thread.

---

### Post by psyopper on 2008-07-13
The Magnifier plugin does this very thing. Choose the "Simple" magnifier and adjust it to it's maximum. I believe the max is 1000x1000 pixels, but the mouse behavior is exactly what you are describing.

I am using Compiz 0.7.6 from the ubutnu ppa repository so I don't know (can't remember) if it is installed with the default 8.04 desktop effects. If you want to try 0.7.6 you can get it from these repositories:

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

If you are running a version prior to Hardy (Gutsy, Feisty) replace hardy in the repo I gave you with the name of your distribution.

---

### Post by GraysonPeddie on 2008-07-16
Oh, okay. I tried the Magnify plug-in but the mouse doesn't scale to fit with the zoom window. With Enhanced Desktop Zoom, it does.

I'm running Ubuntu Studio 8.04.

---

