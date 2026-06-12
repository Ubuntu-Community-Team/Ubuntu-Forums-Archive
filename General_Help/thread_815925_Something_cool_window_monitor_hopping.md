---
title: "Something cool: window monitor hopping"
date: 2008-06-02
forum: General Help
---

### Post by gfixler on 2008-06-02
Sorry - this is a bit of a long read, but if you have multiple monitors spread out side-by-side, with shared resolution (e.g. 0 through n, where n is the right side of the rightmost monitor), then this should let you use hotkeys to push windows back and forth between them.

I borrowed very freely from jamesrl's work found [at this link]("http://ubuntuforums.org/showthread.php?t=522523&highlight=xprop+xwininfo+wmctrl"). Mostly, I just turned it into functions, such that I could reuse elements for different needs, and made it work with any number of monitors, with little tweaking. His swaps between two screens. Mine requires you to provide left/right, and just moves 1 in that direction

NOTE: I'm using the Matrox TripleHead2Go Digital Edition with 3 1280x1024 monitors. The TH2G looks like one huge 3840x1024 screen to Ubuntu (one DVI to the box, 1 to each screen). I'm also running Compiz Fusion (in Hardy), and because of the TH2G, have in the CompizConfig Settings Manager, Display Settings tab, Outputs section, the following outputs:

1280x1024+0+0
1280x1024+1280+0
1280x1024+2560+0

I also have the "Detect Outputs" checkbox just above those unchecked. This all lets the system work more like having 3 separate screens. E.g., I can maximize, and fullscreen to each monitor, instead of having everything expand across all 3 as was happening before setting up the outputs. Usually, windows pop up where I don't want them (I know about Devil's Pie, but it's too much work to set up for *every* program, plus I often don't want the same thing as last time), or I just want to slide a window out of the way for a moment without reaching for the mouse, especially when feverishly coding in several windows :)

I ended up taking out my code that checked if you went off the left, or right side of the screen, because I found that in Compiz, if I did, it actually spun the cube around, and still placed the window properly on the next screen in the right order (e.g. moving off the right screen would spin the cube, leaving the window now on the left screen)! You might want to add that back in if you're on a different setup, or you might lose windows off the edges.

Check after the code for how to use it.

