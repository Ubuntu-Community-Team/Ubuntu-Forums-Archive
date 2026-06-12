---
title: "Test keyboard layout like during installation"
date: 2014-06-03
forum: General Help
---

### Post by contremaitre on 2014-06-03
Hi,

My keyboard layout is not correct, and I don't know which one is the good one.
So I need to test quite a lot to find the good one. I'd like to be able to select a layout and have a text input to test this layout imediatly, like during the installation process.
How can I do this ?
Thanks.

---

### Post by tgalati4 on 2014-06-04
I believe that keyboard layout chooser is part of *ubiquity* which is written in Python.  There are several commandline tools for checking keymaps:  xev, evtool, etc, but I am not aware of a full keyboard tester. 

I don't know of a way of running ubquity's layout chooser by itself, since it is a guided installation tool and not something you want to play with on a working system.

---

### Post by grahammechanical on 2014-06-04
This link has images showing the installation process. The image under Keyboard Layout is still accurate.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Also, once we have installed we can add keyboard layouts and switch between them. In this way we can identify the layout that best suits our keyboard. We can even access keyboard layout charts to see what keys are mapped to what characters.

What you are asking for is already available.

Regards.

---

### Post by contremaitre on 2014-06-05
evtool is not found, and I don't know how to use xev to do what I want.
grahammechanical : I think you did not understand what I need.
My system is already installed, so I don't have access to the graphic install anymore.
I need to find out the good layout for my keyboard, but in order to test them I need a tool to select a keyboard and have a textarea to test some keys on the fly, exactly like in the graphic install layout selector.

---

### Post by LastDino on 2014-06-05
system settings>keyboard>Layout settings>input sources/add layouts/add (or something similar)

There you can select and change layout types, if you're not sure which is yours, you can try few of them (not easy as typing during installation but you can see graphical representation of different layouts once selected by clicking on icon similar to keyboard, keys on screen will light up as you hit your keyboard keys to show what key is being pressed )

There is also short cut key to shift between layouts if you ever need.

[ATTACH=CONFIG]253742[/ATTACH]


The minor difference between what you see and what I do, if at all, it might be due to I'm using Ubuntu gnome. But your version, whichever it is should have this as well.

---

### Post by tgalati4 on 2014-06-05
That should be *evtest* not *evtool*.  My fault.

---

