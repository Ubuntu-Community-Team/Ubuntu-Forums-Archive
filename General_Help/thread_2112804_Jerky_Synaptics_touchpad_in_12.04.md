---
title: "Jerky Synaptics touchpad in 12.04"
date: 2013-02-05
forum: General Help
---

### Post by LochChessMonster on 2013-02-05
Hi All,

**THE PROBLEM:**
I've been running 12.04 for a few months, and have had a problem since my install with my laptop's touchpad. I've just ignored the problem until now, but since I'm spending most of my time on my Ubuntu partition these days, it's a problem I'd like to fix.

When using the touchpad, the mouse is incredibly imprecise: the minimum horizontal distance I can move it is about 1.5 mm (the vertical jump is a bit better, which I think is a product of the larger x-component in the 16:9 resolution), which is an incredibly big jump on my small laptop screen. 

I do not have the same problem with other input, including the built-in Wacom Pen and the trackpoint, which are both capable of moving very small distances. 

The overall mouse experience is pretty bad: I'll often click on the wrong link in a webpage, or launch the wrong application because of this issue. Any thoughts on what to do are very much appreciated!

**WHAT I'VE TRIED:**
- Adjusting different mouse sensitivity and acceleration settings. There has been no change in mouse jumpiness between different settings.
- Using other inputs. The problem seems to only affect the touchpad, which is my preferred mouse input device
- Looked online for similar problems. I found one for a similar problem that I also have at: [http://www.iovene.com/1016/](http://www.iovene.com/1016/) and attempted his solution, without success.

**POSSIBLY RELEVANT MACHINE INFO:**
_Computer_: Lenovo X230 Tablet
_Output for "$ xinput -list"_:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen stylus                   id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Finger touch                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen eraser                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]
```

---

### Post by shutterbc on 2013-02-05
So is it that the resolution is so coarse, or is it hyper sensitive to small movement as well?

---

### Post by LochChessMonster on 2013-02-05
The screen resolution is (1366x768), but the grid that the mouse uses is much smaller, so the 'mouse resolution' is very coarse. As mentioned before, the minimum unit of distance for the mouse to be redrawn on the screen seems to be about 1.5 mm. 

Perhaps the drivers are mapping a much smaller grid of mouse coordinates to the pointer coordinates drawn on the screen?

EDIT:
I did some computations, and found that the minimum movement for redrawing the mouse (1.5 mm) comes out to about 8 pixels in the horizontal direction, and a little bit less vertically.

---

### Post by LochChessMonster on 2013-02-06
I just marked the thread as solved; the problem is specific to the Lenovo ThinkPad X230.

For future users with this problem, attempt the solution at:

[http://www.iovene.com/1016/](http://www.iovene.com/1016/)

and reboot twice (I have no clue why the first one didn't work!).

---

