---
title: "don't have the option shift &amp; alt to change lanuagues what i should to do?"
date: 2008-03-17
forum: General Help
---

### Post by Turge on 2008-03-17
don't have the option shift & alt to change lanuagues what i should to do?

i just don't have it in the keyboard option i have alt and shift bt not shift and alt.
what i should to do if i want to have it?
and i was already have it before don't know what happen.

how i can get it back please?

thx.

---

### Post by der_joachim on 2008-03-17
Open /etc/X11/xorg.conf in your favourite text editor, but make sure that you have backed up your /etc/xorg.conf.

Your keyboard section should look somewhat similar to this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
   Option	       "XkbModel" "pc104" # or whatever your keyboard is.
    Option         "XkbLayout" "us(intl),us(dvorak)" # these contain your languages. Mine is US english and US English Dvorak layout
   Option         "XkbOptions" "grp:alt_shift_toggle" # This is the option you're looking for
EndSection

```

Please note that both KDE and gnome have their own applets, which may or may not override your xorg settings. 

Good luck. :)

---

### Post by Turge on 2008-03-18
> **der_joachim said:**
> Open /etc/X11/xorg.conf in your favourite text editor, but make sure that you have backed up your /etc/xorg.conf.

Your keyboard section should look somewhat similar to this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
   Option	       "XkbModel" "pc104" # or whatever your keyboard is.
    Option         "XkbLayout" "us(intl),us(dvorak)" # these contain your languages. Mine is US english and US English Dvorak layout
   Option         "XkbOptions" "grp:alt_shift_toggle" # This is the option you're looking for
EndSection

```

Please note that both KDE and gnome have their own applets, which may or may not override your xorg settings. 

Good luck. :)
ok first i tell u i do it in root only because i cannot save the file in the normal mode.
then i try to delete the other code of  keyboard that was wrote there and put ur code then i log out from root and try to see in keyboard --->keyboard layout if i have the option to switch with left shift and alt and it wasn't there.

so i go back to root again and then i try to put ur code before the other keyboard code and then i log out and log in in normal mode and than i try to go to keyboard--->keyboard layout and it's still wasn't there.

and it's still don't change me the language when i press left shift and alt.

so what should i do?

---

### Post by Turge on 2008-03-18
> **Turge said:**
> ok first i tell u i do it in root only because i cannot save the file in the normal mode.
then i try to delete the other code of  keyboard that was wrote there and put ur code then i log out from root and try to see in keyboard --->keyboard layout if i have the option to switch with left shift and alt and it wasn't there.

so i go back to root again and then i try to put ur code before the other keyboard code and then i log out and log in in normal mode and than i try to go to keyboard--->keyboard layout and it's still wasn't there.

and it's still don't change me the language when i press left shift and alt.

so what should i do?

any one knows?

---

### Post by Turge on 2008-03-19
> **Turge said:**
> any one knows?

no body?

---

### Post by der_joachim on 2008-03-19
Hmmm... Yesterday's reply disappeared. Probably a PEBKAC. :(

Can you change layouts when in the login screen. Also, what do you use, Gnome, KDE or something else?

Can you post the keyboard  section of your xorg.conf file?

---

### Post by Turge on 2008-03-22
> **der_joachim said:**
> Hmmm... Yesterday's reply disappeared. Probably a PEBKAC. :(

Can you change layouts when in the login screen. Also, what do you use, Gnome, KDE or something else?

Can you post the keyboard  section of your xorg.conf file?

i use GHOME and this is the keyboard section of my xorg.conf file:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"# or whatever your keyboard is.
	Option	    "XkbLayout" "us(intl),us(dvorak)"# these contain your languages. Mine is US english and US English Dvorak layout
	Option	    "XkbOptions" "grp:alt_shift_toggle"# This is the option you're looking for
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

---

### Post by Turge on 2008-03-23
any answer?

---

### Post by Turge on 2008-03-24
> **Turge said:**
> any answer?

any answer?

---

### Post by zvacet on 2008-03-24
Right click on top panel>add to panel and scroll down and you will see keyboar inicator(or something similar I don´t know because I don´t use Engish version)>add it to panel an you can change languages by selecting them in **groups**.

---

### Post by zvacet on 2008-03-25
**System>preferences>keyboard>layout settings (or something similar  to that)>Group Shift/Lock behavior**

---

### Post by Icebear on 2008-03-25
in gnome

you can set up what keys to change the keyboard by

System>Preferences>Keyboard

then choose the >layout option tab>Group Shift/Lock behaviour

and choose the key(s) you want to change with

---

### Post by Turge on 2008-03-30
thank you all but i have tell u when i go to 
System>preferences>keyboard>layout setting>Group Shift/Lock behavior

so i do not have the option to change languages buy shift and alt i have a lot of options but not the option to change languages buy shift and alt.
and i do have that before so how do can i get it back?

if the option is not there i have look for that 31 times.
in System>preferences>keyboard>layout setting>Group Shift/Lock behavior

and it's not there.

what i should to do?

---

### Post by housam on 2008-03-30
Right click on the upper panel >> add to panel >> keyboard indicator >> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> scroll the layouts for the other language >> add.>> close

then you can switch between them by clicking the indicator

---

### Post by Turge on 2008-04-04
> **housam said:**
> Right click on the upper panel >> add to panel >> keyboard indicator >> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> scroll the layouts for the other language >> add.>> close

then you can switch between them by clicking the indicator

i know i can do it like that before u tell this to me.
but i want to know how can i do that i will can to change language with shift & alt without clicking the indicator u understand me?

thank you.

---

