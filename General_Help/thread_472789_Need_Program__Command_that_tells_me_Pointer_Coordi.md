---
title: "Need Program / Command that tells me Pointer Coordinates"
date: 2007-06-13
forum: General Help
---

### Post by mig5 on 2007-06-13
**I HAVE SOLVED MY PROBLEM, LOOK AT THE LAST POST TO FIND OUT HOW**

Hi,
I've looked all over for a program or command that tells me the coordinates of my mouse pointer's current location.  Basically, I need a program / command that can tell me the x and y coordinates of the mouse pointer the moment I run the program /  command.  I need it to tell me the coordinates in relation the the height and width of my whole desktop, not just in relation a certain window (ie: if my desktop is 832x624 resolution I want the coordinates to be from 0-832 on the axis and from 0-624 on the y axis).
I have found other applications that can do this as part of other functions, like screen recorders, but with those you have to draw a rectangle and I just want to know the coordinates of a specific pixel.
I don't mind whether it's just a command, a program or a special mouse cursor that displays the coordinates underneath, I just want something thats easier than using screen recorders all the time just to get some coordinates.

PS: I found some info about a gnome panel applet that tells you the coordinates of your cursor at the following link: [http://webpages.charter.net/decibelshelp/LinuxHelp6.html#utilities](http://webpages.charter.net/decibelshelp/LinuxHelp6.html#utilities)
However I can't find anywhere to download it (yes, I know it's old, BUT I WANT IT =P).

**I HAVE SOLVED MY PROBLEM, LOOK AT THE LAST POST TO FIND OUT HOW**

---

### Post by mig5 on 2007-06-13
OK I've managed to get that coordinate panel applet installed (I found an rpm file and used alien and it seemed to installed OK).  However, it is a gnome 1 panel applet and xfapplet (I'm using Xubuntu) doesn't seem to recongize it.  Xfapplet is a like a compatibility layer in the XFCE panel that lets you use gnome applets, but its not detecting the gnome 1 applet that I want.  I've found a guide about porting gnome applets from gnome 1 to 2, but I can't make head nor tail of it.
[http://developer.gnome.org/doc/API/2.0/panel-applet/applet-porting.html](http://developer.gnome.org/doc/API/2.0/panel-applet/applet-porting.html)

So if anyone either knows of another coordinate program or can lead me through porting the gnome applet I'd really appreciate it.

---

### Post by mig5 on 2007-06-14
I've found a different solution.  Instead of trying to port a gnome 1 applet, called whereami by the way, (which I don't have a clue how to do) and diving into dependency hell, I've found a program that performs the function that I was looking for under windows.  It's called PMeter ( [http://www.pegtop.de/pmeter/](http://www.pegtop.de/pmeter/) ).  It works perfectly in wine.  I just had to change it's settings so that it didn't load its giant rulers all the time, then I added it's coordinates box to my panel using swallower (which was being emulated in xfapplet).  After that I added the program to my start-up (command: wine /home/[me]/wine/.../PMeter.exe) so i runs at each startup.  Now every time I log it flashes on the screen for a couple of secs (I'm fine with that) and then goes down into my panel where I want it.
Even with 3 compatibility layers, wine (windows-linux), xfapplet (gnome-xfce) and swallower (program-applet), the coordinates change in real time and there is no 'lag' as I would have expected.
This just goes to show that you can do anything if you put your mind to it, even if no-one helps you, the linux version of a program doesn't exist anymore and you don't have a standard gnome panel.  Below is a screenshot of how my desktop looks with the coordinates in my panel.

[IMG]http://i9.tinypic.com/4vgve2w.png[/IMG]

---

