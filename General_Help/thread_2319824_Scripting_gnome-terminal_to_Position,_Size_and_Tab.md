---
title: "Scripting gnome-terminal to Position, Size and Tab Count"
date: 2016-04-07
forum: General Help
---

### Post by Jason_Hunter on 2016-04-07
I'm trying to make a script for gnome-terminal to open 2 tabs in a 1280x1024 window and center it on screen. 

Anybody have any idea how to do this?

Can this be done using only gnome-terminal or do I have to involve other tools?

---

### Post by sudodus on 2016-04-07
Try according to this method:

1. Open a terminal window and make an image of it with *alt+PrtScrn*. This will tell you the size of the window. For me (in Lubuntu Xenial) the size is 654x469 pixels. The size might be different in another version and desktop environment.

2. Calculate the offset:

xoff=(1280-654)/2=313
yoff=(1024-469)/2=277

3. Run the following command line

```
gnome-terminal --tab-with-profile-internal-id=Standard --tab-with-profile-internal-id=Standard --geometry=+313+277
```

---

### Post by vasa1 on 2016-04-07
Edit: there's also *gnome-terminal > edit > profile preferences > general > use custom default terminal size*. See the attached image.

Re. the geometry, I've noticed that at least some terminals may not use pixels. Instead, the number of characters in a line can be the *width* and the number of rows can be the *height*.

In my (Openbox) rc.xml, I have```
    <keybind key="W-T">        # gnome-terminal
      <action name="Execute"><command>sh -c "wmctrl -xa gnome-terminal.Gnome-terminal || gnome-terminal --geometry=84x41 2&gt;/dev/null"</command></action>
    </keybind>

```in the *keyboard* section. So my gnome-terminal window opens 84 characters wide (first value) and 41 rows high (second value). Note that this requires that I stay with a particular font type and size but that's not a real problem.

The default placement of the terminal window on the screen is specified in the *applications* section of rc.xml. (I can snap any existing window to wherever I wish.)

```
    <application class="Gnome-terminal" name="gnome-terminal">
      <position force="yes">
        <x>-0</x>
        <y>0</y>
      </position>
      <decor>no</decor>
    </application>

```in the application section. Here, I set the screen position of the gnome-terminal window to have its top right-hand corner at the top right-hand corner of the screen.

I don't know what OP's window manager is, but maybe some per-application rules can be set there.

Regarding > Can this be done using only gnome-terminal or do I have to involve other tools? Window size and window placement, AIUI, involves your window manager so I'd suggest getting familiar with it. Two very useful tools you won't regret installing, IMO, are *wmctrl* and *xdotool*.

---

### Post by Jason_Hunter on 2016-04-08
Yup, excellent;). Thanks.

---

### Post by sudodus on 2016-04-08
I'm glad it works for you. :-) Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

