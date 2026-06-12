---
title: "Reconfiugration of stand-by button"
date: 2007-01-09
forum: General Help
---

### Post by Markus72 on 2007-01-09
Hi all,

I would like to reconfigure the keyboard button which initiates the standby (or hibernate) mode to shutdown the machine completely.

How can I configure something like that?

Thanks
Markus

---

### Post by Buck2348 on 2007-01-09
Try this--not guaranteed, but I made something similar work for me.  Open System -> Preferences -> Keyboard Shortcuts.  Select an item for which the shortcut key in the right column reads "disabled."  Click on the word "disabled" and it should change to "New accelerator . . ."  Press the key you want to reconfigure.  The key name should be shown where "New accelerator" was before.  Now you can use gconf editor to set the keybinding.  Applications -> System Tools -> Configuration Editor -> Apps -> Metacity -> global_keybindings.  In the right pane select "run_command_one" if its value is "disabled"--if not select the first run_command whose value is "disabled."  Click on the word "disabled" and it will open up to allow editing.  Change it to the exact name of the key you found in Keyboard Shortcuts.  Now back in the left pane, select "keybinding commands."  In the right pane select "command_one" (or whichever command you set the key for in the previous step).  Click on the empty space under "value" to edit.  Make the command ```
sudo shutdown -P now
```

If the keyname you obtained in the Keyboard Shortcuts applet is of the form "0xf1" that will work in Metacity.  If you could not get a workable name or any name at all for the key try running xev in a terminal.  This will output in the terminal a lot of information about each key you press, and also when you release it.  Somewhere in the middle of about 5 lines of output you will see "keycode xxx" where xxx is a decimal number.  You can convert that to hex and use it as the key name, in the form 0xyy where yy is a 2-digit hexadecimal number.  

If neither the Keyboard Shortcuts applet or xev will "grab" the key you want to configure, the only other way I know is to install keytouch.  It is in the repositories along with a companion package keytouch editor.  Its purpose is to configure all the extra keys on modern keyboards.  Don't use the keytouch editor from the repos--it is old and has no graphic interface.  You can get both of them [here.]("http://keytouch.sourceforge.net/download.php")

Hope this helps.

Buck

---

