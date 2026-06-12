---
title: "Modify button to execute shell script"
date: 2008-05-03
forum: General Help
---

### Post by Odd-rationale on 2008-05-03
How would I modify a special button on my laptop to execute a shell script?

Basically, I have a shell script that rotates the display 90 degrees clockwise. And I would like for that script to be executed when I press that button.

I found (through using xev) the pressing the button is exactly the same as doing super+6. I know how to link super+6 to the shell script. But that is not what I want to do.

I would like that pressing the button, no longer does super+6. It executes a shell script instead. (So I could still link super+6 so another shortcut if I wanted.) I would like to modify what this button does at a deeper level

Any help is appreciated!

---

### Post by nhandler on 2008-05-04
If you use compiz (installed by default in Gutsy and Hardy), you can set up the keyboard shortcut relatively easy. Start by installing the CompizConfig Settings Manager (if you haven't already)
```
sudo apt-get install compizconfig-settings-manager
```
Now, go to System->Preferences->Advanced Desktop Effects Settings. Click on "General Options". Now click the "Commands" tab. Maximize the commands and key binding sections by clicking on the arrows. Now, place the path to your shell script (make sure it is executable) in the "Command line 0" box. Under key bindings, click on the "Disabled" button next to "Run command 0". Check the "enabled" box. Press the key on the keyboard that you want to use to run the script, and click "Ok". Now close the CompizConfig Settings Manager, and test it out.

---

### Post by Odd-rationale on 2008-05-05
Thanks. But I don't use compiz...

---

### Post by nhandler on 2008-06-03
You can also create keyboard shortcuts through gconf-editor. These will work even without compiz.

Start by launching gconf-edit (Hit Alt+F2, and type "gconf-editor" in the box). Navigate to apps->metacity->keybinding_commands. Now, double click on "command_1" to edit it. Enter the patch to your script in the box. Now, navigate to apps->metacity->global_keybindings. Double click on "run_command_1" to edit it. Now, enter the keyboard shortcut you want to use to run the command. For example, you can enter "<Control><Alt>I" to run the script when you hit Ctrl+Alt+I.

---

