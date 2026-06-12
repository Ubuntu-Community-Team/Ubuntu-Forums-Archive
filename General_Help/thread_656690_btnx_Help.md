---
title: "btnx Help"
date: 2008-01-02
forum: General Help
---

### Post by dethredic on 2008-01-02
I have installed btnx successfully, but after assigning the buttons with events I am getting mixed results.

I have the logitech G5 mouse with two thumb buttons.

I set the xorg.conf to its default for the mouse:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

It worked as a regular 2 button + wheel mouse, with the side scroll not doing anything, and the back button acting as another wheel click, and the forward button acting as another right click. 

The recognition of the buttons went fine, and when it came to assigning the values, that went well as well. 

When I got to testing it:

the back button works with no flaws
the side scroll works with no flaws
[B]the forward button does not work (still stuck on right click)
middle click now does middle click as well as left scroll[/B]

any ideas how I can fix my 2 problems?

---

### Post by dondad on 2008-01-02
I would ask this question in the btnx tutorial thread on the tutorials board. The author keeps track of that thread and should be able to help you.

[http://ubuntuforums.org/showthread.php?t=455656&highlight=btnx](http://ubuntuforums.org/showthread.php?t=455656&highlight=btnx)

---

### Post by dethredic on 2008-01-03
ok, thanks.

---

