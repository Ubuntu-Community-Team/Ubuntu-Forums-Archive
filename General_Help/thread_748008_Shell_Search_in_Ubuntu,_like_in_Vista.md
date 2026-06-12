---
title: "Shell Search in Ubuntu, like in Vista"
date: 2008-04-07
forum: General Help
---

### Post by buried on 2008-04-07
I really liked the shell search and instant search in Vista (vista was good for me, no errors, it just because my hardware is supported, to all who complains about it, well that's their comps"
And I wonder if there is a feature for Ubuntu thats similar, I know Beagle is good, but I want it to be in the GNOME File manager shell, with instant search.

---

### Post by justleen on 2008-04-07
SInce Gutsy, there is a search panel in Gnome... The looking glass next to the clock (top-right) .. THat what you need?

---

### Post by jakupl on 2008-04-07
yeah. like justleen said. But beware, the search tool is _case sensitive_
That made me sweat at the beginning when I wasn't used to it :)

---

### Post by jakupl on 2008-04-07
btw. Is there any way of making it "not-case-sensitive"? ... maybe in a script
I know, that's the whole way linux works... but in the search area, it's not very practical.

---

### Post by buried on 2008-04-07
no I meant as in the shell (file manager not on the desktop)

---

### Post by wormser on 2008-04-07
I am not familiar with Vista's search option, but it sounds like you want to search within the shell.  There are a couple of commands. First is locate but it needs the database updated before it will work.  The other is the find command.

```
sudo updatedb
```
```
locate whatever
```

```
find / -name whatever
```

The / will search everything.  You can search specific directories by specifying them.  Like find /home/username -name whatever.

---

### Post by buried on 2008-04-07
This is very hard to explain, search **WITHIN** the **CURRENT WINDOW**, (e.g I open up a huge folder full of crap, now I need to search for a certain thing in this folder, so I click the search and type in "example" and a list of files should pop up in the current folder, like in Vista, i'm not implying that I want something "looking" like vista, I just need something that is similar to vista's feature idea.
To make it even clearer here's a screenshot, thanks to everyone who tried to help, much appreciatted :D
[img]http://www.imgsync.com/data/img/7524142vistaserch.jpg[/img]

---

### Post by justleen on 2008-04-07
erm.. there is this binocular icon, called "Search" in nautilus.. ?

---

### Post by buried on 2008-04-07
Is there a mod to place it on the right so I don't have to click File>Search or without me having to max the window

---

### Post by prshah on 2008-04-07
> **buried said:**
> This is very hard to explain, search **WITHIN** the **CURRENT WINDOW**, (e.g I open up a huge folder full of crap, now I need to search for a certain thing in this 


In your huge folder full of crap, just start typing the filename, and the local search text box opens up in the bottom right hand corder of the window, while the screen jumps to the first match.

---

### Post by munkyeetr on 2008-04-07
> **prshah said:**
> In your huge folder full of crap, just start typing the filename, and the local search text box opens up in the bottom right hand corder of the window, while the screen jumps to the first match.
**EDIT: After entering my method below, I see prshah has a way better method, that appears to be exactly what you are looking for. I will still leave mine here though, and humbled, slink from the room...**

I think this will *somewhat* address the functionality you are looking for; **this will add the ability to *right-click* on a directory in nautilus and limit your search to the currently selected directory**. At least, I think that's sort of what you are looking for :) .

1) Install Nautilus Actions:
```

sudo apt-get install nautilus-actions

```

2) **System** -> **Preferences** ->** Nautilus Actions Configuration**
3) **Add** a new action
4) Fill in like so (*or customize as you want, this is how I have mine*):
> 
**Menu Item & Action Tab**

Label: **Search...**
Tooltip: **Search this folder**
Icon: **gtk-find**
Path: **/usr/bin/gnome-search-tool**
Parameters: **--hidden --path=%M**

**Conditions Tab**
Filenames: *****
Mimetypes: ***/***
Appears if selections contains: **Only folders**

5) Done.

**NOTES:**
* You may need to close and reopen Nautilus to have the changes take effect.
** This only works on the right-hand panel of nautilus, not on the tree side, which is a shame :(
*** I hope this is what you are looking for! :)



---

### Post by prshah on 2008-04-07
> **munkyeetr said:**
> **EDIT: After entering my method below, I see prshah has a way better method, that appears to be exactly what you are looking for. I will still leave mine here though, and humbled, slink from the room...**


Ahhh i've finally got to the other side of the fence, after soooo long slinking around myself..

---

### Post by buried on 2008-04-07
thanks munkyeetr, that's what I was looking for,  thanks prshah for trying to help, Greatly Appreciated.

---

### Post by prshah on 2008-04-07
> **buried said:**
> [color=red]thanks munkyeetr, that's what I was looking for[/color],  thanks prshah for trying to help, Greatly Appreciated.

oops leaped too soon...

---

### Post by munkyeetr on 2008-04-07
> **prshah said:**
> oops leaped too soon...
LOL, and I thought *for sure* it was yours!

---

### Post by noynac on 2008-04-07
> **jakupl said:**
> btw. Is there any way of making it "not-case-sensitive"? ... maybe in a script
I know, that's the whole way linux works... but in the search area, it's not very practical.

You can use the find command with -iname rather than -name and the search will not be case sensitive. Using wormser's example, the following search is case sensitive...

```
find / -name whatever
```

The following search is not case sensitive...

```
find / -iname whatever
```

---

