---
title: "Make hidden files appear in folder from terminal?"
date: 2013-10-29
forum: General Help
---

### Post by adec2 on 2013-10-29
Hi is there a command from the terminal that will show hidden files in the folders? I know about CTRL+H and ls from terminal but i would like to know if there is a command that does the same as ctrl+h from the terminal that shows/hides hidden files/folders?

---

### Post by howefield on 2013-10-29
Try

```
ls -a
```

---

### Post by bapoumba on 2013-10-29
Hello :)
ls -a

Edit : Woohoo, ninja'd !

---

### Post by adec2 on 2013-10-29
Nono guys many thanks but what i want is to type a command in the terminal and go to the folder and see it has shown hidden files :)

---

### Post by sudodus on 2013-10-29
You go to folders with the ***cd*** command

for example

```
 cd Desktop  #relative path, works when you are in your home folder
```

```
cd ~/Desktop  # absolute path, works always
```
or
```
 cd /home/$USER/Desktop  # absolute path, works always
```

and then you run ```
ls -a
``` or long output
```
ls -la
```

You can also use path with the ls command, for example

```
ls -la ~
```
to list all files and folders including the hidden ones in your home directory.

---

### Post by adec2 on 2013-10-29
Hi, but i do not want to list the contents in the terminal i just would like to type a command in the terminal so that when i click back on my folder it has done the same as CTRL+H. I just want to add a custom script to thunar so i can right click any folder and select show/hide files/folders

---

### Post by sudodus on 2013-10-29
Well, that is another thing :-)

I think it is hard to make something that is easier than *ctrl+H*. If you don't want to use the keyboard, there is an entry in a pull-down menu to toggle listing hidden files.

---

### Post by stinkeye on 2013-10-29
> **adec2 said:**
> Hi, but i do not want to list the contents in the terminal i just would like to type a command in the terminal so that when i click back on my folder it has done the same as CTRL+H. I just want to add a custom script to thunar so i can right click any folder and select show/hide files/folders
Don't know why you want to but for nautilus.....
```
gsettings set org.gnome.nautilus.preferences show-hidden-files true
```

---

### Post by adec2 on 2013-10-29
i'll have to look into this further. The gsettings command didnt automatically show hidden files either

---

### Post by steeldriver on 2013-10-29
If you are using thunar as mentioned in post #6 then gsettings / dconf won't help you afaik

There is a somewhat parallel settings mechanism called xfconf, it shows a parameter called /last-show-hidden

```

$ xfconf-query -c thunar -l
/last-details-view-column-widths
/last-details-view-zoom-level
/last-icon-view-zoom-level
/last-separator-position
**/last-show-hidden**
/last-view
/misc-single-click
/misc-thumbnail-mode
/tree-icon-emblems
/tree-icon-size

```

If you monitor it while toggling thunar's hidden file visibility (via Ctrl-H or the View->Show Hidden Files checkbox) it appears to be the relevant parameter

```

$ xfconf-query -c thunar -p /last-show-hidden -m
Start monitoring channel "thunar":

set: /last-show-hidden
set: /last-show-hidden
set: /last-show-hidden
set: /last-show-hidden

```

but although setting it seems to be allowed e.g.
```

xfconf-query -c thunar -p /last-show-hidden **-s true**

```
it does not change the active display i.e. it seems to just be a record of the 'last' toggle event as indicated by its name, rather than an actively updateable setting like the dconf/gsettings equivalent.

---

### Post by stinkeye on 2013-10-29
Oh didn't realize you were using thunar.
Happen to have it installed though when trying some alternatives to nautilus.
The gsettings command is only for nautilus and does not update in realtime anyway.

Just had a play with thunar and although maybe not the best way, I can
send the ctl+h shortcut keys with an **xdotool** command (may need to install)....
```
xdotool key ctrl+h
```

Also if your reason for doing this is you mainly use the mouse,
have a look at easystroke mouse gestures.
I use this with wmctrl commands to control windows.
I've attached a short video.

---

### Post by adec2 on 2013-10-30
Stinkeye! Thanks very much I have gone with the xdotool suggestion and added that command to my custom actions! Works great thank you very much!

---

