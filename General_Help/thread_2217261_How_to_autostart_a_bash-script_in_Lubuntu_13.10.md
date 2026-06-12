---
title: "How to autostart a bash-script in Lubuntu 13.10?"
date: 2014-04-16
forum: General Help
---

### Post by Kai_Konnen on 2014-04-16
I wrote a bash-script named swapkeys.sh. The scripts path is /home/USERNAME/bin/swapkeys.sh. I made it executable and it works fine when started from a terminal or by double-clicking it in the file-manager. 


I tried several ways to autostart the script


1. Startbutton - Preferences - Default applications for LXSession - Autostart: Added [FONT=courier new]/home/USERNAME/bin/swapkeys.sh[/FONT] as a "Manual autostart application". My script doesn't start. Other commands i added at the same place (I tried [FONT=courier new]lxtermina[/FONT]l and[FONT=courier new] synclient MaxTapTime=0[/FONT] (disables the touchpad)) work fine. 


2. I copied the script swapkeys.sh into[FONT=courier new] /usr/bin[/FONT] and tried to start it adding the lines swapkeys and swapkeys.sh in the same dialogue


3. I added a file named swapkeys.desktop at [FONT=courier new]home/USERNAME/.config/autostart[/FONT]. The file contains the following lines
```
[Desktop Entry]
Name=Swapkeys
Exec=/home/USERNAME/bin/swapkeys.sh
Type=Application
Terminal=false

```

None of these methods does work. What's wrong? Any idea what else I can try


Thank you for helping


Kai

---

### Post by Dennis N on 2014-04-16
This is what I did in Lubuntu 13.10 to run a script at log in.  

Add the executable command to the file:

**[FONT=Courier New]~/.config/lxsession/Lubuntu/autostart[/FONT]**

and it will run automatically when you log in.

In your case, since the script is in ~/bin, just add this line into the autostart file:

[B][FONT=Courier New]swapkeys.sh
[/FONT][/B]
and save.

Note: Be sure the script file is executable as well.

---

### Post by Kai_Konnen on 2014-04-16
Thank you for answering. Tried that, it doesn't work. On my system the path is

[B][FONT=Courier New]~/.config/lxsession/[COLOR=#ff0000]L[/COLOR]ubuntu/autostart (capital L in "[COLOR=#ff0000]L[/COLOR]ubuntu")
[/FONT][/B]
Is this of significance? Renaming is possible, but after reboot the system generates a new [COLOR=#ff0000]L[/COLOR]ubuntu directory

---

### Post by Dennis N on 2014-04-16
Yes - it's a typographical error. Lubuntu in the path should be capitalized. I have also corrected the post. To the OS, "lubuntu" is not the same as "Lubuntu" - it is case sensitive.

---

### Post by Kai_Konnen on 2014-04-17
The solution: 

1.  Reinstall Lubuntu 13.10
2. [COLOR=#000000] **Startbutton - Preferences - Default applications for LXSession - Autostart**: Add [/COLOR][COLOR=#000000][FONT=courier new]/home/USERNAME/bin/swapkeys.sh[/FONT][/COLOR][COLOR=#000000] as a "Manual autostart application". 
I tried that before. After reinstalling Lubuntu, it worked.  Apparently I broke something while experimenting with different autostart-types. [/COLOR]

---

