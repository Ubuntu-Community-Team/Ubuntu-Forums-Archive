---
title: "where is compiz started on start-up?"
date: 2008-04-25
forum: General Help
---

### Post by scradock on 2008-04-25
I am having a problem getting emerald to "stick" as the window-decorator in compiz. It sometimes switches in, sometimes doesn't. I want to check the actual "call", which should be in a start-up script somewhere.

I don't have compiz in my session start list - it is included automatically in 8.04. Adding it to my session start list (System | Preferences | Sessions) with the -c emerald option doesn't seem to help.

Where is compiz actually started in the labyrinth of start-up scripts? Does anybody know? Is it documented anywhere? The man page for compiz dates from 2006, by the way........

---

### Post by luisromangz on 2008-04-25
I use compiz fusion launching it from fusion-icon (which allows switching between compiz/metacity and remembers what were you using the last time the program was running) and not from the appearance menu (which doesn't allow you choosing emerald or gtk-window-decorator, something that fusion-icon does).

---

### Post by scradock on 2008-04-25
Thanks - I was missing that! I remember there "used to be" a way to switch decoration manager "on the fly", but that vanished while I wasn't using compiz.

I'm still curious as to how I could ensure compiz autostarts with emerald - any ideas?

---

### Post by Zorael on 2008-04-25
I'm not sure it accepts the -c argument anymore.

Two questions.
You do have the Window Decorations plugin enabled, I assume?
When you say 'Emerald doesn't start', are you saying that another window decorator starts? In other words, does Compiz still work, yet it's displaying the normal non-Emerald Gnome theme?


Also, you could enter 'emerald --replace' to be run at startup.

---

### Post by scradock on 2008-04-25
Yes, I have Window Decoration enabled as a plugin. But there is no place to set emerald as the _initial_ decorator; the setting is "if there is no other decorator enabled".

And there is another one, the normal GNOME one - with the unrememberable name like "gnome-decorator-gtk" or something like that. That's what i get, most of the time; occasionally I get emerald. It was most annoying....

I was reluctant to try adding emerald --replace because I didn't want that to happen at the wrong time, not knowing when compiz was being started. What I want is for compiz to start with emerald as its decorator. There must be a way?

---

### Post by Zorael on 2008-04-26
You could create a short script to make sure it's run in sequence.
```
#!/bin/bash
compiz --replace $@ &
emerald --replace &
```
This will run compiz, then run emerald regardless of whether compiz started it or not. Of course, add extra arguments to the compiz line if you want (such as --loose-binding for nvidia cards for the performance gain, or --ignore-desktop-hints if you're running KDE).


There's this way, too.
```
#!/bin/bash

compiz --replace $@ &

while true; do
	if ps -C emerald > /dev/null
	then
		# emerald running, break
		break
	else
		# emerald not running, launch
		emerald --replace &
	fi
done
```
That would spare your system the extra effort of restarting emerald if it's already running.

---

### Post by scradock on 2008-04-26
Thanks, Zorael - those should work, but they both assume I'm starting from a system that isn't initiating compiz already. Mine is (and so are most installs of 8.04).

How can we make sure that the script that initiates compiz does so with emerald, if we don't know which script that is? I've checked the /usr/bin/compiz script itself - it sets use_emerald="yes" correctly, but doesn't use it itself.....

---

### Post by Zorael on 2008-04-26
Disable compiz under Advanced Desktop Settings and set up such a script to start automatically, in Sessions. :>

Else, you might be able to redirect the symbolic link /etc/alternatives/x-window-manager to your script.

Another alternative would be to rename /usr/bin/compiz to something like compiz.launcher, and make your own /usr/bin/compiz (which should look something like that script), only it should call compiz.launcher instead of just compiz (which would create an infinite loop of child processes = bad. killall compiz.)



Oh, and you might want to add '$@' before the ampersand '&' wherever in the script compiz is launched. That will pass arguments supplied to the script to compiz itself.
```
#!/bin/bash

compiz --replace $@ &

...
```
Just realized this, messy and should've mentioned it earlier.

---

### Post by Lithium17 on 2008-04-26
Usually when I wanted it on startup I set it as a new application in the Session Manager, adding in the code:

```
compiz --replace -c emerald
```

Which works, even in hardy. I don't know why yours doesn't.

---

### Post by scradock on 2008-04-26
Well, thank you all for the helpful suggestions. I find that having fusion-icon allows me to set emerald as the decorator reliably, and to change back and forth if I need to. The problem has "gone away", so I shan't be needing new scripts.

I am still curious as to why:

compiz didn't reliably start with emerald enabled;
compiz sometimes did start with emerald enabled;
why no-one seems to know just where compz is called during start-up;
why fusion-icon isn't part of a standard compiz install, since it does give essential control that is not available otherwise.

But as I say, thanks anyway, especially to luisromangz

---

### Post by Zorael on 2008-04-27
> **scradock said:**
> I am still curious as to why:

compiz didn't reliably start with emerald enabled;
compiz sometimes did start with emerald enabled;
why no-one seems to know just where compz is called during start-up;
why fusion-icon isn't part of a standard compiz install, since it does give essential control that is not available otherwise.
We'd need to see the terminal output when you're launching compiz and emerald won't start. Else we can only make (educated) guesses.

Gnome likely has a setting in its gconf files which you could change to disable Compiz from being the default window manager. I think there's a gconf editor installed by default (gconftool-2? I don't use Gnome).

Most don't need fusion-icon unless they're having issues or if they're going to toggle Compiz every now and then. So omitted, either to lower disk space usage or to follow the unix/linux ethos of only having stuff you need installed.

---

### Post by scradock on 2008-04-27
Thanks, Zorael. I obviously haven't been very clear.

I have been getting compiz starting up reliably at log-in; that's not the problem. The only problem was that it would sometimes start with gtk window decorations, sometimes emerald, even though I thought I had set it to use emerald.

Now I have fusion-icon installed I can switch emerald and gtk decorators at will, and having set emerald as the decorator using fusion-icon it stays enabled until I change the setting. 

That tells me there is a setting - SOMEWHERE - that fusion-icon knows about and I don't. I have been asking all along if anyone can tell me where that setting is. I have scoured gconf and all the config files I can imagine that might have some bearing on the matter, without success. So I kept on asking.

Incidentally, now I have fusion-icon installed I can easily switch compiz/metacity as well, but that was not the original question.

Anyway, thanks for the helpful suggestions, and all the good work.

---

