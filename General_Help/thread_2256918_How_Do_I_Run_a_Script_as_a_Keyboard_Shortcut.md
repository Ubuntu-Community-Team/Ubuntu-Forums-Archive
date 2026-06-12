---
title: "How Do I Run a Script as a Keyboard Shortcut?"
date: 2014-12-15
forum: General Help
---

### Post by Blasman on 2014-12-15
I am trying to run a script as a keyboard shortcut in Xubuntu 14.04.  It does not appear to be working.

The script is as follows:
```
#!/bin/bash
echo $1 | sudo tee /sys/class/backlight/acer-wmi/brightness

```

I made sure that it is executable with the "chmod +x" command.  I can successfully run "brightness 0" and "brightness 9" in a terminal window to change my laptops brightness.  I put the script in a directory that is in my $PATH.  I added the same "brightness 0" and "brightness 9" commands to keyboard shortcuts in the keyboard manager.  However, nothing appears to happen when I press the keyboard shortcuts.  I tried adding "bash" before the command as suggested in another thread that I found on here, but that did not work either.

Any ideas how I can get this working?  Thanks.

---

### Post by tgalati4 on 2014-12-15
Why don't you loosen the permission on brightness and drop sudo from your script.

```
sudo chmod 777 /sys/class/backlight/acer-wmi/brightness
```

Do the built-in brightness keys not work?  On my Acer laptop, the brightness keys are Fn+Left Arrow or Right Arrow.

---

### Post by Blasman on 2014-12-15
Thanks but that didn't appear to help, the keyboard shortcuts still do not work.

The built in brightness keys do work.  However, I am trying to bind a key that will lower the brightness to it's lowest setting and another key that will raise the brightness to it's max setting.

---