```
#!/bin/bash
# swap_monitor.sh (original version)
# Moves the active window to the other screen of a dual-screen Xinerama setup.
#
# movewin.sh (modified version)
# allows movement of windows left and right between multiple monitors
#
# Requires: wmctrl, xprop, xwininfo
#
# Original Author: Raphael Wimmer
# raphman@gmx.de
#
# Modified by: Gary Fixler
# gfixler+bash@gmail.com

function getNumberOfMonitors
{
    # simply must be hardcoded
    # e.g. MatroxTripleHead2Go can service 3 screens,
    # but appears as only one monitor to the computer

    # change to your number of monitors
    echo 3
}

function getMonitorWidth
{
    numberOfMonitors=$(getNumberOfMonitors)
    monitorLine=$(xwininfo -root | grep "Width")
    monitorWidth=$((${monitorLine:8}/$numberOfMonitors ))
    echo $monitorWidth
}

function getActiveWindowID
{
    activeWinLine=$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)")
    activeWinID="${activeWinLine:40}"
    echo $activeWinID
}

function getActiveWindowHorizontalPosition
{
    activeWinID=$(getActiveWindowID)
    xPosLine=$(xwininfo -id $activeWinID | grep "Absolute upper-left X")
    xPos=${xPosLine:25}
    echo $xPos
}

function getActiveWindowWidth
{
    activeWinID=$(getActiveWindowID)
    xWidthLine=$(xwininfo -id $activeWinID | grep "Width")
    xWidth=${xWidthLine:8}
    echo $xWidth
}

function getActiveWindowCurrentMonitor
{
    numberOfMonitors=$(getNumberOfMonitors)
    monitorWidth=$(getMonitorWidth)
    activeWinID=$(getActiveWindowID)
    xPos=$(getActiveWindowHorizontalPosition)
    i="0"
    while [ $xPos -gt $monitorWidth ]
    do
        xPos=$[$xPos-$monitorWidth]
        i=$[$i+1]
    done
    echo $i
}

function getActiveWindowPositionOneMonitorToTheLeft
{
    monitorWidth=$(getMonitorWidth)
    currentMonitor=$(getActiveWindowCurrentMonitor)
    activeWinID=$(getActiveWindowID)
    xPos=$(getActiveWindowHorizontalPosition)
    xPos=$[$xPos-$monitorWidth]
    echo $xPos
}

function getActiveWindowPositionOneMonitorToTheRight
{
    monitorWidth=$(getMonitorWidth)
    numberOfMonitors=$(getNumberOfMonitors)
    currentMonitor=$(getActiveWindowCurrentMonitor)
    activeWinID=$(getActiveWindowID)
    xPos=$(getActiveWindowHorizontalPosition)
    xPos=$[$xPos+$monitorWidth]
    echo $xPos
}

function changeActiveWindowMonitor
{
    activeWinID=$(getActiveWindowID)
    if [ $1 -eq "0" ]
    then
        newXPos=$(getActiveWindowPositionOneMonitorToTheLeft)
        newXPos=$[$newXPos-5]
    else
        newXPos=$(getActiveWindowPositionOneMonitorToTheRight)
        newXPos=$[$newXPos-5]
    fi

    winState=$(xprop -id ${activeWinID} | grep "_NET_WM_STATE(ATOM)" )

    if [[ `echo ${winState} | grep "_NET_WM_STATE_MAXIMIZED_HORZ"` != "" ]]
        then
        maxH=1
        wmctrl -i -r ${activeWinID} -b remove,maximized_horz
    fi

    if [[ `echo ${winState} | grep "_NET_WM_STATE_MAXIMIZED_VERT"` != "" ]]
        then
        maxV=1
        wmctrl -i -r ${activeWinID} -b remove,maximized_vert
    fi

    if [[ `echo ${winState} | grep "_NET_WM_STATE_FULLSCREEN"` != "" ]]
        then
        fulls=1
        wmctrl -i -r ${activeWinID} -b remove,fullscreen
    fi

    # move window (finally)
    wmctrl -i -r ${activeWinID} -e 0,${newXPos},-1,-1,-1

    # restore maximization
    ((${maxV})) && wmctrl -i -r ${activeWinID} -b add,maximized_vert
    ((${maxH})) && wmctrl -i -r ${activeWinID} -b add,maximized_horz
    ((${fulls})) && wmctrl -i -r ${activeWinID} -b add,fullscreen

    # raise window (seems to be necessary sometimes)
    wmctrl -i -a ${activeWinID}

}

function moveActiveWindowOneMonitorToTheLeft
{
    changeActiveWindowMonitor 0
}

function moveActiveWindowOneMonitorToTheRight
{
    changeActiveWindowMonitor 1
}

"$1"

exit 0
```

Now to use it... As I'm using Compiz Fusion on Hardy, I did the hotkey assignments through the CompizConfig Settings Manager. Adjust for your needs. In the General section, Commands tab, under Commands, I made two entries:

/home/gfixler/scripts/winmonmv.sh moveActiveWindowOneMonitorToTheLeft

/home/gfixler/scripts/winmonmv.sh moveActiveWindowOneMonitorToTheRight

Obviously, that first bit is the path to my script (winmonmv.sh), but the trailing bit is the argument passed to it, which is read at the end, causing the right function to kick off. I've mapped the commands to Alt+h, and Alt+l, so I can move the windows left and right in a manner similar to character moves in Vim - just my preference. Map them however you want. Also, change the 'echo 3' line in the first function to however many monitors you have - I can't even detect that on the TH2G, so I didn't bother to automate it in any way.

I actually considered not posting this, just because it's so bizarre, and one-off, but I figured it would help some folks, either by providing some working bash script to dig through for useful nuggets, or because if you're like me, you'll actually consider purchasing something like a Matrox TH2G (no affiliation) when you find useful code like this that makes it more functional, and 'cool.'

