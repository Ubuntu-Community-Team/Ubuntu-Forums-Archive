---
title: "Flight gear..."
date: 2007-03-10
forum: General Help
---

### Post by cessna_89702 on 2007-03-10
Hey I just installed flightgear from the synaptic and im having trouble finding where the game installed at. Is there a icon i click and it will start. Please help me find it

---

### Post by Famicommie on 2007-03-10
Open up synaptic, find the package that you installed, right click on it, select "properties" and select the tab "installed files".

The game launcher should be located somewhere in /usr/bin

---

### Post by cessna_89702 on 2007-03-11
I right click the package called flight gear and I get some files.
     ```
/.
/usr
/usr/games
/usr/games/est-epsilon
/usr/games/gl-info
/usr/games/yasim
/usr/games/js_demo
/usr/games/fgjs
/usr/games/fgfs
/usr/games/metar
/usr/games/terrasync
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/fgfs.1.gz
/usr/share/man/man1/fgjs.1.gz
/usr/share/man/man1/js_demo.1.gz
/usr/share/man/man1/pstest.1.gz
/usr/share/man/man1/est-epsilon.1.gz
/usr/share/man/man1/gl-info.1.gz
/usr/share/doc
/usr/share/doc/flightgear
/usr/share/doc/flightgear/AUTHORS
/usr/share/doc/flightgear/README
/usr/share/doc/flightgear/README.Debian
/usr/share/doc/flightgear/copyright
/usr/share/doc/flightgear/AptNavFAQ.FlightGear.html
/usr/share/doc/flightgear/FlightGear-FAQ.html
/usr/share/doc/flightgear/Nasal.html
/usr/share/doc/flightgear/README.Cygwin
/usr/share/doc/flightgear/changelog.gz
/usr/share/doc/flightgear/README.IRIX
/usr/share/doc/flightgear/README.JSBSim
/usr/share/doc/flightgear/README.Joystick
/usr/share/doc/flightgear/README.MSVC
/usr/share/doc/flightgear/README.MacOS
/usr/share/doc/flightgear/README.SimGear
/usr/share/doc/flightgear/README.Unix
/usr/share/doc/flightgear/README.Win32-X
/usr/share/doc/flightgear/README.autoconf
/usr/share/doc/flightgear/README.electrical.gz
/usr/share/doc/flightgear/README.gui.gz
/usr/share/doc/flightgear/README.digitalfilters
/usr/share/doc/flightgear/README.properties.gz
/usr/share/doc/flightgear/README.extensions
/usr/share/doc/flightgear/README.fgjs
/usr/share/doc/flightgear/README.introduction
/usr/share/doc/flightgear/README.jsclient
/usr/share/doc/flightgear/README.logging
/usr/share/doc/flightgear/README.mingw
/usr/share/doc/flightgear/README.running.gz
/usr/share/doc/flightgear/README.plib
/usr/share/doc/flightgear/README.submodels.gz
/usr/share/doc/flightgear/README.protocol
/usr/share/doc/flightgear/README.uiuc.gz
/usr/share/doc/flightgear/README.sound
/usr/share/doc/flightgear/README.src
/usr/share/doc/flightgear/README.xmlhud.gz
/usr/share/doc/flightgear/README.xmlpanel.gz
/usr/share/doc/flightgear/README.xmlsound.gz
/usr/share/doc/flightgear/README.xmlsyntax.gz
/usr/share/doc/flightgear/changelog.Debian.gz
/usr/share/doc/flightgear/README.TerraSync
/usr/share/doc/flightgear/NEWS.gz
/usr/share/doc/flightgear/Thanks.gz
/usr/share/doc/flightgear/README.IO.gz
/usr/share/doc/flightgear/README.Linux.gz
/usr/share/doc/flightgear/README.commands.gz
/usr/share/doc/flightgear/README.conditions.gz
/usr/share/doc/flightgear/README.multiplayer.gz
/usr/share/menu
/usr/share/menu/flightgear
```

Where would it be? The launch icon.

---

### Post by cessna_89702 on 2007-03-11
ok i run it by using ```
fgfs
``` at the termiinal
i get ```
zach@zach-laptop:~$ fgfs
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
fgfs: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted

```

that back whats wrong

---

### Post by cessna_89702 on 2007-03-11
anyone??

---

### Post by cessna_89702 on 2007-03-12
need help running flight gear.
i run the command fgfs in the terminal and get
```
zach@zach-laptop:~$ fgfs
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
fgfs: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted

```

whats wrong.. the program opens and closes

---

### Post by cessna_89702 on 2007-03-19
I got flight gear from synaptic. I run the command fgfs to run it and teh box to load comes up but in the terminal i get.
```
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
]
```
 

and then this next code comes up when the box closes
```
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
fgfs: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted

```



help???

---

### Post by aysiu on 2007-03-19
Yes. No one knows. That's typically why people don't answer. It's not that we don't care. For more info, read [To all those with zero-reply threads](http://www.ubuntuforums.org/showthread.php?t=82471)

By the way, please don't create multiple threads on the same topic. I've merged your threads together.

Probably your best bet is a Google search on your error. I did one and got these results. Hope they help.
[http://www.mail-archive.com/flightgear-devel@lists.sourceforge.net/msg06189.html](http://www.mail-archive.com/flightgear-devel@lists.sourceforge.net/msg06189.html)
[http://www.mail-archive.com/debian-amd64@lists.debian.org/msg20218.html](http://www.mail-archive.com/debian-amd64@lists.debian.org/msg20218.html)
[http://lists.debian.org/debian-amd64/2006/09/msg00305.html](http://lists.debian.org/debian-amd64/2006/09/msg00305.html)

---

### Post by sruckh on 2007-04-06
Here is a somewhat related question, although, quite indirectly related.

From the file list in the package we see:
/usr/share/menu/flightgear

If you read the man pages for install-menu and update-menu it looks like those programs should create appropriate menu items for all the window managers configured in:

/etc/menu-methods

Why is it that the menu item is not created as the original posted suggested?  Why must the OP have to look at the package contents to find the a binary to execute when it appears like the package contained files for adding a menu item?

---

### Post by Dan_472 on 2007-04-09
Hi cessna_89702,

I don't know all that much, but I can tell you my experience:

I run flightgear by "taking the terminal" to the directory /usr/bin ,   then typing 'fgfs'

About the "rendering", I had a similar problem until I installed the right graphics driver.   Are you able to play any other games that use high-quality 3D graphics?

---

