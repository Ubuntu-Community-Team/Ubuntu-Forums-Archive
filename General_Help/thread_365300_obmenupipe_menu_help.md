---
title: "obmenu/pipe menu help"
date: 2007-02-19
forum: General Help
---

### Post by moore.bryan on 2007-02-19
*i'm trying to have the files on my usb flash drive show-up in the openbox menu with a pipe, but i can't seem to figure out how to do it.  any takers?*

---

### Post by moore.bryan on 2007-02-20
*nobody?*

---

### Post by fuscia on 2007-02-21
i don't understand what pipe menues are, but couldn't you just make an entry that has a command something like *file-manager /path/to/usbflashdrive*?

---

### Post by K.Mandla on 2007-02-22
I've been messing with something similar and can't figure out how it works either.

I just want to pipe the names of files in a specific directory back into the menu, to change the wallpaper with feh. This is as far as I got.

```
#!/bin/sh

WPPATH="$HOME/environment/*"

echo "<openbox_pipe_menu>" 

for wallpaper in $WPPATH; do
	echo "<item label=\"$wallpaper\">" 
	echo "    <action=\"Execute\">" 
	echo "        <execute>" 
	echo "            feh --bg-scale $wallpaper" 
	echo "        </execute>" 
	echo "    </action>" 
	echo "</item>" 
done

echo "</openbox_pipe_menu>" 
```
I know the script is working because if I redirect the output into an xml file, I get a perfectly formed menu of what's in that directory.

But when I add this to my menu.xml file, but it doesn't seem to do anything.

```
<menu execute="/home/kmandla/.config/openbox/wallpapers.sh" id="pipe-10190" label="Change wallpaper"/>
```
All I get is a tiny, optionless spud of a menu box. Very confusing. 

I've been scouring the Web for some sort of tutorial or howto, but information seems exceedingly sparse. Added to that problem is the fact that most pipe menu scripts seem to be written in perl or python, and I don't know enough about those languages to know exactly what's happening, or what they output.

:confused:

---

### Post by K.Mandla on 2007-02-23
Okay, I had some success, but unfortunately, not through my own efforts. Instead, I found [this thread]("http://forums.gentoo.org/viewtopic-t-114447-highlight-.html") on the Gentoo forums that has a sample in the first post that I was able to modify and make work like I wanted. Best I can guess, my item labels were invalid in the script I wrote. If this one works for you ... cool!

---

### Post by moore.bryan on 2007-02-24
> **K.Mandla said:**
> Okay, I had some success, but unfortunately, not through my own efforts. Instead, I found [this thread]("http://forums.gentoo.org/viewtopic-t-114447-highlight-.html") on the Gentoo forums that has a sample in the first post that I was able to modify and make work like I wanted. Best I can guess, my item labels were invalid in the script I wrote. If this one works for you ... cool!
*which one did you use, the first or later one?  *

---

### Post by moore.bryan on 2007-02-24
[I]k.mandla... 
i've almost been able to get it to do what i want using the first script on your link.  the problem now is the folders on the flash drive that need to have their own pipemenus specified in the script... any ideas?
[/I]

---

### Post by K.Mandla on 2007-02-25
If you mean subdirectories ... well, I haven't made that work either. That script also doesn't do very well with really large directories. 

I know there's a built-in obm-dir command that alphabetizes subdirectories and can handle large lists. You might try that; I couldn't make much use of it because I needed something that could accept arguments (flags, like "dkpg --purge" or something). So long as you don't want those, it'll work.

---

### Post by moore.bryan on 2007-02-25
*obm-dir looked promising, but i can't seem to get the syntax right.  on the openbox faq it says ```
obm-dir <directory> <command>
``` what it doesn't tell me are the commands.  i also saw the obm-nav command... have you looked into that?*

---

### Post by moore.bryan on 2007-02-25
[I]when i try ```
obm-dir "/path/to/dir/" display
```
i get ```
Traceback (most recent call last):
  File "/usr/bin/obm-dir", line 75, in ?
    for m in vmenu:
TypeError: iteration over non-sequence
```
any ideas?
 [/I]

---

### Post by K.Mandla on 2007-02-26
I get a lot of those errors too. I eventually dropped obm-dir because it didn't behave at all, and I chased after the script I listed above. I did look up the source code for obmenu, but I didn't take the time to try and fix it. I don't have enough in the way of python skillz to take the time and figure out what was wrong with it.

obm-nav, on the other hand, seems to do what I want, but isn't very useful beyond that.

---

### Post by moore.bryan on 2007-02-26
*is there a known bug, then?  i think, using the script, i could manually set-up each dir and subdir, but now i've a new problem... it'll tree the dir for me, but it won't let me open any of the files... i guess that's a whole different story...*

---

### Post by K.Mandla on 2007-02-26
I don't know if it's a bug or just a quirk of the way you and I are using it. If you take a look at the [obmenu]("http://obmenu.sourceforge.net/") Web site, you can read through the docs or even pick apart the code. 

There's probably a better way to do what we want it to do; I'll keep looking around and see if anything surfaces.

---

### Post by moore.bryan on 2007-02-26
[I]yeah, i was looking around the site, but didn't find it incredibly helpful.  i'll keep you in mind if i find anything...
thanks for your help.
[/I]

---