Anyway, now when I hit Alt+h, and Alt+l, the active window will move one screen left, or right, keeping in the same location to the pixel. Note that I did have to add 5 to each in the changeActiveWindowMonitor function, to account for my decorator (window frames). You might need to adjust this if your decorations don't match. An easy way to tell is to butt the window up against one edge of a monitor, then jump it over, and see if it's on the edge of the other. Also, jump back and forth, and see if an error accumulates, and adjust those 5 values to compensate, if needed.

Good luck!

---

### Post by jbinto on 2008-06-21
Excellent, exactly what I've been looking for, and works pretty well. I haven't looked at it too hard, but from some strange behaviour, I think it assumes the monitors are the same width. I'll have to look at it later.

I'm shocked GNOME doesn't have something like this built in like KDE. But then again, considering GNOME's "the user is a moron" philosophy, and how difficult it actually was to do something so simple (bind commands to keys in gconf-editor), I'm not so surprised really.

I should mention I'm running an Intel 945GM on a laptop with a CRT to my right. The reason I needed something like this is sometimes I'm still in dual monitor mode but I've disconnected the CRT (or don't want to hook it up) and I need to move a window. 

Thanks!

---

### Post by Vadi on 2008-06-21
> **jbinto said:**
> I'm shocked GNOME doesn't have something like this built in like KDE. But then again, considering GNOME's "the user is a moron" philosophy, and how difficult it actually was to do something so simple (bind commands to keys in gconf-editor), I'm not so surprised really.

Maybe it's not designed for you?

---

### Post by detrate on 2008-11-24
I've had a very stressful day today.  Yesterday my friend reminded me I should enable advanced desktop effects.  It had some window focus errors and I was googling on how to fix them.  I came across the predecessor of this this thread, which led me here and my jaw dropped.

I've been looking for this forever since I abandoned windows and ultramon.  I love you so much right now.

It works wonderfully.

---

### Post by gfixler on 2008-11-24
> **detrate said:**
> It works wonderfully.

Excellent! I'm glad to hear it, detrate :)

---

### Post by loomsen on 2008-11-24
OK, that's a nice Script, chapeau. But why don't you use TwinView? Wouldn't it have been a lot easier Configuring your xorg.conf?

Anyway, as I have my TV attached, and resolutions are far off being similar, TwinView hasn't ever been an option for me anyway.

That the Cube spins is just due to the X-Servers nature. Compiz wouldn't and couldn't work otherwise (usually Compiz, or the graphics device more likely, draws windows even if they are directed to OffScreenPixmaps)

Definition of what works and what doesn't is due to the style chosen to enlarge the Desktop. TwinView virtualizes One Large Desktop, which is drawn by one graphics device. That's why Xinerama will work in TwinView, cause the video device controls the Output.

If you have different resolutions across your screens, you either have to specify the lowest over all, or a part of your smallest screen is drawn OffScreen with TwinView.

