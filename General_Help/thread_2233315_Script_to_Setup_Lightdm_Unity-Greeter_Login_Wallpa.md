---
title: "Script to Setup Lightdm Unity-Greeter Login Wallpaper/Dots"
date: 2014-07-07
forum: General Help
---

### Post by TJSL on 2014-07-07
System: Ubuntu 14.04, clean install

I am having issues scripting the commands below to change the background on my login screen (see [http://askubuntu.com/questions/455849/unity-greeter-does-not-display-custom-wallpaper](http://askubuntu.com/questions/455849/unity-greeter-does-not-display-custom-wallpaper))

```

sudo xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false'
gsettings set com.canonical.unity-greeter background 'path-to-image'
exit
```

The above commands appear to work, but when I run them as a script (below), the script does not return from "sudo su lightdm -s /bin/bash"


```

#! /usr/bin/env bash
sudo xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false'
gsettings set com.canonical.unity-greeter background 'path-to-image'
exit
```

It is apparently necessary to "wrap" su when executing it within the bash script. I have explored executing commands from su and sudo (e.g., with -c option). However, it appears that I am not using the correct username, or I am, and "sudo xhost +SI:localuser:lightdm" is requiring another layer of complexity (beyond merely switching the user). What changes do I need to make to my script for it to run?

Thanks!

---

### Post by TJSL on 2014-07-08
The solution below appears to work. The salient addition is <<HERE ... HERE which wraps the commands that need to be executed as the lightdm user.

```

sudo cp files/background.jpg /usr/share/backgrounds/background.jpg #copy wallpaper into system hierarchy

#configure lightdm
sudo xhost +SI:localuser:lightdm

sudo su lightdm -s /bin/bash <<HERE
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false' #eliminates display of other users wallpaper at login
gsettings set com.canonical.unity-greeter background '/usr/share/backgrounds/background.jpg' #set login wallpaper
gsettings set com.canonical.unity-greeter draw-grid 'false' #removes dots on background
gsettings set com.canonical.unity-greeter background-color '#000000' #eliminates purple screen before background loads
exit
HERE
```

---

