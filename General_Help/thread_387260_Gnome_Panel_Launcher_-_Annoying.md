---
title: "Gnome Panel Launcher - Annoying"
date: 2007-03-18
forum: General Help
---

### Post by josephus on 2007-03-18
I made a script that toggles the visibility of a window, and execute the script by adding a custom application launcher to the gnome panel.  Whenever I execute the script using the panel icon a wireframe box flashes briefly on the screen.  This does not happen if I make a desktop icon that does the same thing, or if I execute the script from the terminal.  Is there any way that I can get rid of this?  Thanks.

---

### Post by 23meg on 2007-03-18
Could you post your script so that I can try? I did the same a while ago and I recall it worked flawlessly.

---

### Post by josephus on 2007-03-18
it's a pretty ugly hack, but i'm pretty new at this.  Basically I'm using wmctrl to move a panel on and off screen.  I store the position of the window in a data file in ~/scripts/data.

```
#!/bin/sh
offscreen=1200
onscreen=$(cat ~/scripts/data)
pos=$(wmctrl -l -G | grep "Xfce Panel")
if [ -n "$pos" ]
then
	pos=${pos#* }
	pos=${pos#* }
	xpos=${pos%% *}
	pos=${pos#* }
	ypos=${pos%%  *}
	xpos=$(expr $xpos + 0)

	if [ $xpos = $offscreen ]
	then
		ypos=$(expr $ypos + 0)
		$(wmctrl -r "Xfce Panel" -e 0,$onscreen,$ypos,-1,-1)
	else
		ypos=$(expr $ypos + 0)
		$(wmctrl -r "Xfce Panel" -e 0,$offscreen,$ypos,-1,-1)
		echo $xpos > ~/scripts/data
	fi
else
	nohup xfce4-panel &
fi
```

---

### Post by josephus on 2007-03-18
I still don't know why it's happening, but found that I could work around the problem by wrapping the bash script around a python created gnome applet.

---

### Post by mcduck on 2007-03-18
Here's how to get rid of those ugly wireframe animations:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global and disable 'enable_animations' to disable them for panel launchers & minimizing/restoring applications.
3. Go to apps/metacity/general and enable 'reduced_resources' to disable them all
4. Finally go to desktop/gnome/interface and enable 'accessibility' to get show window contents while moving windows, as the 'reduced_resources' disables it.

---

### Post by 23meg on 2007-03-18
So you're using both panels together? Why exactly? The script mysteriously didn't work at all for me. Why aren't you using the "hidden" property in wmctrl instead of moving the panel on and off the screen?

[QUOTE=josephus]I still don't know why it's happening, but found that I could work around the problem by wrapping the bash script around a python created gnome applet.[/QUOTE]

By calling the script from within an applet you wrote?

---

### Post by josephus on 2007-03-18
mcduck: thanks for the tip.  solves the problem perfectly.

23meg: originally i was using both panels because i couldn't place the gnome panel where i wanted, but i've since reverted back to just using gnome panel again.  the whole purpose was to create a status bar panel with a bunch of applets which i could hide and unhide, kinda of like a gnome drawer but with more arbitrary placement and more flexibility with window transparency.

i don't use the hide and unhide feature on wmctrl because i can't get it to respond to the requests.  i'm not sure why it's not working for you.  can you move the windows from the command line?

```
wmctrl -r <Window Name> -e 0,xpos,ypos,-1,1
```

---

### Post by josephus on 2007-03-19
there was a minor typo in the last post
```

wmctrl -r <Window Name> -e 0,xpos,ypos,-1,-1
```

If you are using metacity  (i'm using xfwm4) it doesn't seem to work properly because when you request a move to position <x,y> it actually moves it to position <2x,2y> (or at least that's what returned when you query the position).  Either metacity or wmctrl must have a bug somewhere.

---