And that's exactly the point why Xinerama doesn't work with separate X-Screens, because Output is managed by two different(even tho it's the same, just virtualized to being two different) video devices.

Anyway, I'll try it, see if it works for different resolutions as well.

Thx for sharing!

---

### Post by detrate on 2008-11-25
> **loomsen said:**
> OK, that's a nice Script, chapeau. But why don't you use TwinView? Wouldn't it have been a lot easier Configuring your xorg.conf?

I'm using this with TwinView and it works like magic.  It even wraps around my compiz cube to the next virtual desktop.  It's smooth like butter.


Xinerama = major lose if you're trying to play games, at least in my experience.  I switched to TwinView a while ago because xinerama was trying to steal my mouse when I tried to turn right.  I had to run a separate xorg.conf to null out my second monitor which meant I couldn't run my games in windowed mode and peep IRC.  TwinView has its downfalls, like supporting only one card (my second card is doing nothing) and supporting only 2 monitors (as the name implies by still, lame).

Anyway... I digress.  This application is exactly what I wanted / needed.

---

### Post by gfixler on 2008-11-25
> **loomsen said:**
> OK, that's a nice Script, chapeau. But why don't you use TwinView? Wouldn't it have been a lot easier Configuring your xorg.conf?

I'm on a pretty weird setup. I have 3 identical monitors, and they're all connected to a [Matrox TripleHead2Go Digital Edition]("http://techgage.com/print/matrox_triplehead2go_digital_edition"). The Matrox is only connected to one DVI output of my video card. The other one has nothing connected. The computer sees the Matrox box, which looks like a triple-wide monitor. It takes that triple-wide signal and sends 1/3rd to each monitor. TwinView wouldn't do anything for me here.

I'd like to hear about your setup and how this works for you if you try it, and feel like sharing your experience. Thanks!

---

### Post by ChrisMoose on 2009-02-13
Ahhh... a thousand blessings on your head, sir! I'm also a new convert to Ubuntu, and was missing the UltraMon shortcuts.

FWIW, I'm running TwinView with two monitors, and this works like a champ.

Any ideas about adding UltraMon's ability to stretch a window across both monitors? I used this when working in my IDE of choice quite a bit. I can do it manually, of course, but it'd be nice to have. I may do some tinkering and report back.

Again, thanks!

---

### Post by gfixler on 2009-02-14
> **ChrisMoose said:**
> Any ideas about adding UltraMon's ability to stretch a window across both monitors? I used this when working in my IDE of choice quite a bit. I can do it manually, of course, but it'd be nice to have. I may do some tinkering and report back.

Again, thanks!

Thanks, ChrisMoose. I don't immediately know how to do that, but I'm wondering if you can just use the stuff I posted to set the window to double the width of a screen, and move it to the top-left corner of the left one. My monitor setup is weird, wherein all 3 seem like 1 to my computer, so my computer thinks of it as a triple wide width resolution value. I can move things anywhere across all 3. I'm not sure if it works the same way if not using a Matrox TripleHead2Go to do what I'm doing.

Worth a shot, though! I'd like to hear if you get anything working.

---

### Post by beefcurry on 2009-04-11
this does work like a charm on twinview.

---

### Post by koekiemonster on 2010-06-28
a very nice script. it inspired me to make a maximize on both monitors script, you can find it here:

[http://ubuntuforums.org/showthread.php?p=9523601#post9523601](http://ubuntuforums.org/showthread.php?p=9523601#post9523601)

all we need now is to get the buttons into the windowbar and we're done! :guitar:

---

### Post by niki+a on 2011-01-02
Nice.

Just one comment:

Don't know if this is system or environment or bash version specific issue (and don't care enough to investigate), but on Ubuntu 10.04 64 bit edition move from left to right did not work, until I changed the following line:

```
    
if [ $1 -eq 0 ] #line 96 remove "0" (quotes from 0)

```

Awesome script, simple and works right now out of the box.

Oh, one more thing, had to: 

```

sudo aptitude install wmctrl

```

---

### Post by OmegaPhil on 2011-03-13
As I have taken gfixler's code and extended it for my own purposes, I am releasing these here under a [Creative Commons CC0 license]("http://creativecommons.org/publicdomain/zero/1.0/") in case anyone finds them useful (see attachment).

Its all in the README, but if you are familiar with bash script and the shell in general and willing to adapt some hardcoded stuff associated with my setup, then you might be able to use this.

The scripts implement: Moving windows between two monitors, changing the 'focussed monitor' (i.e. focus the centre window of the other monitor), changing window states (maximised, normalised, minimised etc) with one function for a particular direction, an attempt at tiling/'docking' a window left/right/top/bottom, and focussing a window of a program (including moving to the relevant desktop) with the ability to specify the desktop, a whitelist regex match of the window title, and then a blacklist regex match of those hits to get rid of windows you don't want in the results. If you already had an applicable window in focus, the next applicable window is focussed.

Any quesions, please read the README.

---

