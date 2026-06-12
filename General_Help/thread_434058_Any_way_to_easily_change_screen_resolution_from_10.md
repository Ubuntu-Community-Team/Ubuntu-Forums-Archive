---
title: "Any way to easily change screen resolution from 1024 x 768 to 1280 x 1024?"
date: 2007-05-05
forum: General Help
---

### Post by christarp on 2007-05-05
Title say it all really.

---

### Post by RockDoctor on 2007-05-05
You've got two options. #1, which may work, is to look at System->Preferences->Hardware->Screen Resolution. If that location doesn't offer you the option you're looling for, you'll need to edit /etc/X11/xorg.conf (as root) . Here's the magic part of my xorg.conf file:

SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

---

### Post by christarp on 2007-05-05
> **RockDoctor said:**
> You've got two options. #1, which may work, is to look at System->Preferences->Hardware->Screen Resolution. If that location doesn't offer you the option you're looling for, you'll need to edit /etc/X11/xorg.conf (as root) . Here's the magic part of my xorg.conf file:

SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

That's what I was hoping I didn't have to do, is edit the config, since I have only been using this for about 1 day I'm gonna hold off on it.

---

### Post by CocoAUS on 2007-05-05
Easiest way to get your resolution up:
[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution)

All you need to do if you're worried about messing something up is make a backup of your xorg.conf file.  If anything goes wrong, it'll spit you out into a bash prompt, and from there's you'll be able to just replace the messed up file with your backup and log in.

The command to copy a file is cp, so to make a backup of the file, you do
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

To copy the file back over, simply
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

