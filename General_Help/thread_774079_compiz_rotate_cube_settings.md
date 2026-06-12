---
title: "compiz rotate cube settings"
date: 2008-04-29
forum: General Help
---

### Post by n00d1ek1ng on 2008-04-29
so i was configuring compiz and somehow my settings for the cube desktop got messed up.

i was wondering how i can initiate the rotating/cube desktop when i click both left and right buttons....

it is currently sent to ctrl+alt+button1

---

### Post by pro003 on 2008-04-29
I think by default to rotate cube is:

ctrl + alt + left click on mouse ...& roll the cube

it should also work : ctrl + alt + left/righ arrow:popcorn:

---

### Post by hermes0710 on 2008-04-29
> **n00d1ek1ng said:**
> so i was configuring compiz and somehow my settings for the cube desktop got messed up.

i was wondering how i can initiate the rotating/cube desktop when i click both left and right buttons....

it is currently sent to ctrl+alt+button1

I don't know if its possible to use more than one combination in order to activate an effect, at least by the "Advanced Desktop Settings ...". If you knew which specific command initiates the rotation effect then you could try binding manually the <ctrl><alt>button2(or 3 i don't remember)through gconf-editor (it's in the nautilus folder)

---

### Post by n00d1ek1ng on 2008-04-29
well the thing is my default used to be just the left and right buttons on my mouse.....so i kno it's possible, but i just don't kno how to reconfigure it...

---

### Post by Hooya on 2008-06-02
I would like to do the same thing the OP is asking.  I want to change the binding that is by default <Control><Alt>Button1 and make it Button1+Button2, but I cannot for the life of me figure out how one would set that combination.  Every syntax I try comes back as not a valid button.  Any suggestions?  I want cube rotation with Mouse Alone, no keyboard left hand being used.

---

### Post by chemtut on 2008-06-03
enable viewport switcher----it works for me---scroll wheel only!!!

---

### Post by Forlong on 2008-06-03
> **n00d1ek1ng said:**
> well the thing is my default used to be just the left and right buttons on my mouse.....so i kno it's possible, but i just don't kno how to reconfigure it...
You can configure that in the **Bindings** tab of the **Rotate Cube** plugin.

---

### Post by Hooya on 2008-06-04
> **Forlong said:**
> You can configure that in the **Bindings** tab of the **Rotate Cube** plugin.

How do you bind two mouse buttons?  Try to do it, let me know exactly what you put in the binding field to get it to work.  I've tried everything I can think of and nothing works.

> **chemtut said:**
> enable viewport switcher----it works for me---scroll wheel only!!!

Only if your mouse is over the desktop background (not over an application) and you can't drag it around like you can with the keyboard bindings.  That's what I want.  I have managed to bind the middle mouse click to drag it around when my mouse is on the desktop, but it still won't work if I have applications covering the desktop.

---

### Post by Forlong on 2008-06-04
> **Hooya said:**
> How do you bind two mouse buttons?
I'm afraid, that's not possible at all.


This thread may be of interest for you: [http://ubuntuforums.org/showthread.php?t=816036](http://ubuntuforums.org/showthread.php?t=816036)

---

### Post by Hooya on 2008-06-04
hmm... the OP said he had his like that before, but you've been around a lot longer, so you probably know what you're talking about.  Pity really.  Not really that big of a deal.

---

### Post by Forlong on 2008-06-05
Hm... now that I think about it... it's kinda possible... not with Compiz, though.

You have to map left+right mouse-click to middle mouse-click in X.
To achieve that, open your xorg.conf as root, e.g.
```
sudo gedit /etc/X11/xorg.conf
```
And add```

	Option		"Emulate3Buttons"	"true"
```
to the **Section "InputDevice"** that has an Identifier like "Configured Mouse"

Then restart X and make sure the **Viewport Switcher** plugin in ccsm is enabled.


Please note, that this will only work, when hovering with the mouse-cursor over the desktop.

---

### Post by Hooya on 2008-06-07
Well, I've already been doing that using the middle mouse button (button 2), but like you said, I have to be over an open patch of desktop.  Better that not having that option, but it could be idealized.

---

