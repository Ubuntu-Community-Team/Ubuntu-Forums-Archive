---
title: "Question about systray in Cairo-dock"
date: 2008-05-25
forum: General Help
---

### Post by Chonnawonga on 2008-05-25
I just installed the latest build of Cairo-dock (1.5.6) and I'm loving it. I have one annoying problem, though: instead of the systray appearing on the dock with everything else, it appears in a little bubble off on its own. (It looks like a speech bubble: see attachment.) This wouldn't be such a big deal, except that even when the panel is collapsed (auto-hidden) the systray bubble still appears on the screen, and it gets in the way.

Anybody know what might be causing this, or how I could fix it? I've tried playing around with the options, but to no avail.

Thanks!

---

### Post by fabounet on 2008-05-28
left-click to show the bubble, middle click to hide it.
or just detach the applet from the dock to make it a desklet, and place it in a corner of your screen.

---

### Post by Chonnawonga on 2008-05-28
Hi fabounet!

Thanks for the tips! That much is good to know. Ideally, though, what I'd like to do is make the systray icons a part of the main dock, showing up on the same level as the launchers, etc. Do you know if that's possible?

---

### Post by VeeDubb on 2009-01-26
I've wanted to do the same thing since the first time I tried cairo-dock.

The default functionality is terrible, and having a systray that is only viewable by minimizing all your windows or switching desktops, which is what is required if you use it as a desklet, just really stinks.

I just can't believe that programmers capable of coming up with something as great as cairo-dock can't put together a notification area plugin that works in a useful manner.  It's just insane.

So, I'm suck with one of the following options:
A. Use AWN which consistantly has all sort of horrible visual artifacts on my machine (and I've tried several versions)
B. Use cairo-dock with a minimally functional systray
C. Keep using at least one of the gnome panels.

That just stinks.

---

### Post by fabounet on 2009-01-26
I personnally use the systray of CD in desklet mode, letting it either above other window or on the Widget Layer.
but I don't use it so much (only for the Network applet), so it's not so harmful.
the systray mechanism on X is just awful in case you don't know.
so it wil need time ... or some volunterer.

---

### Post by VeeDubb on 2009-01-26
> **fabounet said:**
> 
the systray mechanism on X is just awful in case you don't know.
so it wil need time ... or some volunterer.

So I've found in my reading. 

If I only used it for the network applet I'd just do without and fire up the network manager on the rare occasion that I actually needed it.

But, I need it for pidgin notifications, synce tray-icon, and a variety of apps that have really well "minimize to tray" features.

For now, I'm just using it in the doc, because then I can at least take a look at it when I'm using a program in full screen, which is my main reason for using a dock instead of gnome-panels anyway.  It doesn't make any sense to me, to buy a nice big widescreen LCD, and then waste a bunch of screen real estate with gnome-panels.

---

### Post by VeeDubb on 2009-01-26
What I don't understand, is why having the X implementation for system tray icons suck, causes a problem.

The latest release of AWN has finally gotten their notification area applet to work flawlessly on my system.  

If it wasn't for the fact that half of their other applets are perpetually broken and the thing always has really ugly visual artifacts on my system, I'd switch to AWN and never look back.

I just want the stupid bubble that C-D puts their systray in to be displayed as part of the dock instead of as a floating bubble.

---

### Post by fabounet on 2009-01-27
yep but the code of the systray applet is a big hack, just the code of gnome-panel taken by force, and put into a dialog window (or a desklet).
the dock can't handle gtk-widget easily because they can't zoom, and they are tooooo slow to move/resize.
when gtk will do nice widget, we'll be able to use the gnome-panel's applets in the dock. until that moment, we have to make our own applets, and the systray is quite hard to do.

Probably Cairo-Dock2 will solve all of these problems though.

---

### Post by VeeDubb on 2009-01-27
Oh cool, I just realized I'm actually talking to the main dev for cairo-dock.

FWIW, with the exception of the systray, I LOVE cairo-dock.  Puts the others to shame.  Having one program that combines docks and desklets and works as smoothly as cairo-dock does is a god send.  

Frankly, I'm not sure why AWN is so popular.

I'm using 2.0.0-beta1 right now, and love it.

I'm not much of a programmer, but if you ever need somebody to beta test a better systray, I'll be first in line.


A side note you might pass along to whoever does the compilation script to compile from source, there are a TON of dependencies it doesn't check for.  I finally got it installed from debs, but even then I had to run getlibs to make it work.  Awesome now though.

---

### Post by fabounet on 2009-01-28
because it's 1 year older than CD ? ^_^
anyway thanks for your report
improving the systray is on the TODO list of the 2.0 (beta3 maybe) :-)

---

### Post by dasbooter on 2009-02-12
> **fabounet said:**
> because it's 1 year older than CD ? ^_^
anyway thanks for your report
improving the systray is on the TODO list of the 2.0 (beta3 maybe) :-)

Just thought I would drop a little thanks here Fab.A good dock is hard to find.

Kiba-dock = stalled dev and memory leaks on my system
AWN = horrible artifacts on my machine also
Cairo-dock = Stylish, lost of glitz, flare, workability. I had to sort of beat it into submission to get it to work(alas I could not compile from SVN but that is my own issue). I am not sure if the stacks applet behav is proper?

I also will retain one gnome-panel for the systray. I sort of wish Ubuntu would champion/back the dev of new dock. Gnome-panel is really archaic I mean I cant even configure it to stay behind windows and pop up when needed.Desktops are moving forward and thanks to the forward thinking of devs like Fab we have some great tools.

---

### Post by fabounet on 2009-02-13
so many things to do and so few time ^_^
your support is welcome, thanks :-)

---

### Post by wingnux on 2009-05-14
I've just installed cairo-dock 2 and it works great! Yeah, there's this systray issue but I hope it gets a workaround soon.

My question is: Is there any way to forcibly delete ALL gnome panels? I'm pretty happy with CD so I don't need any panel taking unnecessary space but the panel help says that "You must always have at least one panel in the GNOME Desktop.
If you have only one panel in the GNOME Desktop, you cannot delete that panel." =/

---

### Post by fabounet on 2009-05-15
in gconf, you can delete a key containing the word "panel"
then after restarting gnome, no more gnome-panel :-)
detaching the systray from the dock and place it in a corner of the desktop, keeping it above other window, is the only fix I know about the systray.

---

### Post by wingnux on 2009-05-15
Thank you VERY MUCH! =)

---

### Post by fafbox on 2010-07-31
I'm using both CD and Awn...in order to use best applets from each other...
ex: systrey is better on Awn (i hope only for the moment :)) but stacks applet is better in CD

my settings:
awn has an extended panel and both docks are auto-hiding...
CD is centered while awn is on the right
attached are some print screens

"There are no problems, only solutions" !

---

### Post by bobcollard on 2010-07-31
Cairo Dock 2.1.3 on Xubuntu 10.04, hidden Panel, notifications come up on desktop for Exaile, Thunderbird and Gmail-Notify.  Hidden Dock with clean look for desktop.  Love it and no complaints.

---

