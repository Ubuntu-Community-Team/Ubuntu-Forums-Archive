---
title: "wmctrl output"
date: 2013-10-21
forum: General Help
---

### Post by vasa1 on 2013-10-21
When I run **wmctrl**, I see that the application's name isn't mentioned for **some** applications:
```
[08:27 AM] ~ $ wmctrl -l
0x01400020 -1 vasa1-Inspiron-1545 panel
0x01000003 -1 vasa1-Inspiron-1545 Desktop
0x02200023  0 vasa1-Inspiron-1545 geany-my-conf.txt - /home/vasa1/Desktop - Geany
0x024000a1  0 vasa1-Inspiron-1545 Search Results - Ubuntu Forums - Mozilla Firefox
0x02000006  0 vasa1-Inspiron-1545 Classical - File Manager
0x02600004  0 vasa1-Inspiron-1545 LXTerminal
0x02800003  0 vasa1-Inspiron-1545 MegaBookmarks.txt
[08:27 AM] ~ $ 

```

I've seen this is on Lubuntu 13.04 and now  in 13.10, just in case the specific distro has anything to do with it. The missing application name is **Leafpad** and relates to the last entry.

As mentioned [elsewhere]("http://ubuntuforums.org/showthread.php?t=2180156&p=12814871#post12814871"):> both **wmctrl** and **xwininfo** don't mention Leafpad when a window of Leafpad is open! **xprop** does so and so does **xlsclients**. 

---

### Post by Toz on 2013-10-22
From "man wmctrl":
```
       -l     List the windows being managed by the window manager.  One  line
              is  output  for  each window, with the line broken up into space
              separated columns.  The first column always contains the  window
              identity  as a hexadecimal integer, and the second column always
              contains the desktop number (a -1 is used to identify  a  sticky
              window). If the -p option is specified the next column will con&#8208;
              tain the PID for the window as a  decimal  integer.  If  the  -G
              option  is  specified  then  four  integer  columns will follow:
              x-offset, y-offset, width and height.  The  next  column  always
              contains the client machine name. [COLOR="#FF0000"][B]The remainder of the line con&#8208;
              tains the window title[/B][/COLOR] (possibly with  multiple  spaces  in  the
              title).

```
I notice the same with putty, but it allows me to set a window title in its config. Unfortunately, leafpad does not offer a similar config option. 

Or...
```
wmctrl -lx
```
...will display the WM_CLASS instance in the listing to identify leafpad windows, and/or:
```
wmctrl -ir 0x00c00003 -N Leafpad
```
...where 0x00c00003 is the window hexidecimal identifier will allow me to change the window title.

Maybe file a bug report with leafpad to ask for window title configuration options?

---

### Post by Vaphell on 2013-10-22
if you want to know which window is owned by a given program, correlate wmctrl info with pgrep


```
$ prog=firefox
$ wmctrl -lp | grep -f <( pgrep "$prog" )
0x03e000ba  0 1900   void wmctrl output - Mozilla Firefox
```

---

### Post by vasa1 on 2013-10-22
I should have explained what I want to do ...

I've set up various simple short cuts in Openbox (Lubuntu's window manager): W+f opens Firefox, W+l opens leafpad, W+y opens geany, W+t opens lxterminal and so on.

My needs are such that I rarely, if ever, need to have separate instances of the same program. So, if I press W+f, I'd like to bring the existing Firefox window into focus (or start Firefox if it isn't running). I could use the tab switcher (Alt-tab) but that could take more keypresses depending on how many different applications are open.

[stinkeye's solution]("http://ubuntuforums.org/showthread.php?t=2180156&p=12814007#post12814007") does that for me:```
sh -c "wmctrl -a <str> || <start command>"
``` which I modified to a small script, fx.sh:```
#!/usr/bin/env bash

wmctrl -a Firefox || firefox

``` and then assigned W+f to that in lubuntu-rc.xml:```
    <!-- Launch Firefox -->
    <keybind key="W-f">
      <action name="Execute">
        <command>fx.sh</command>
      </action>
    </keybind>

```

Now, thanks to Toz, I just need to use **wmctrl -xa** instead of **wmctrl -a** and that will catch cases such as leafpad.

---

