---
title: "Tablet PC Help (Setting up the pen)"
date: 2008-03-13
forum: General Help
---

### Post by mattimeeleo on 2008-03-13
Hello, I'm new to the Linux OS... My friend got me into it just today. And I really like it!

Ookay... So major problem I have with this OS is that my stylus (pen) functionality is not working at all... nada.

I read through several posts and links to how to get my pen working, but all these linux terms are just confusing me. 

Currently, I have no idea what to do... So it would be really helpful if someone would guide me step by step (like... literally. Tell me where everything is under)

---

### Post by mlazy on 2008-03-17
have you edited your xorg.conf?

Press alt-f2, then type in gnome-terminal and press enter.

This brings up the terminal, in which you should type:

```

sudo gedit /etc/X11/xorg.conf

```

This should bring up a text editor with some configuration of your hardware.

Go to the way bottom, and delete the ```
#
``` signs from the beginning of the lines in front of "stylus", "cursor" and "eraser".

For example, my xorg.conf looks like this on the bottom:

```

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

That did it for me.

---

