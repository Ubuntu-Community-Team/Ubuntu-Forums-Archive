---
title: "how to excute a particular command via a shortcut key"
date: 2014-10-04
forum: General Help
---

### Post by raghav6 on 2014-10-04
I'm trying to switch my monitor via a shortcut key after a lot of research I found these command works just fine
for turning off external/vga monitor and turning on laptop monitor
```
xrandr --output LVDS1 --auto --output VGA1 --off
```
for turning on external/vga monitor and turning off laptop monitor
```
$ xrandr --output LVDS1 --auto --output VGA1 --off
```

now i just want to learn how to make it work via a shortcut key

_**since I'm on Lubuntu**_***,*** there is no UI way to map keys like in Ubuntu so, most probably the solution would be creating some sort of files in in home folder with embedded command hence I'm putting it under all variant 
thanks in advance :)

---

### Post by raghav6 on 2014-10-05
Bump!

---

### Post by vasa1 on 2014-10-05
I have no experience with the specific command you need help with, but keyboard shortcuts in Lubuntu are managed in ~/.config/openbox/lubuntu-rc.xml.

You can edit that file by hand with a plain text editor (which is what I do) and not something like LibreOffice or Abiword (unless you remember to save as plain text!); or use a GUI but I don't know much about that.

Whatever you do, please back up that file first for safety.

Please look at [http://pclosmag.com/html/Issues/201011/page09.html](http://pclosmag.com/html/Issues/201011/page09.html) even though it's old and mentions lxde and not Lubuntu. It's very helpful and explains the various sections of lubuntu-rc.xml.

---

### Post by CantankRus on 2014-10-05
Use a toggle script perhaps.

Save as **monitor-toggle.sh** and make executable. 
```
#!/bin/bash
 # script to toggle between 2 monitors

currentmonitor=$([COLOR="#FF0000"]xrandr -q | awk '/ connected/{print $1}'[/COLOR])
			
if [ "$currentmonitor" == "LVDS1" ] 
	then
		[COLOR="#FF8C00"]**xrandr --output VGA1 --auto --output LVDS1 --off**[/COLOR]
	else
		[COLOR="#FF8C00"]**xrandr --output LVDS1 --auto --output VGA1 --off**[/COLOR]
fi
exit 0
```
[COLOR="#FF0000"]**xrandr -q | awk '/ connected/{print $1}'**[/COLOR] should output **LVDS1** when that monitor is active.
Check the [COLOR="#FF8C00"]**xrandr**[/COLOR] commands work as the 2 commands you gave earlier were the same.

---

### Post by raghav6 on 2014-10-09
yeah right sorry :) you mean I should create that in in home/'my username' or in root ? and what do you mean when you say make it 'executable'?

---

### Post by CantankRus on 2014-10-09
It's a bash script that will toggle between your 2 monitors.
Copy and paste into gedit and save wherever you like in your home directory.
I create a folder named **scripts** and save there, just to keep things organized.
Once the file is saved navigate to it in the file browser and right click on it.
**Properties > Permissions** and tick the execute box. 

Right click on the script again and this time select "Copy". This will copy the path to the clipboard.
You can now test to see if the script works by right clicking in a terminal and "Paste Filenames" and press Enter. 
With the terminal still in focus, hit your keyboard up arrow to bring up the command again and press enter.
Does this toggle between your connected monitors?

If so use the same path to the script as the command in keyboard shortcuts.
In Lubuntu you can use obkey.(see pic)

Obkey edits the file @ **~/.config/openbox/rc.xml**
I had to create this file as a link to my **lubuntu-rc.xml** file.
```
ln -s ~/.config/openbox/lubuntu-rc.xml ~/.config/openbox/rc.xml
```

---

### Post by raghav6 on 2014-10-11
Ok ok, first I made folder called script in the home folder and I was and created that file but, there is no option or execute box in the properties ( there must be a command for that in terminal right? )instead there button which can chose who can execute it 
[ATTACH=CONFIG]257122[/ATTACH]
none the less I double clicked on it and clicked on execute and it successfully switched from VGA1 to LVDS1 
but when I did the same again nothing happened !! to isolate the issue I made two different bash files for each script every time when I ran the script for LVDS1 monitor,monitor got switched without a hitch but whenever I run the script for VGA1 my laptop screen goes black but nothing comes up in my VGA I can see that the monitor is active but nothing on the screen then i changed the second script so that it enables both monitor (auto instead if off) and it worked !!!! but it all most took 3 sec to arrange stuff in the VGA monitor
I've experienced the same thing when I change my monitor preference manually via preference>monitor setting for some strange reason if untick  DVI montor and check VGA monitor and hit apply same thing happens but,when I tick VGA monitor and hit apply once and come back again and THEN un-tick the DVI it works fine(without any time delay) .perhaps VGA needs DVI at the beginning to get stuff off of it or something like that but i'm not sure

how do I install obkey 'sudo apt-get install obkey' wont work and all I can get them from their website is compressed file which I can't install via synaptic key

---

### Post by CantankRus on 2014-10-11
Sorry I use a different file browser.
You can make a script executable with...
```
chmod +x [COLOR="#808080"]/path/to/script[/COLOR]
```

