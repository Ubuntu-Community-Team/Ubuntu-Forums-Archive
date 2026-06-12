---
title: "Maintaining mouse/touchpad settings"
date: 2013-10-08
forum: General Help
---

### Post by James Wilde on 2013-10-08
I have recently installed 13-04 64 bit, and find cursor control a little shaky.  It's very difficult to move the cursor to one of the scroll arrows, for example, and have it stay there when one lifts ones finger from the touchpad.  I have found that slowing down the touchpad pointer speed helps a lot,, but each time, on restart, I find that it has reset itself to roughly 50%.  Is there any way to fix this so that it stays where I have put it even through a reboot?

---

### Post by varunendra on 2013-10-10
You may try installing "gpointing-device-settings" which is a GUI tool for extended mouse/touchpad settings -
```
sudo apt-get install gpointing-device-settings
```

It does not create a launcher icon in Unity, so you may have to run it from terminal (or Alt-F2) > "gpointing-device-settings" command.

See if it can set the touchpad to your liking (make a note of the default values before changing them, since it does not have a "Defaults" button). It should be able to save the settings once set. If not, you may have to look into scripting solutions with "xinput" commands.

---

### Post by James Wilde on 2013-10-10
Thanks, Varunendra!  I solved it with dconf-editor.

---

### Post by varunendra on 2013-10-10
Congrats! And thanks for mentioning the alternative. :)

---

