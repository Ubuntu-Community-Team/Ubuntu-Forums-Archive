---
title: "[SOLVED] Running 'sensors' in terminal from script or shortcut?"
date: 2007-11-23
forum: General Help
---

### Post by drs305 on 2007-11-23
What script or panel shortcut will allow me to open a terminal and then automatically run 'sensors' (or any app) within in the resulting window? I know this should be pretty easy but I've tried various iterations of &, &&, piping, etc and just can't figure it out, even after extensive bash searching with google and reading the man page for gnome-terminal. 

What I currently do is open a terminal window of definite proportions ```
gnome-terminal --geometry 80x26+30+42 --notitle  --nomenu
```

and then type in 'sensors' to display a nice little data window. I'm trying to figure out just how to put it all in one command or script so I don't have to manually type in the command 'sensors'.

I don't really want to use multi gnome-terminal unless I have to. I'm also mostly interested in the terminal display and not GUI equivalents at the moment (althouh you can make recommendations if you want). I am already familiar with xsensors and am using lm_sensors.

And I guess while I'm here, when making an alias, is there a way to pause it for input without writing a script?

I know this must be incredibly basic but I'm stumped. Heck, I can't even figure out how to sort the Places names in Nautilus side pane!  ](*,)

Thank you.

---

### Post by chewearn on 2007-11-23
One easy way to script a window/dialog is to use zenity (you can install this via synaptic).

Type this to find out how to make all sorts of window/dialog boxes:
```
zenity --help
```Here is a simple script to help you out on your sensors display:
```
#!/bin/bash

sensors > results
zenity --text-info --filename results --width=800 --height=800
rm results
```Usage example:
Create a text file in you home name showsensor.sh

Copy / paste the code above into the file.  Make the file executable:
```
chmod +x showsensor.sh
```
Then, you can either run the file from command line:
```
./showsensor.sh
```or create a panel shortcut for it.

---

### Post by drs305 on 2007-11-23
AstalaVista,
Works great. I have used zenity to pause scripts to issue warnings  before but hadn't used it as you did. I'll have to read more about zenity to find out what it can do.

Thanks for the reply.

---

