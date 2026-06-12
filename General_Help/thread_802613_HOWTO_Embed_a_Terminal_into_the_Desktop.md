---
title: "HOWTO: Embed a Terminal into the Desktop"
date: 2008-05-21
forum: General Help
---

### Post by ssjlance on 2008-05-21
I've seen a few other guides on how to do this, but I thought I'd post my method for it as I haven't seen it anywhere. This guide assumes you have already installed compizconfig-settings-manager.

	First thing you'll want to do is open gnome-terminal. Go to Edit > Profiles. Make a new profile, and name it transparent. Under the General tab, deselect the box that says &#8220;Show menubar by default.&#8221; Also, if you want to use a custom font, go ahead and do that. Look under the effects tab, and click the box that says &#8220;Transparent background. Slide the bar all the way to none. Finally, go to the Scrolling tab and disable scrolling.
	After you have the profile setup, you'll need to go into Compiz Settings. Select Window Rules, and make sure it's turned on. Copy the following line:

name=gnome-terminal

	Paste the line into the following boxes: Skip taskbar, Skip pager, Below, Sticky, Non movable windows, Non minimizable windows, Non maximizable windows, and Non closable windows. Go to the tab that says "Size Rules," and size it according to your desktop.
	Next, you need to remove the window decorations. To do this, open ccsm and navigate to the Window Decoration plugin. Open it, and at the bottom where it says "Decoration Windows" and "Shadow Windows," replace the text, "any" with this:

!(name=gnome-terminal)

	The only thing left to do is make it start up by default. Simply putting it into the list of startup programs seems to make the desktop act strange, so you'll want to do it through a script. Make an empty file in your home dir and name it &#8220;deskterm.sh,&#8221; or something along those lines. Go into a terminal and use the following command:

sudo chmod +x deskterm.sh

	After you've made the file executable, open it with your favorite text editor and add this line:

sleep 10 && gnome-terminal --window-with-profile=transparent;

	Now, go to System > Preferences > Session, and add a program to your startup. You just need to link to the script you made. Name it whatever you please, it really doesn't matter. And now, if all has gone well, you should have a terminal embedded into your desktop.
	If all has gone well, your desktop should look something like this:
[img]http://img187.imageshack.us/img187/3898/screenshotjc9.png[/img]

If you have any problems/suggestions, please post them. I'm here to help. :guitar:

---

### Post by stldirty on 2008-05-21
ok and if i wanted to remove it what would i do?

---

### Post by ssjlance on 2008-05-21
If you want to remove it, just remove the script from System > Preferences > Sessions and remove the arguments from your compiz settings.

---

### Post by digitalvectorz on 2008-05-22
What if i wanted that to load up as described herein, but i also want to open up the default profile for multiple that i can access from the panel/taskbar?

---

### Post by ssjlance on 2008-05-22
If you're asking what I think you're asking, you just need to open a terminal with the command gnome-terminal. Leave out the --window-with-profile=transparent.

If you want to just leave it on so you can use it at all times, then make sure the box that says "Show menubar by default" is selected.

---

### Post by digitalvectorz on 2008-05-22
then the problem lies in ccsm; cause i open the default and it's resized to fullscreen and not moveable.  hrm...

---

### Post by digitalvectorz on 2008-05-22
Okay. I figured it out.

In the CCSM, everywhere you said to use 

name=gnome-terminal

,use

name=gnome-terminal --window-with-profile=transparent

instead, and that will break ccsm's hold on every instance of the terminal (in case ppl wanted a background terminal and multiple foreground terminals)

---

### Post by digitalvectorz on 2008-05-22
actually scratch that...that didn't work.

But it seems:

name=gnome-terminal & title=transparent & type=normal

works, now it's a matter of aligning the background window under the gnome-panel rather than behind it.

---

### Post by digitalvectorz on 2008-05-22
okay, got it.  

After following the above tutorial using
```

name=gnome-terminal & title=transparent & type=normal

```

instead of only

name=gnome-terminal

the desktop terminal starts under the upper gnome-panel.  To resolve this issue, just open ccsm > Place Windows > Fixed Windows
and add a new entry in "Windows with fixed position"

Positioned windows:
    name=gnome-terminal & title=transparent & type=normal
X,Y Positions:
    0,0

and that should resolve it.

knowing my luck, i'll find another fault in this.  *sigh*

Hope this answers my (and anyone elses possible) questions.

---

### Post by digitalvectorz on 2008-05-22
Sigh. That doesn't work either.

<feels like such a n00b o.O>

---

### Post by garrison742 on 2008-05-22
I am pretty new to all this so here is a easy question. I set the profile to transparent and changed nothing in ccsm, how do I get back my edit and other choices on top bar if I want them?

---

### Post by L14UX_1NS1D3 on 2008-05-22
Hey this Sound like a nice solid way to have a embedded terminal running without much sweat. But say you wanted to embed something else on the desktop like, say a media player. Would this be possible? My eyes would pop out of my head if I could be running amarok as a desktop background. With this you could even have a media player playing video in the background!. Yet would this work?

---

### Post by ssjlance on 2008-05-22
In theory, this would work with any window you would want. The terminal just seems most practical to me. You would just have to make sure to place the window above/below any panels you had to make sure all options were accessible.

[quote=garrison742]I am pretty new to all this so here is a easy question. I set the profile to transparent and changed nothing in ccsm, how do I get back my edit and other choices on top bar if I want them?[/quote]

Did you set the profile to transparent and that loads every time you open it with just the command gnome-terminal? If that's the problem, just type this into the terminal:

gnome-terminal --window-with-profile=Default

And as for being able to open another window, I don't see why you would really need to. If you just need to change a setting really quickly, opening it without the transparent profile should work. If you really need to have an open forground terminal, you could just install Konsole.

And don't feel like a noob. This took me a while to figure out, and there are probably better ways of doing it.

---

### Post by garrison742 on 2008-05-22
thanks. I knew there would be a simple command I just did not how it was worded. More comfy messing things up when I know how to get them back.:lolflag:

---

### Post by victorgreen on 2008-06-15
Thanks so much, everything worked once I restarted X, but its still seeing the terminal in the desktop as an open window, how do I make it a sticky?

---

### Post by ssjlance on 2008-06-15
Could you go into a little more detail on that? What exactly have you done?

---

### Post by suterb42 on 2008-10-22
I found an easy way to get a terminal on your desktop. Install screenlets, then get this screenlet:

[http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844](http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844)

---

