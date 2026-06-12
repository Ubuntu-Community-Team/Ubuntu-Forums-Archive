---
title: "Games on Xubuntu"
date: 2007-11-10
forum: General Help
---

### Post by R_T_H on 2007-11-10
(I didn't post this in games because I believe that area is about more serious gaming).

The games that came packaged with the Gutsy Gibbon Xubuntu that I recently downloaded don't always work. For example, the "five in a row" allows me to make a move, then the the computer makes a move and the window closes. Can anyone suggest why, and suggest a solution? 

Thank you for your time

Reuben

EDIT: Sorry for the poor spelling and grammar earlier. I wasn't really thinking...

---

### Post by R_T_H on 2007-11-11
Bump?

Please?

---

### Post by skymera on 2007-11-11
alien arena :)
americas army
doom3 - not free

lots of other junk ones too

---

### Post by R_T_H on 2007-11-11
I was wondering why the games I already had packaged didn't work...

Thanks for your time though

---

### Post by mali2297 on 2007-11-11
I guess that you are referring to gnome-games which are also included in regular ubuntu. The games in the package:
> 
 * aisleriot - different solitaire card games
 * blackjack - the casino card game
 * glchess - 2D/3D chess game
 * glines - color lines game, aka fiveormore
 * gnect - four in a row game
 * gnibbles - snake game, up to four players
 * gnobots2 - improved old BSD robots game
 * gnome-sudoku -  sudoku game
 * gnometris - Tetris, the popular Russian game
 * gnomine - popular minesweeper puzzle game
 * gnotravex - puzzle where you match tile edges together
 * gtali - sort of poker with dice and less money
 * iagno - the popular Othello game
 * mahjongg - classic Eastern tile game
 * same-gnome - remove as many balls in as few moves as possible

Choose one of those that crash and start it from the terminal. For example,
```

gnect

```
Then see if you get any error message in the terminal when the game crashes.

---

### Post by R_T_H on 2007-11-11
Will do. Thanks.

Reuben

---

### Post by R_T_H on 2007-11-11
I did do, and this was the result

(Transcript from terminal):

reuben@Laptop01:~$ gnect
(gnect:5280): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed
 (gnect:5280): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
 (gnect:5280): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed
 (gnect:5280): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
 Segmentation fault (core dumped)
 reuben@Laptop01:~$ 

Any ideas?

Thanks for your time,
Reuben

---

### Post by atlfalcons866 on 2007-11-11
do you have direct rendering enabled?

---

### Post by mali2297 on 2007-11-12
> **R_T_H said:**
> I did do, and this was the result

(Transcript from terminal):

reuben@Laptop01:~$ gnect
(gnect:5280): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed
 (gnect:5280): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
 (gnect:5280): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed
 (gnect:5280): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
 Segmentation fault (core dumped)
 reuben@Laptop01:~$ 

Any ideas?

Thanks for your time,
Reuben

I don't really know what is causing this, but you could try to disable composite.

* Open a terminal. 
* Make a backup of the file /etc/X11/xorg.conf :
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
* Open the file in mousepad:
```

gksudo mousepad /etc/X11/xorg.conf

```
* Add the following lines at the end of the file:
```

Section "Extensions"
        Option "Composite" "Disable"
EndSection

``` 
* Save and quit mousepad.
* Restart X with the keys CTRL+ALT+BACKSPACE (or reboot).
* Test again to run **gnect**.

If it still crashes, replace /etc/X11/xorg.conf with the backup:
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

---

### Post by mali2297 on 2007-11-12
> **atlfalcons866 said:**
> do you have direct rendering enabled?

To find out, run 
```

glxinfo | grep rendering

```
in the terminal.

---

### Post by R_T_H on 2007-11-14
Thanks. I'll try that  now. I didn't really want to ask for fear of appearing too forthright.

Reuben

EDIT: I haven't tried turning rendering off yet, but something has resulted in my graphics card being undetected (it now runs in 640x480).

I backed up the xorg.conf as directed, and changed it as said. Upon restarting it said the it could not detect the graphics card, and ran in safe graphics mode. I tried replacing the xorg.conf (with the backup) but it said it did not exist. Therefore, I followed the earlier gksudo mousepad etc., and removed the code that I had added. I restarted, but again it could not detect my graphics card. Any suggestions?

Reuben.

---

### Post by mike555 on 2007-11-14
What card do you have ATI? anyway you should install "Envy" and then let it install the proper drivers for your graphic card ....... of course if you can't get a GUI you will need to do that using the command line ......

---

### Post by R_T_H on 2007-11-14
I can get a GUI, it just looks awful. I think it's an integrated card, being an older laptop.

---

### Post by mali2297 on 2007-11-14
> **R_T_H said:**
> Thanks. I'll try that  now. I didn't really want to ask for fear of appearing too forthright.

Reuben

EDIT: I haven't tried turning rendering off yet, but something has resulted in my graphics card being undetected (it now runs in 640x480).

I backed up the xorg.conf as directed, and changed it as said. Upon restarting it said the it could not detect the graphics card, and ran in safe graphics mode. I tried replacing the xorg.conf (with the backup) but it said it did not exist. Therefore, I followed the earlier gksudo mousepad etc., and removed the code that I had added. I restarted, but again it could not detect my graphics card. Any suggestions?

Reuben.

You can try reconfiguring xorg.conf with
```

sudo dpkg-reconfigure xserver-xorg

```
This starts an application in the terminal which will ask you (among other things) which drivers you want to use.

You can also check the restricted driver manager (in the menus).

---

### Post by mali2297 on 2007-11-14
> **R_T_H said:**
> I can get a GUI, it just looks awful. I think it's an integrated card, being an older laptop.

You should be able to find out which card you have with:
```

lspci -v | grep -A5 VGA

```

---

### Post by R_T_H on 2007-11-14
The sudo dpkg-reconfigure xserver-xorg seems not to work for me. I get the application, but I know not how to actually use it. The text comes up, and tells me what the program is, but I can't actually get to use it. I have no files on Xubuntu (it's just been a recent experiment), so I think I'll just uninstall it and start again. Thanks for your time and effort.

Reuben

---

### Post by merike on 2007-12-30
I have the exact same problem using gnome-games with KDE. I get the same errors when running from konsole. Disabling composite did not work. And I have direct rendering enabled. Any other suggestions?

---

### Post by tontikki on 2008-03-08
Same here on xubuntu. I suppose the gnome games not really designed to work with xfce,

---

### Post by mali2297 on 2008-03-08
As an alternative, I can recommend [Simon Tatham's Portable Puzzle Collection]("http://www.chiark.greenend.org.uk/~sgtatham/puzzles/"). It is available in the *universe* repository as **sgt-puzzles**.

---

### Post by empthollow on 2008-04-27
Good News!, just solved your problem. run the following command and all gnome-games should run without problems.
```
sudo apt-get -y isntall gstreamer0.10-plugins-base
```
for some reason it isn't listed in the dependancies but it is also not part of xfce so it needs to be installed manually. Hope that solves your problem, i was getting the same error messages.

---

### Post by R_T_H on 2008-04-27
Wow! I stumbled across my own old thread whilst looking up chess. I'm using VEctor Linux now, but I still come back here. Anyone suggest any chess engines with variable difficulty suitable for beginners? :)

---

