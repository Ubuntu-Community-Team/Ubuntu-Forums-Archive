---
title: "Unity Launcher is Missing ??"
date: 2018-08-16
forum: General Help
---

### Post by tomasu01 on 2018-08-16
I've enabled the Unity Plugin with the CCSM Tool already yet, it still didn't show.
Please help! I'm using Ubuntu 18.04 LTS.
I've done so many solutions online and yet, they haven't worked for me.

It disappeared after I did the following in the terminal (I was supposed to remove the dock):
```
cd /usr/share/gnome-shell/extensions/
sudo mv ubuntu-dock@ubuntu.com{,.bak}
```

---

### Post by deadflowr on 2018-08-16
unity plugin and gnome shell extensions are two exclusively different things.
You need to run unity in order to utilize the unity plugin.
Ubuntu 18.04 does not use unity, it uses gnome shell.
Which is why the dock disappeared after you moved the Ubuntu dock extension.

Currently, where is the Ubuntu dock folder you moved?
You need to move it back to it's original file/folder name.
Or a reinstall of the ubuntu-dock extension should do that too
```
sudo apt install --reinstall gnome-shell-extension-ubuntu-dock
```

---

### Post by monkeybrain20122 on 2018-08-16
18.04 defaults to gnome shell, if you want the unity goodies you will have to install unity session yourself, but that is very easy
```

sudo apt install ubuntu-unity-desktop
```

If you use a touchpad, also 
```
sudo apt install xserver-xorg-input-synaptics
```


During installation choose lightdm as your default

then reboot and log into unity, that's it.

If desired you can remove gnome shell at this point.

---

### Post by tomasu01 on 2018-08-16
Thanks for replying, but I do not know where the Ubuntu folder was moved to, all I do know is that it's moved. I got this step from a Ubuntu tutorial on how to remove the dock. But however, the reinstallation worked. But if I want to install the Unity Launcher again (instead of Dock), how do I do that?

And yes, I'm a half-Windows user and a half Ubuntu user but I have more experience in Windows so it kinda makes sense why my knowledge on Ubuntu is so little.

Update:
Whopps, How could I forget that you once said that Ubuntu uses GNOME not Unity. I'll see what I want to do.

Update 2:
Okay, so now how do I remove the dock so I can get the GNOME launcher back instead? Any answer would be appreciated.

---

### Post by deadflowr on 2018-08-16
Did you follow monkeybrain20122's advice to install unity; (the ubuntu-unity-desktop installs unity)
or did you just reinstall the gnome-shell-extension-ubuntu-dock package?

> how do I remove the dock so I can get the GNOME launcher back instead

Hard to tell what you mean, as the Ubuntu dock is the Gnome launcher.
But I'm guessing you mean have the launcher in gnome's more commonly default setting of, "only show when opening the Activities overview".
In which case, the easiest way is to install gnome-tweaks from the Ubuntu Software and open it (gnome-tweaks ; also known as Tweaks) 
Then go to the section marked Extensions and scroll down to Ubuntu Dock and toggle it to off.

But that would only apply if just gnome and not unity.
(And for the record you cannot remove unity's dock; you can hide it, but not disable it completely, not easily at least)

Not sure where i was heading with this...

---

