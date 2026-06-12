---
title: "[SOLVED] How to change mouse cursor in fluxbox ?"
date: 2008-04-05
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-04-05
The topic says it all :)

---

### Post by -grubby on 2008-04-05
Right out of the Fluxbox startup file :
```

xsetroot -cursor_name right_ptr

``` 
xsetroot finds your desired cursor and sets it :). Just add that line to your startup file(of course editing "-cursor_name"

---

### Post by LinuX-M@n1@k on 2008-04-05
But where should the cursors be ? I want to install one, but I don't know where ?

Edit: I installed it in ~/.icons/ but when I try to start it nothing happens...
```
boris@linux:~$ xsetroot -aero-drop right_ptr
usage: xsetroot [options]
  where options are:
  -display <display>   or   -d <display>
  -fg <color>   or   -foreground <color>
  -bg <color>   or   -background <color>
  -rv   or   -reverse
  -help
  -def   or   -default
  -name <string>
  -cursor <cursor file> <mask file>
  -cursor_name <cursor-font name>
  -solid <color>
  -gray   or   -grey
  -bitmap <filename>
  -mod <x> <y>
boris@linux:~$ 
```
help ?

---

### Post by -grubby on 2008-04-05
It appears you would run : 
```

xsetroot -bitmap -filename

```

---

### Post by LinuX-M@n1@k on 2008-04-05
I cant make it :((((((((((
```
boris@linux:~/stalonetray-0.7.6$ xsetroot -bitmap -Human
xsetroot: can't open file: -Human
boris@linux:~/stalonetray-0.7.6$ xsetroot -bitmap -filename Human
usage: xsetroot [options]
  where options are:
  -display <display>   or   -d <display>
  -fg <color>   or   -foreground <color>
  -bg <color>   or   -background <color>
  -rv   or   -reverse
  -help
  -def   or   -default
  -name <string>
  -cursor <cursor file> <mask file>
  -cursor_name <cursor-font name>
  -solid <color>
  -gray   or   -grey
  -bitmap <filename>
  -mod <x> <y>
boris@linux:~/stalonetray-0.7.6$

``` :confused::confused::confused:

---

### Post by kerry_s on 2008-04-05
sudo apt-get install xcursor-themes

sudo xedit /etc/X11/cursors/core.theme
(when using xedit, click save 2x to save)

comment out the core and put yours
example of mine:

```
[Icon Theme]
#Inherits=core
Inherits=aero-extra-large

```

restart X

---

### Post by -grubby on 2008-04-05
Oh sorry, oops. You run this :
```

xsetroot -bitmap filename 

```
Note that "filename" has no "-"

---

### Post by LinuX-M@n1@k on 2008-04-05
> **nathangrubb said:**
> Oh sorry, oops. You run this :
```

xsetroot -bitmap filename 

```
Note that "filename" has no "-"

```
boris@linux:~$ xsetroot -bitmap aero-drop
xsetroot: can't open file: aero-drop
boris@linux:~$ xsetroot -bitmap Human
xsetroot: can't open file: Human
boris@linux:~$ xsetroot -bitmap WTF !?!?!??!
bash: !?!?: event not found
boris@linux:~$
```
:lolflag:

Edit: @ kerry_s, not working xDD I think my Ubuntu freaked out :D

---

### Post by -grubby on 2008-04-05
I think that "file" is the path to the mouse cursor, including the file extension.

---

### Post by LinuX-M@n1@k on 2008-04-05
> **nathangrubb said:**
> I think that "file" is the path to the mouse cursor, including the file extension.
```

boris@linux:~$ xsetroot -bitmap /usr/share/icons/DMZ-Black/cursor.theme
xsetroot: bad bitmap format file: /usr/share/icons/DMZ-Black/cursor.theme

boris@linux:~$ xsetroot -bitmap /usr/share/icons/DMZ-Black/index.theme 
xsetroot: bad bitmap format file: /usr/share/icons/DMZ-Black/index.theme

boris@linux:~$ xsetroot -bitmap /usr/share/icons/DMZ-Black
xsetroot: bad bitmap format file: /usr/share/icons/DMZ-Black

boris@linux:~$ xsetroot -bitmap /usr/share/icons/DMZ-Black/cursors/left_ptr
xsetroot: bad bitmap format file: /usr/share/icons/DMZ-Black/cursors/left_ptr

boris@linux:~$ xsetroot -bitmap /usr/share/icons/DMZ-Black/cursors/arrow 
xsetroot: bad bitmap format file: /usr/share/icons/DMZ-Black/cursors/arrow

boris@linux:~$ WTF IS GOING ON HERE !?
```

---

### Post by -grubby on 2008-04-05
That's strange..though I've never tried to install or use an alternative icon theme. You might want to try kerry_s' advice

---

### Post by LinuX-M@n1@k on 2008-04-05
I tried, nothing happens... And DMZ-Black is not an alternative cursor. It's one of the default Ubuntu cursors.

---

### Post by kerry_s on 2008-04-05
> 
Edit: @ kerry_s, not working xDD I think my Ubuntu freaked out 


are you putting the exact name of the cursor? you have to put it exactly like it is in ~/.icons, spelling and all.

there's also a gtkrc-2.0 option, but i can't remember the wording.

i put mine in /usr/share/icons, pic->

---

### Post by LinuX-M@n1@k on 2008-04-05
I even moved it to /usr/share/icons and still nothing:
[ATTACH]65044[/ATTACH]
.........

---

### Post by kerry_s on 2008-04-05
> **LinuX-M@n1@k said:**
> I even moved it to /usr/share/icons and still nothing:
[ATTACH]65044[/ATTACH]
.........

did you restart X? ctrl+alt+backspace at the log in

you don't need full path.

---

### Post by LinuX-M@n1@k on 2008-04-05
> **kerry_s said:**
> did you restart X? ctrl+alt+backspace at the log in

you don't need full path.

yes, about 3 times

---

### Post by kerry_s on 2008-04-05
> **LinuX-M@n1@k said:**
> yes, about 3 times

can you try a reboot, i've come across some instances where the cursor was cached and only changed after a reboot.

---

### Post by LinuX-M@n1@k on 2008-04-05
> **kerry_s said:**
> can you try a reboot, i've come across some instances where the cursor was cached and only changed after a reboot.

I already tried. Still no change... Thats freakin' weird o_O
The funny thing is that I used to know how to change it, but I forgot !! And now I can't find that site ...

---

### Post by kerry_s on 2008-04-05
i think you can put->
gtk-cursor-theme-name= "name-of-theme"

in ~/.gtkrc-2.0 and it would change the cursor. :confused:

---

### Post by LinuX-M@n1@k on 2008-04-06
I didn't have that file :) I created it, rebooted and........... no change :D roflcopter

---

### Post by mali2297 on 2008-04-06
Try this approach...

* Make a directory **~/.icons/default**. 
* Create a file **~/.icons/default/index.theme** that contains the lines
```

[Icon Theme]
Inherits=DMZ-Black

```
* Restart X.

---

### Post by LinuX-M@n1@k on 2008-04-06
At last !! Thanks, mali2297 !!

---