You can download the latest obkey [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://github.com/nsf/obkey/archive/master.zip") ...This is a direct download link to the zip file.
Extract the archive. 
Open a terminal and change directory(cd) to the extracted folder.
eg my extracted folder is in ~/Downloads
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **cd ~/Downloads/obkey-master**
[COLOR="#008000"]glen@Trusty:~/Downloads/obkey-master$[/COLOR] **./obkey ~/.config/openbox/lubuntu-rc.xml**
```
The second command specifies the config for obkey to open so you don't need to create a link like I said earlier.

If you have 2 commands that work for you to switch monitors, try this script bound to a keyboard shortcut.
```
#!/bin/sh

## script to toggle running 2 commands

TOGGLE=$HOME/.toggle

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    [COLOR="#FF0000"]<<Insert your 1st command>>[/COLOR]
else
    rm $TOGGLE
    [COLOR="#FF0000"]<<Insert your 2nd command>>[/COLOR]
fi

exit 0
```
Use [COLOR="#FF0000"]your commands[/COLOR] and make executable.

---

### Post by raghav6 on 2014-10-13
ok I've done that but I've couple more question

1.how to bind a this script file to a key? I don't see any add script option ? it pretty confusing
2.what i'm suppose to to if I want run the obkey again ? is it possible to create a permanent  shortcut or something so that open it when ever I want 

3. even this script still has the same issue I mentioned before 
> but when I did the same again nothing happened !! to isolate the issue I made two different bash files for each script every time when I ran the script for LVDS1 monitor,monitor got switched without a hitch but whenever I run the script for VGA1 my laptop screen goes black but nothing comes up in my VGA I can see that the monitor is active but nothing on the screen then i changed the second script so that it enables both monitor (auto instead if off) and it worked !!!! but it all most took 3 sec to arrange stuff in the VGA monitor

> I've experienced the same thing when I change my monitor preference manually via preference>monitor setting for some strange reason if untick DVI montor and check VGA monitor and hit apply same thing happens but,when I tick VGA monitor and hit apply once and come back again and THEN un-tick the DVI it works fine(without any time delay) .perhaps VGA needs DVI at the beginning to get stuff off of it or something like that but i'm not sure

so to make this work I wan't  a script enable VGA first and wait for a second and then it should turn DVI off which solves the above issue so, perhaps script would be some thing like this ( i don't anything about syntax of this coding so please refine it ) 

```
#!/bin/sh


## script to toggle running 2 commands


TOGGLE=$HOME/.toggle


if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
#first it will enable the both monitor
xrandr --output VGA1 --auto --output LVDS1 --auto

wait; 1000ms
#some script to wait for a second
    
xrandr --output VGA1 --auto --output LVDS1 --off
#then it switch off DVI

else
    rm $TOGGLE
    xrandr --output LVDS1 --auto --output VGA1 --off
fi


exit 0
```

---

### Post by CantankRus on 2014-10-13
Test different commands in the terminal.
Once you have 2 commands that work use them in the script.
eg 
```
xrandr --output VGA1 --auto --output LVDS1 --auto **&&** sleep 1 **&&** xrandr --output **LVDS1 --off**
xrandr --output VGA1 --auto --output LVDS1 --auto **&&** sleep 1 **&&** xrandr --output **VGA1 --off**
```
**&&** waits for the preceding command to complete before moving on to the next command.

To put obkey into the applications menu, create a .desktop file.
Terminal...
```
gedit ~/.local/share/applications/obkey.desktop
```
Copy and paste in the following and save.
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=sh -c "cd [COLOR="#FF0000"]~/Downloads/obkey-master[/COLOR] && ./obkey ~/.config/openbox/lubuntu-rc.xml"
Name=obkey
Icon=keyboard
Categories=GTK;Utility;
Comment=keyboard shortcuts openbox
```
Edit this to reflect the [COLOR="#FF0000"]path to your **obkey-master** folder[/COLOR].
Should now find obkey in the applications menu under accessories.(may need to log out/in)

See attached vid for using obkey.
After you have entered keys in the Key(text) section hit enter.
control=C
alt=A
shift=S
Windows(Super)=W

*****Must hit the save icon at top left when finished*****

---

### Post by raghav6 on 2014-10-14
WOOOHOOO finally it's working !! thank you so very very much I never thought anybody would help me out this far(that video nailed it)!! along the way I learned a lot about scripting and lubuntu 

although this post was originally about to map those scripts to keyboard shortcuts you actually solved my scripting problem as well which I've previously posted [here]("http://ubuntuforums.org/showthread.php?t=2244050") 
so now I'm trying to make switching of VGA to LVDS1 to happen automatically whenever the laptop switches to battery mode as suggested in #6 and #7 in [that]("http://ubuntuforums.org/showthread.php?t=2244050") post any thoughts on that?
(sorry I'm becoming bit greedy about scripting :) )

---

### Post by CantankRus on 2014-10-14
Never had a laptop so don't know about battery/power switches.
Might find something useful in this thread... [http://ubuntuforums.org/showthread.php?t=1907792](http://ubuntuforums.org/showthread.php?t=1907792)

---

