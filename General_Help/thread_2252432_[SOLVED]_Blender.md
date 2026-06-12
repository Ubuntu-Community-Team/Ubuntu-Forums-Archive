---
title: "[SOLVED] Blender?"
date: 2014-11-11
forum: General Help
---

### Post by peterkirylo on 2014-11-11
Can anyone tell me how to upgrade from blender 2.69 that you get from app store to blender 2.72 downloaded from [http://www.blender.org/download/](http://www.blender.org/download/) please help.):P

or maybe just how to make a desktop shortcut for it?:confused::confused:

anyone?

---

### Post by lisati on 2014-11-12
Please be patient. This forum has members who live in many different time zones, and someone who is able to help might not have seen your thread yet.

---

### Post by mcduck on 2014-11-12
The best way is to just uninstall the version from Ubuntu's repositories, download the one from Blender's web site, extract it somewhere in your home directory, and then create a .desktop file for it in *~/.local/share/applications*.

Here's the .desktop file I'm using:
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Categories=Graphics;
Name[en_US]=Blender
Name=Blender
Exec=/home/mcduck/Programs/Blender/blender
Terminal=false
MimeType=application/x-blender
Icon[en_US]=blender
Icon=/usr/share/icons/Moka/256x256/apps/blender.png

```
(Change the icon to whatever you like, if nothing else you can find Blender icons packaged witht he application itself, in the Icons folder...)

After that it should appear in Unity's dash, or your desktop menus, depending on what desktop environment you are using. If not, log out and back again and things should start working.

Updates are fairly easy, just extract new files over the existing Blender installation, version-specific stuff goes into folder with the version name, which you can delete afterwards. Having a PPA repository would of course be convenient, but since it really is just extract-and-run, I can see why no one has bothered to deal with packaging it into .deb files and maintaining a PPA repository for it.

Edit:
You might also want to add this line in *~/.local/share/applications/mimeapps.list*:
```
application/x-blender=blender.desktop;
```
The name should of course match with the name of the .desktop file you created. This allows you to open .blend files by double-clicking on them.

---

### Post by jhay2 on 2014-11-12
blender from irie ppa should work :)

---

### Post by mcduck on 2014-11-12
He seems to be compiling it with a bit annoying options, for example CUDA support is missing by default some professional codecs are left out,, and also the PPA doesn't include all Ubuntu versions, which are the main reasons I've been avoiding it. Plus he's not providing the stable version but weekly build from git, not the best way for anyone who uses it for work purposes...

---

### Post by peterkirylo on 2014-11-12
> **mcduck said:**
> The best way is to just uninstall the version from Ubuntu's repositories, download the one from Blender's web site, extract it somewhere in your home directory, and then create a .desktop file for it in *~/.local/share/applications*.

Here's the .desktop file I'm using:
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Categories=Graphics;
Name[en_US]=Blender
Name=Blender
Exec=/home/mcduck/Programs/Blender/blender
Terminal=false
MimeType=application/x-blender
Icon[en_US]=blender
Icon=/usr/share/icons/Moka/256x256/apps/blender.png

```
(Change the icon to whatever you like, if nothing else you can find Blender icons packaged witht he application itself, in the Icons folder...)

After that it should appear in Unity's dash, or your desktop menus, depending on what desktop environment you are using. If not, log out and back again and things should start working.

Updates are fairly easy, just extract new files over the existing Blender installation, version-specific stuff goes into folder with the version name, which you can delete afterwards. Having a PPA repository would of course be convenient, but since it really is just extract-and-run, I can see why no one has bothered to deal with packaging it into .deb files and maintaining a PPA repository for it.

Edit:
You might also want to add this line in *~/.local/share/applications/mimeapps.list*:
```
application/x-blender=blender.desktop;
```
The name should of course match with the name of the .desktop file you created. This allows you to open .blend files by double-clicking on them.


ok nvm I am not that skilled at computers guess I wil just have to load blender the hard way through the file itself because I have no isea how to do what you ask.:(

I tried using his site [http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/](http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/) but when I bring up terminal I can't type?

---

### Post by mcduck on 2014-11-12
all you have to do is open a text editor, paste the code I use in my .desktop file (make sure the Exec-line matches with the location where you extracted Blender), and then save it into *~/.local/share/applications* folder (a hidden folder inside you home directory) using *blender.desktop* as the name.

Setting the last line for custom icon is optional, most icon themes already come with an icon for Blender, and once you have saved the file you can also right-click on it, select "Properties" and set the icon there if you prefer.

---

### Post by peterkirylo on 2014-11-12
I got i I typed Ctrl+Alt+T to bring up terminal then typed "[FONT=monospace]gnome-desktop-item-edit --create-new ~/Desktop" without quotes and from there it was easy.Ty for every ones help.:) [/FONT]

---

### Post by mcduck on 2014-11-12
> **peterkirylo said:**
> I tried using his site [http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/](http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/) but when I bring up terminal I can't type?

oh, wow. That's quite complicated (and to be honest, pretty horrible) way of creating a simple .desktop file :D I really wouldn't recommend following those instructions, especially since they require installing extra applications you don't need and probably don't really even want.

*gnome-desktop-item-edit* is quite likely already installed by default, so everything above that part in the instructions can be discarded. And you still need to move the .desktop file created that way into correct location if you want it to appear in desktop menus or Unity's dash.

---

