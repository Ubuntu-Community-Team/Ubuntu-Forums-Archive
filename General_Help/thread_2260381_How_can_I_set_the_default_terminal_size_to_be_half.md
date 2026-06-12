---
title: "How can I set the default terminal size to be half the screen?"
date: 2015-01-11
forum: General Help
---

### Post by TriforceOfKirby on 2015-01-11
So I want the default terminal size to be the same size as if you pressed Ctrl+Super+Left. In my attempt to doing this, I opened a terminal and pressed Ctrl+Super+Left, then I input these commands:
```

[COLOR=#000000][FONT=Consolas]tput cols
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]tput lines
[/FONT][/COLOR]
```
To get the current terminal size, which gave me 72 columns and 39 rows, then I put those values into Edit>Profile Preferences>Use custom default terminal size; however, this didn't quite work, upon opening a new terminal, it was 1 row short of the bottom of the screen and a tiny bit short of the width. So if I set the rows to 40 (or anything higher), there is still an extra space left at the bottom, adding an extra column makes it a bit too wide. I'm not too concerned about the width being exact, but the extra space at the bottom is annoying, is there any way to get the terminal to fill up the entire height?

---

### Post by sudodus on 2015-01-11
You can also try the geometry option and select what works well for you. Try with different values and see what happens!

Examples:

```
gnome-terminal --geometry 80x20+100-50

xterm -geometry 80x20+100-50
```

From ```
man X
```

```
GEOMETRY SPECIFICATIONS
       One of the advantages of using window systems instead of hardwired terminals is that applications don't have to
       be restricted to a particular size or location on the screen.  Although the layout of windows on a  display  is
       controlled  by  the window manager that the user is running (described below), most X programs accept a command
       line argument of the form -geometry WIDTHxHEIGHT+XOFF+YOFF (where WIDTH, HEIGHT, XOFF, and  YOFF  are  numbers)
       for specifying a preferred size and location for this application's main window.

       The  WIDTH  and HEIGHT parts of the geometry specification are usually measured in either pixels or characters,
       depending on the application.  The XOFF and YOFF parts are measured in pixels and are used to specify the  dis&#8208;
       tance of the window from the left or right and top and bottom edges of the screen, respectively.  Both types of
       offsets are measured from the indicated edge of the screen to the corresponding edge of the window.  The X off&#8208;
       set may be specified in the following ways:

       +XOFF   The  left edge of the window is to be placed XOFF pixels in from the left edge of the screen (i.e., the
               X coordinate of the window's origin will be XOFF).  XOFF may be negative, in which  case  the  window's
               left edge will be off the screen.

       -XOFF   The  right  edge  of the window is to be placed XOFF pixels in from the right edge of the screen.  XOFF
               may be negative, in which case the window's right edge will be off the screen.

       The Y offset has similar meanings:

       +YOFF   The top edge of the window is to be YOFF pixels below the top edge of the screen (i.e., the  Y  coordi&#8208;
               nate  of  the window's origin will be YOFF).  YOFF may be negative, in which case the window's top edge
               will be off the screen.

       -YOFF   The bottom edge of the window is to be YOFF pixels above the bottom edge of the screen.   YOFF  may  be
               negative, in which case the window's bottom edge will be off the screen.

       Offsets  must  be given as pairs; in other words, in order to specify either XOFF or YOFF both must be present.
       Windows can be placed in the four corners of the screen using the following specifications:

       +0+0    upper left hand corner.

       -0+0    upper right hand corner.

       -0-0    lower right hand corner.

       +0-0    lower left hand corner.

       In the following examples, a terminal emulator is placed in roughly the center of the screen and a load average
       monitor, mailbox, and clock are placed in the upper right hand corner:

           xterm -fn 6x10 -geometry 80x24+30+200 &
           xclock -geometry 48x48-0+0 &
           xload -geometry 48x48-96+0 &
           xbiff -geometry 48x48-48+0 &

```

---

### Post by TriforceOfKirby on 2015-01-11
So is there a way to always use that option by default when opening a terminal window?

---

### Post by mc4man on 2015-01-11
Assuming gnome terminal
Open a terminal > Edit  > Profile Preferences > enable Use a custom .. & alter the values to suit.

---

### Post by TriforceOfKirby on 2015-01-12
Ok thank you.

---

