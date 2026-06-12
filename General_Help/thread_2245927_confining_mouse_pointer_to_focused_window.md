---
title: "confining mouse pointer to focused window"
date: 2014-09-27
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-09-27
I'd like to be able to easily confine the mouse pointer (and effects of mouse buttons and the scroll wheel) to the focused window and be able to realease it with a keybinding. There is an old closed thread on this and similar topics here:
[http://ubuntuforums.org/showthread.php?t=1181014](http://ubuntuforums.org/showthread.php?t=1181014)

Pfanne, in post 4
[http://ubuntuforums.org/showthread.php?t=1181014&p=9374287#post9374287](http://ubuntuforums.org/showthread.php?t=1181014&p=9374287#post9374287)
posted a link to script he wrote that does (apparently) just what I want. But the link is dead and he hasn't been around for almost 2 years. Did anybody save a copy of his script by chance?

Or know some other easy way to do this? I'm running plain Openbox under 14.04, so any solution that works for Lubuntu should work for me. I can always study the component tools mentioned in his post and presumably figure out how to write a script with the same function, but stuff like that often turns into a project that takes way longer than I expect and turns into an obcession causing me to consume massive quantities of caffeine and peanutbutter and lose much sleep, so if there is a pre-made solution I'd love it.

---

### Post by pfanne on 2014-09-29
Hi,
after Dreamer Fithp Apprentice wrote me a pm I decided to update the script and use the proper XServer API to create pointerbarriers.
Pointerbarriers are lines that the mousecursor cannot cross. They can be made semipermeable.
This solution consists of a small c program that creates a single pointerbarrier and a bashscript to keep track of the currently focused window and create and destroy barriers as needed.
To be able to run all this your first need to download the c program and the script from [http://pastebin.com/Wq14pNXh](http://pastebin.com/Wq14pNXh) and [http://pastebin.com/2HGzNDHC](http://pastebin.com/2HGzNDHC) and install the packages xdotool and build-essenstial
```
sudo apt-get install xdotool build-essenstial
```
after that you have to compile the c program with the command:
```
gcc pointerbarrier.c $(pkg-config --cflags --libs x11 xfixes) -o pointerbarrier
```
after that just make sure you drop the compiled program and the script into the same folder and run the script from there.
The way the script works is that you just have to run it once and it will keep doing its thing until you either close it or run another instance of the program which will close the old one.
The easiest way to make this work is to just bind the script to a hotkey.

---

