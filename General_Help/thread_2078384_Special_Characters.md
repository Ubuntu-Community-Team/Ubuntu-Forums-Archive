---
title: "Special Characters"
date: 2012-10-30
forum: General Help
---

### Post by juliarain on 2012-10-30
I currently use the Character Palette panel applet in Ubuntu 10.04 (old gnome) to insert scientific symbols and Greek letters into documents. I'm thinking about upgrading, possibly to Linux Mint with the Cinnamon desktop. 

Current palette is: &#945;&#946;&#947;&#948;&#949;&#950;&#951;&#952;&#953;&#954;&#955;&#956;&#957;&#958;&#959;&#960;&#961;&#962;&#963;&#964;&#965;&#966;&#967;&#968;&#969;&#8729;&#8652;&#8651;&#916;°

I click the character I want, and then paste it into any document using Ctrl + V. Super easy. 

Is there any way to make this applet work in a different desktop environment?

---

### Post by Vaphell on 2012-10-30
no idea about the applet, but the effect itself is rather easy to achieve (though in example below it might not be as pretty due to generic gui window used).
this script uses zenity for selection window, and xsel to manipulate selection buffer and xdotool to produce fake ctrl+v
```
#!/bin/bash

dict="&#945;&#946;&#947;&#948;&#949;&#950;&#951;&#952;&#953;&#954;&#955;&#956;&#957;&#958;&#959;&#960;&#961;&#962;&#963;&#964;&#965;&#966;&#967;&#968;&#969;&#8729;&#8652;&#8651;&#916;°"

# select char
char=$( zenity --list --column=Character --height=700 < <( echo $dict | sed 's/./&\n/g' ) )
# put char in ctrl+c/ctrl+v buffer
printf "$char" | xsel -bi
# paste char automatically by emulating ctrl+v combination
xdotool key ctrl+v
```

i gave this script a hotkey in keyboard prefs and in works. Invoke the script with hotkey, doubleclick on any char, it appears in text (and still lives in ctrl+v buffer)

---

### Post by drmrgd on 2012-10-30
That is super cool!!!!  I had to install xsel and xdotool to get it to work (simply 'sudo apt-get install xsel xdotool'), but it works completely flawlessly, and gives me a whole bunch of ideas for similar tools.  Another fantastic piece of coding from the master!

---

### Post by Vaphell on 2012-10-30
lmao, surely you jest
since when slapping few tools together is fantastic piece of coding? :D

---

### Post by juliarain on 2012-10-30
Thank you! This is awesome! 

I tested this in my current system (Ubuntu 10.04). I did have trouble getting the keybindings to work correctly. Any time I tried to bind it to <Ctrl>somekey it would launch whenever I hit that key regardless of whether or not Ctrl was pressed. I finally bound it to <Alt>y, and that works. 

-----------------------------------------------------------------
Full instructions in case anyone else is interested: 

1. Save the script as a .sh file. 

2. In terminal: 
sudo apt-get install xsel xdotool
[enter password]
gconf-editor 

3. In Configuration Editor, apps >> metacity >> keybinding_commands. Right click command_1 >> Edit Key. Type out path to where the .sh file is saved. 

4. In global_keybindings (above keybinding_commands), right click run_command_1 >> Edit Key. Replace "disabled" with desired shortcut.

---

### Post by Vaphell on 2012-10-30
i use 10.04 too and i didn't have to use gconf-editor, i created custom hotkey via Preferences > Hotkeys (or whatever its called in EN)
gnome-keybinding-properties in terminal

---

### Post by juliarain on 2012-10-30
> **Vaphell said:**
> i use 10.04 too and i didn't have to use gconf-editor, i created custom hotkey via Preferences > Hotkeys (or whatever its called in EN)
gnome-keybinding-properties in terminal

Preferences > Keyboard Shortcuts. That actually allowed me to use <Ctrl>y without launching it whenever I try to type a plain y. 

Why does that work differently than Configuration Editor?

---

