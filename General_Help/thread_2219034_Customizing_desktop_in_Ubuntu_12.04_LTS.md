---
title: "Customizing desktop in Ubuntu 12.04 LTS"
date: 2014-04-22
forum: General Help
---

### Post by fkam on 2014-04-22
[IMG]http://ubuntuforums.org/asset.php?fid=249983&uid=1916604&d=1398199010[/IMG][IMG]http://ubuntuforums.org/asset.php?fid=249983&uid=1916604&d=1398199010[/IMG][ATTACH=CONFIG]252384[/ATTACH]
[LEFT][COLOR=#000000][FONT=Ubuntubeta]Hi Everyone,[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]I am new to Ubuntu and running 12.04 LTS and is a pleasure to use. Can anyone help to customize my screen as the image above. basically having all my icons at the bottom horizontally and the conki's on the right hand side. It will also be great if anyone can help to find the image as I don't remember where I first saw it, if not any other image will do but the conki's are paramount.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]Any help is greatly appreciated.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]PS. laptop is Packard Bell Easynote L4 / 32bit.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]Thanks.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]Francka[/FONT][/COLOR][/LEFT]

---

### Post by ajgreeny on 2014-04-22
Are you sure that is ubuntu with the unity desktop?

You can autohide the launchbar on the left of the screen, but not remove it as far as I'm aware.  What you show could be another DE such as xfce4, used in Xubuntu, but your picture shows what looks like a dock, eg awn or cairo-dock at the bottom which is different from the unity launchbar, though does basically the same job.

I can not help with the wallpaper, but to get conky to the right hand side of the desktop you need to add lines to the configuration file, normally **.conkyrc** in your home.  It is impossible to see exactly what that conky window shows so you may need to search for details of the content you want for that.
```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50
```editing the figures to your liking.

---

### Post by oldfred on 2014-04-22
Every month there is this thread.

[http://ubuntuforums.org/showthread.php?t=2214270&highlight=august+april](http://ubuntuforums.org/showthread.php?t=2214270&highlight=august+april)

They post details on how they configured their system.

---

### Post by ibjsb4 on 2014-04-22
With no panels and a dock (cario dock I think)  My guess would be gnome-fallback (it does say ubuntu :))

If you wish to use/try this desktop, it can be added to your current ubuntu install.

[https://apps.ubuntu.com/cat/applications/precise/gnome-session-fallback/](https://apps.ubuntu.com/cat/applications/precise/gnome-session-fallback/)

---

### Post by whatthefunk on 2014-04-22
Google image search is your friend:
[http://ubuntuforums.org/showthread.php?t=2161991&page=2](http://ubuntuforums.org/showthread.php?t=2161991&page=2)

---

### Post by Frogs Hair on 2014-04-22
Cairo Dock stand-alone session and VinDSL Conky would be my guess. 

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

