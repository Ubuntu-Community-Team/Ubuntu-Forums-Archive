---
title: "Problem with creating launcher"
date: 2016-12-30
forum: General Help
---

### Post by marsdenf on 2016-12-30
Using Xubuntu 14.04.  I want to create a launcher on my panel to disable xscreensaver and then display a notification for it on the desktop.  If the command " xscreensaver-command -exit " is used in the launcher, it works.  And if " notify-send "Screensaver de-activated" " is put into the launcher by itself, then a notification appears in the top right as desired.  But if I try to chain the commands thus:  "  xscreensaver-command -exit && notify-send "Screensaver de-activated" " then this error msg appears: 


            
                Failed to execute command "screensaver-command -exit && notify-send "Screensaver de-activated"".  Failed to execute child process "screensaver-command" (No such file or directory)




How can the two commands be executed, with the second depending on the success of the first?  TIA

---

### Post by marsdenf on 2016-12-30
Of course the "x" is missing from xscreensaver, but I changed it and it still does not work.  No error message this time, but the saver is not de-activated and no notification appears.

---

### Post by sisco311 on 2016-12-30
You can't use control operators (&&, ||, ...) directly in the command field of the launcher.

Either run the commands in a subshell:
```
sh -c 'screensaver-command -exit && notify-send "Screensaver de-activated"'
```
or create a script for your commands:
```
#!/bin/sh
 
screensaver-command -exit &&\
notify-send "Screensaver de-activated"


```make it executable and invoke it in the launcher.

---

### Post by marsdenf on 2016-12-30
Finally figured out how to do what you suggested.  (I know almost nothing about the command line.)   Thanks for your help.

---

