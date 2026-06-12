---
title: "i have a problem with the size of my titlebar text"
date: 2008-03-27
forum: General Help
---

### Post by perfect_circle on 2008-03-27
okay, ive seen threads about this before, and i was told to change the font size in the appearance section.  well i do that when my font is huge, and i can get it to a normal size. then next time i turn my computer on, the font is tiny. here are some pictures. starting with a tiny font.  also the size of font at the log on screen is always huge. any ideas?

goes like this. 
make tiny font normal. from size one to ten.

reboot.  

regular font then becomes huge. 

change font size again. from size ten to one.

---

### Post by pointone on 2008-03-27
Are you running Compiz/Desktop Effects? Try running "gtk-window-decorator --replace" and see if this solves the problem. You can make this solution permanent by adding this command to a simple script that runs on startup.

---

### Post by perfect_circle on 2008-03-27
i tried that and it made the font smaller again....than i changed it to ten again, and now the bar has disapeared....

---

### Post by pointone on 2008-03-27
Set everything back to the defaults, log out, log back in, then try the "gtk-window-decorator --replace" command.

---

### Post by perfect_circle on 2008-03-27
how exactly do i go about setting up as a script to run from startup

---

### Post by pointone on 2008-03-27
Create a script containing the following:

```
#! /bin/bash

sleep 15    # sleeping ensures the desktop has fully loaded first
gtk-window-decorator --replace
```

I always save my personal scripts in ~/bin, but you can save wherever you wish... 

I would personally save this script as ~/bin/titlebar_fix.sh

```
chmod +x ~/bin/titlebar_fix.sh
```

Next, open System > Preferences > Sessions > Add

Name: Whatever you want (Titlebar Fix)
Command: /home/<username>/bin/titlebar_fix.sh (or wherever you've saved the script)
Comment: Whatever you want (Fix the titlebar size!)

Voila! You're done!

---

### Post by perfect_circle on 2008-03-27
just so were clear, a script is a text file right?

---

### Post by pointone on 2008-03-28
Yes, simply create the file in gedit or your favourite editor.

---

### Post by KryoFrk on 2008-05-22
Has anyone done this and can they tell us if it just fixes after you've logged in or does it also fix the login screen? Thanks

---

