---
title: "How to make a shortcut for an app needing u to enter &quot;./appnamehere&quot;?"
date: 2015-12-10
forum: General Help
---

### Post by javierdl on 2015-12-10
I found this app that to open it, it requires you to do it via a Terminal, you navigate to the location of the app, then enter "./" followed by the app's name (no spaces). 
Is not that I'm against the Terminal, but it's rather cumbersome compared to the standard way via the GUI.

Thanks guys,

JDL

---

### Post by deadflowr on 2015-12-10
Create a Desktop Launcher for it.
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by javierdl on 2015-12-10
Interesting! 
I'll look into this asap

Thank you DF :)

JDL

---

### Post by javierdl on 2015-12-10
Hi again,

I created a shortcut with a ".desktop" file.
But the application is not opening :(

Here's my file:

```
[Desktop Entry]
Version=x.y
Name=NormalMap Generator
Comment=...
Exec=/home/javier/Applications/NormalmapGenerator/./NormalmapGenerator
Icon=/home/javier/Pictures/blender_addon_icon.png
Terminal=false
Type=Application
Categories=Utility;Application;

```

It probably has to do with the last part of my Exec= line (./NormalmapGenerator)
The file does show with the icon I assigned to it.

Thanks,

---

### Post by ian-weisser on 2015-12-10
On the Exec line, simply use the full path of your executable.
Don't add "./", which simply means "execute this file located in the current directory"

---

### Post by javierdl on 2015-12-11
Thanks Ian :)
Unfortunately that didn't help :(
I noticed the app file doesn't have an extension. However in the instructions where DeadFlowr suggested, the executable file does have an extension (.sh).
I did try adding that ext both in the .desktop file, and the app file itself (one at a time, tested each separately), without avail.

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1449846515140/temp/noextapp.png[/IMG]

---

### Post by oldos2er on 2015-12-11
File extensions don't mean much on Linux.

If you post the .desktop file you tried to create, we can help troubleshoot it.

---

### Post by javierdl on 2015-12-11
Thanks Oldos2er, here it is then

Go to the bottom of this [page]("https://sites.google.com/site/javierwebfolio/temp")

NormalMap Generator.desktop

Thanks

---

### Post by javierdl on 2015-12-18
I guess this one is a toughy :(
Or maybe is the holidays....

---

### Post by howefield on 2015-12-18
Would it work to install the app via a ppa and obtain a launcher that way ?

---

### Post by buzzingrobot on 2015-12-18
Since this thing is a shell script, try changing "Terminal=false" to "Terminal=true".  That's a toggle that's set to 'true' if the script needs to open a terminal.  A script that runs in the background, i.e., generates no onscreen display, would  use 'false'.

You've run this thing in a terminal, so the script is already set as executable.

---

### Post by javierdl on 2015-12-19
Thank you Howefield.
Unfortunately I can't recall where I got this app from. Even after googling it I can't find it. Not the one I have anyway.

---

### Post by howefield on 2015-12-20
> **javierdl said:**
> Thank you Howefield.
Unfortunately I can't recall where I got this app from. Even after googling it I can't find it. Not the one I have anyway.

Try this and check it is what you are looking for..

[http://deb.phpblender.de/nmg.html](http://deb.phpblender.de/nmg.html) 

```
sudo wget http://deb.phpblender.de/deb.phpblender.de.gpg.key
sudo apt-key add deb.phpblender.de.gpg.key

sudo sh -c 'echo "deb http://deb.phpblender.de/ stable main" >> /etc/apt/sources.list'

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nmg
```

---

### Post by javierdl on 2015-12-20
YES! That's the one!
I just installed it with the PPA, and now it's in my App Launcher, thanks to you **howefield**!

Happy holidays!

JDL

---

### Post by howefield on 2015-12-20
Cool, glad it was what you needed, the other benefit of the PPA is that you will automatically get updates should there be any.

And Happ Hoidays to you.

---

