---
title: "Resolution problem with fiesty fawn"
date: 2007-05-22
forum: General Help
---

### Post by zairulazwan on 2007-05-22
Hi I'm a new here, please help

Im having problem that my monitor/display resolution can't go to its max like windows 1280x1024. I'M using a sony SM-HS75P model and my graphic card ATI Technologies Inc RV280 [Radeon 9200 SE]. How can I rectify this matter
Thank you

---

### Post by JSThePatriot on 2007-05-22
If you already have your ATI graphic card installed properly you can edit the following file as follows.```
// Make a back up of your x11 config file
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

// Open the file for editing.
sudo gedit /etc/X11/xorg.conf

// Scroll down to the Section "Screen". Scroll further
// to the SubSection(s) "Display". Under Modes you should
// have something similar to the following "1024x768" "800x600" "640x480"
// Now you add your own entry here. "1280x1024" This would make your line
// look like: "1280x1024" "1024x768" "800x600" "640x480"

// Save the file, and exit.

// Restart your X11 (easiest just restart the machine).
```

If anything happens oddly you can always use the following to restore your backup file.```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

I hope this helps you along,
JS

---

### Post by JSThePatriot on 2007-05-22
I also noticed someone else wanting to do something similar so I decided I would link you to the more verbose answer given there.

[http://ubuntuforums.org/showthread.php?t=451152](http://ubuntuforums.org/showthread.php?t=451152)

Hope you get this resolved,
JS

---

