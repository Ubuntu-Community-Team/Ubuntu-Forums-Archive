---
title: "system monitor"
date: 2007-01-27
forum: General Help
---

### Post by tacm on 2007-01-27
Is there a set of keystrokes that can bring up this application simular to the ctrl,alt,del in windows?  Thanx

---

### Post by Ramses de Norre on 2007-01-27
You can set one yourself, if you use gnome:```
gconf-editor /apps/metacity
``` there you can assign a keystroke to a command in global_keybindings and then assign an actual command to those keystrokes in keybinding_commands.
You'll probably be able to do this in kde too but I don't know how.

---

### Post by fragos on 2007-01-27
The following bash script will do the job for you.  This is how I did it.

#!/bin/bash
# Ctrl Alt Del will bring up System Monitor

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

---

### Post by tacm on 2007-01-27
thax for the script.....im a noob am i supose to put in all four lines, or just the bottom two?  Thanx

---

### Post by chalex on 2007-01-27
you do need all four lines.

---

### Post by fragos on 2007-01-27
Executable scripts all start with #! and the location of the script processor as in "#!/bin/bash".  Bash scripts are also referred to as shell scripts.  In the simplest sense, anything you can enter on a command line can be placed in a shell script.  Let's say we have a script called "CtrlAltDel".  The script file permissions must be set to execute and you run it on a command line as "./CtrlAltDel".  All executable binaries and scripts must be one of the directories shown when you enter "echo $PATH" on the command line.  Which one is a lesson for another day.  Good luck.

---

### Post by tacm on 2007-01-27
Thanx a lot it worked like a charm

---

