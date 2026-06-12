---
title: "Webbrowser Chart Display - X-Axis cut off"
date: 2016-08-26
forum: General Help
---

### Post by kyosaku on 2016-08-26
Hello there,

this problem came up a few weeks ago with some update to Ubuntu 14.04LTS, though I am not sure when exactly.  

It does not occur in the Windows versions of the webbrowsers Firefox and Chrome, so I thought I'd post it under Ubuntuforums.

to replicate the problem, when using firefox or chromium, looking at an interactive chart like : 

[https://finance.yahoo.com/chart/%5EDJI#eyJtdWx0aUNvbG9yTGluZSI6ZmFsc2UsImJvbGxpbmdlclVwcGVyQ29sb3IiOiIjZTIwMDgxIiwiYm9sbGluZ2VyTG93ZXJDb2xvciI6IiM5NTUyZmYiLCJtZmlMaW5lQ29sb3IiOiIjNDVlM2ZmIiwibWFjZERpdmVyZ2VuY2VDb2xvciI6IiNmZjdiMTIiLCJtYWNkTWFjZENvbG9yIjoiIzc4N2Q4MiIsIm1hY2RTaWduYWxDb2xvciI6IiMwMDAwMDAiLCJyc2lMaW5lQ29sb3IiOiIjZmZiNzAwIiwic3RvY2hLTGluZUNvbG9yIjoiI2ZmYjcwMCIsInN0b2NoRExpbmVDb2xvciI6IiM0NWUzZmYiLCJyYW5nZSI6IjF5In0%3D](https://finance.yahoo.com/chart/%5EDJI#eyJtdWx0aUNvbG9yTGluZSI6ZmFsc2UsImJvbGxpbmdlclVwcGVyQ29sb3IiOiIjZTIwMDgxIiwiYm9sbGluZ2VyTG93ZXJDb2xvciI6IiM5NTUyZmYiLCJtZmlMaW5lQ29sb3IiOiIjNDVlM2ZmIiwibWFjZERpdmVyZ2VuY2VDb2xvciI6IiNmZjdiMTIiLCJtYWNkTWFjZENvbG9yIjoiIzc4N2Q4MiIsIm1hY2RTaWduYWxDb2xvciI6IiMwMDAwMDAiLCJyc2lMaW5lQ29sb3IiOiIjZmZiNzAwIiwic3RvY2hLTGluZUNvbG9yIjoiI2ZmYjcwMCIsInN0b2NoRExpbmVDb2xvciI6IiM0NWUzZmYiLCJyYW5nZSI6IjF5In0%3D)

the bottom of the chart is just cut off & one cannot read the values/dates nor is there a way to scroll downto it.
Search engine does not seem to turn up results for this specific kind of problem, so far.

please help :)

---

### Post by dragonfly41 on 2016-08-26
I can view that yahoo chart in full in Ubuntu 14.04 (32bits) on an old laptop.

The only thought I have is that I'm not using Unity and I'm in Gnome Classic Desktop mode  .. 

[http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/](http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/)

Or perhaps you can launch that URL in an iframe to see if your axis is clipped?

---

### Post by kyosaku on 2016-08-26
Hi,

I have tried your suggestion - but unfortunately, neither Gnome Classic Compiz nor Metacity change anything.
How can I launch an URL in an iframe ?

---

### Post by ajgreeny on 2016-08-26
When I view that page I can see all the chart unless I use Ctrl+ to zoom in too much then the bottom of the chart is hidden.  Ctrl- to zoom out reduces the size of the left hand pane but the chart autofills the rest of the space.

Try using Ctrl- to zoom out and you should find all is visible if you zoom out far enough.

---

### Post by kyosaku on 2016-08-26
Hi there and thank you for your suggestion,

unfortunately, Ctrl- does not do the trick.  This is weird: I can see the x-axis for a very short moment when I zoom out, but it then disappears.

I have no clue what is going on here, as it happens in both Chromium and Firefox ?!

---

### Post by ajgreeny on 2016-08-26
Is your screen resolution correct for your monitor?

That is the only other possibility that I can think of at present.

---

### Post by kyosaku on 2016-08-26
Hmmm ... unless there is a way to set this specifically for firefox and chromium,  the screen resolution is 1920x1080 - native for this machine.

---

### Post by kyosaku on 2016-08-29
> **ajgreeny said:**
> Is your screen resolution correct for your monitor?

That is the only other possibility that I can think of at present.

in the meantime ...

VBox Windows + Firefox | Chrome -> chart is normally displayed


does this make sense to anyone ?

---

### Post by ajgreeny on 2016-08-29
> **kyosaku said:**
> in the meantime ...

VBox Windows + Firefox | Chrome -> chart is normally displayed


does this make sense to anyone ?
What screen resolution does your Windows use?

---

### Post by kyosaku on 2016-08-29
The resolution setting is 1280x689 - (Scaled to 150%).

I see the browser window under XP has a vertical scrolling bar showing up, so I can scroll down.  Under Ubuntu this bar is missing.  Obviously the browser thinks my display is bigger in vertical size than it is.  Full window view doesn't help either.

---

### Post by ajgreeny on 2016-08-30
Check if your FF window in Ubuntu is maximised and if not maximise it; it is possible that you have an unmaximised window but it is too large for the screen resolution so the bottom of the whole window is missing; do you use the Add-on toolbar? Go to the View menu, Toolbars and select Add-on bar or just hit **Ctrl /** together and you should see another toolbar at the bottom of the screen; if not your window is too large for your resolution.

---

### Post by kyosaku on 2016-08-31
> **ajgreeny said:**
> Check if your FF window in Ubuntu is maximised and if not maximise it; it is possible that you have an unmaximised window but it is too large for the screen resolution so the bottom of the whole window is missing; do you use the Add-on toolbar? Go to the View menu, Toolbars and select Add-on bar or just hit **Ctrl /** together and you should see another toolbar at the bottom of the screen; if not your window is too large for your resolution.

Unfortunately, there is no add-on bar - only the bookmarks.  Now I also tried resizing the window to custom size and using the scrolling bar that appears to scroll maximally down.  But this problem persists.  Maybe a bug in the Java-Plugin ? Or is it a Java-chart ?

---

### Post by dragonfly41 on 2016-08-31
Since you seem to be willing to put a lot of effort into getting this to work, here is another suggestion ...

You wrote

> 
[COLOR=#000000]*in the meantime ...*[/COLOR]

[COLOR=#000000][I]VBox Windows + Firefox | Chrome -> chart is normally displayed
[/I][/COLOR][COLOR=#000000][I]
You could try installing Ubuntu in VBox (which itself runs in Ubuntu).
Then see if your view in Ubuntu/Vbox session is clipped as it is in parent Ubuntu.

Incidentally my earlier idea about embedding your htpps URL an iframe didn't work out because of cross-domain security.




[/I][/COLOR]

---

### Post by kyosaku on 2016-10-17
Thank you for all of your help & suggestions - 

finally I found a partial solution to the problem:

at least in Chromium the chart displays OK if I set the Foxclocks plugin to deactivate "status display" (this frees space on the bottom of screen).  So it seems this is a problem with Foxclocks extension.

---

