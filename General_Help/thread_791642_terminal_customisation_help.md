---
title: "terminal customisation help"
date: 2008-05-12
forum: General Help
---

### Post by Smendrick on 2008-05-12
hey there new to all this so go easy on me!!!
basically i have  picture i want as my background on ym terminal which i have setup but i want to set the terminal so it the windows size is automatically set the right size for the background picture

am using hardy

---

### Post by Achtung on 2008-05-12
You can change the launcher properties to include "-geometry=200x100" (or any other value in number of characters) as argument in the startup command line. 

There must be a way to change it through gconf-editor, but I can't recall the option off the top of my head.

---

### Post by Smendrick on 2008-05-12
yeah have found some options in the editor and there is a part about a custom command wondering if that will work?

---

### Post by Smendrick on 2008-05-12
problem slved found this in a previous thread


he gnome-terminal uses a termcap file for its basic settings. To change these:
Code:

sudo gedit /usr/share/vte/termcap/xterm

Now look for a line about 1/3 of the way down the file that looks like this:
Code:

	:co#80:it#8:li#24:\

To change the number of columns, change the co# number, in this case 80.
To change the number of rows, change the li# number, in this case 24.
So as an example if you want a terminal window of 132x25:
Code:

	:co#132:it#8:li#25:\

You must exit all gnome-terminal proceses before the changes take effect.



credit to Kanji_Man

---

### Post by Nythain on 2008-05-12
that explains the funny math when doing geometrys for terminal emulators...
i had always assumed the MxN was pixels and some wonky math, turns out its columns and rows

---

