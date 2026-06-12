---
title: "Right click New Folder"
date: 2015-08-08
forum: General Help
---

### Post by GrouchyGaijin on 2015-08-08
I know that I can create a new directory from the command line with
```
mkdir
```
Frequently I want to create a directory that uses the date as a name.
I know that I can do this from the terminal by using:
```

now=$(date +"%d-%b-%Y")
mkdir $now

``` 

I am looking for an easier (by easier I mean fewer steps) way to do this.
I see that Ubuntu has the option to right click and choose to create a new folder.


My question is:
Is there a way to edit the default name of a new folder so that right clicking and choosing "New Folder" will create a new directory using the current date as directory the name?

---

### Post by mc4man on 2015-08-08
Don't think so, that option is hard coded in nautilus source.

In a fashion you could use nautilus-actions, however n-a only works when r. clicked _on_ a file/folder. So in this case it'll create in your pwd  (not in the dir you right clicked on if r. clicking on a dir. with your present command set.
It, (command),  could be altered & then it would create in the dir. right clicked on
Or it can be set to create the new dated folder in a specific dir all the time.

So multiple variations are possible or multiple n-a actions

---

### Post by CantankRus on 2015-08-08
When you first create a new folder using right click, the folder name is highlighted, ready to be renamed.

You could use a script using xdotool to paste the date in with a keyboard shortcut.
**_xdodate.sh_**
```
#!/bin/bash

xdotool sleep 1 type --delay 50 $(date +%d-%b-%Y) && xdotool key Return
```
Save and make the script executable.
Set a keyboard shortcut using the path to the script as the command.
May need to install xdotool.

---

### Post by NathanRodriguez on 2015-08-08
Some kind of mkdirnow.sh script won't solve your situation ?

---

### Post by GrouchyGaijin on 2015-08-09
@CantankRus Thanks that is basically what I did.

---

