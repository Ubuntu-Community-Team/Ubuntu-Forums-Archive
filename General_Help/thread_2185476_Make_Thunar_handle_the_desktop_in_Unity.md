---
title: "Make Thunar handle the desktop in Unity"
date: 2013-11-02
forum: General Help
---

### Post by Finalfantasykid on 2013-11-02
I am running Ubuntu 13.10 with nautilus handling the desktop icons and whatnot, however I would like to try to use Thunar to handle the desktop instead.  Is there any way to make it do this while still running Unity?

---

### Post by rihikz on 2013-11-02
Hello.

Follow these steps to switch to Thunar:


Start Synaptic, and search for and install the thunar and thunar-archive-plugin packages. After installation, you can run Thunar by typing thunar in a terminal window.
To cause Thunar to open whenever you click an entry in the Places menu, you&#8217;ll need to edit a configuration file: open a terminal window, and type the following:
```
gksu gedit /usr/share/applications/nautilus-folder-handler.desktop
```


Scroll to the bottom of the file, and look for the line that reads```
 Exec=nautilus --no-desktop %U
``` Change it so it reads ```
Exec=thunar %U
``` Then save the file, log out and back in again, and test the changes by selecting Places --> Home.

---

### Post by Finalfantasykid on 2013-11-02
That didn't seem to have any effect.  Also I didn't have **Exec=nautilus --no-desktop %U** in the file, it said **Exec=nautilus %U** instead, not that probably makes any difference.  Here are the full contents of the file:

```

[Desktop Entry]
Name=Files
Comment=Access and organize files
Exec=nautilus %U
Icon=system-file-manager
Terminal=false
NoDisplay=true
Type=Application
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;
MimeType=inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.2.1
X-Ubuntu-Gettext-Domain=nautilus

```

---

### Post by rihikz on 2013-11-02
Try changing the 4th line to ```
Exec=thunar %U
```

Make sure the file got saved, then kill nautilus and start thunar or try logging in and out.

---

### Post by Finalfantasykid on 2013-11-02
Nope, that still didn't do it.  Are you sure that is the right file, or is there another one that I need to change?

And this isn't to change what opens by default when clicking a menu (although I suppose I want that as well), but it is the file manager which handles the desktop icons.

---

### Post by Toz on 2013-11-02
> **Finalfantasykid said:**
> I am running Ubuntu 13.10 with nautilus handling the desktop icons and whatnot, however I would like to try to use Thunar to handle the desktop instead.  Is there any way to make it do this while still running Unity?
Thunar doesn't manage the desktop, its simply a file manager. There is a plan to extend it so that it takes over the desktop management facilities that xfdesktop currently performs, but that has been [post-poned to 4.12]("http://wiki.xfce.org/releng/4.10/roadmap/thunar#for_412_replace_xfdesktop_by_adding_a_thunarx_interface_for_desktop_extensions"). In Xfce, xfdesktop manages the desktop.

---

### Post by Finalfantasykid on 2013-11-02
That is sort of what I was afraid of.  And there ins't any hope to get xfdesktop running within Unity is there?  I try to run it in the terminal, and it complains that there is already another desktop manager running.

---

### Post by Toz on 2013-11-02
I honestly don't know if it will work, or if it will break stuff, or what may happen (think "end of the world"), but you can force xfdesktop to manage the desktop via:
```
xfdesktop --replace
```
...again, I have no idea what will happen if you try this on a system running unity. Perhaps best to try it on a test system or within a VM.

May I ask, why do you want to replace the Unity desktop management facilities? Or why you don't just run Xfce (Xubuntu)?

---

### Post by Finalfantasykid on 2013-11-02
Whoa what the, I was sure I ran that earlier and it didn't work.  I did it now and it did!

Could I just add xfdesktop to the startup applications?  And how would I stop nautilus from starting up?

> [COLOR=#000000]May I ask, why do you want to replace the Unity desktop management facilities? Or why you don't just run Xfce (Xubuntu)?[/COLOR]

I like XFCE, but I much prefer what Unity offers.  Except nautilus pretty much sucks now and Thunar is getting more and more appealing, and I want to give it a go for a while.

---

### Post by Toz on 2013-11-03
> Could I just add xfdesktop to the startup applications? And how would I stop nautilus from starting up?

I'm not exactly sure (uncharted territory) but it sounds right. I do believe that nautilus has a "--no-desktop" parameter that prevents it from managing the desktop. You might want to add this parameter to the Exec line of its .desktop file in /usr/share/applications.

---

### Post by philinux on 2013-11-03
> **Finalfantasykid said:**
> I am running Ubuntu 13.10 with nautilus handling the desktop icons and whatnot, however I would like to try to use Thunar to handle the desktop instead.  Is there any way to make it do this while still running Unity?

You'll have better luck with Nemo as a nautilus replacement. [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by EAZ on 2014-04-14
> **Finalfantasykid said:**
> Whoa what the, I was sure I ran that earlier and it didn't work.  I did it now and it did!

Could I just add xfdesktop to the startup applications?  And how would I stop nautilus from starting up?


This is from my Thread on LQ (LinuxQuestions.org), which is under my Account (LAN-Dominator.nl)

Official Source: 
[http://www.linuxquestions.org/questions/linux-software-2/change-of-default-file-manager-700122/#post3566192](http://www.linuxquestions.org/questions/linux-software-2/change-of-default-file-manager-700122/#post3566192)


You should copy, move and edit the default Nautilus file:
[FONT=lucida sans unicode]
[/FONT][FONT=lucida sans unicode][SIZE=2]
[/SIZE][/FONT][COLOR=#000000][FONT=Verdana]the perfect way to change the Default File Manager under Ubuntu (gnome)..[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]From Nautilus to Thunar[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]1. Backup the official Nautilus file[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:```

sudo mv /usr/bin/nautilus /usr/bin/nautilus.real
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
2. Now make the new Nautilus file[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:
```
sudo gedit /usr/bin/nautilus
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
3. place this code and save it[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:```

#!/bin/bash

#zenity --info --text="${1}/${@}" #DEBUG
if [ -n "${1}" ]; then
    if [ "${1:0:1}" == "/" ]; then
        thunar "${1}"
    elif [ "${1}" == "--no-desktop" ]; then
        if [ -n "${2}" ]; then
            if [ "${2:0:7}" == "file://" ] || [ "${2:0:1}" == "/" ]; then
                thunar "${2}"
            else
                nautilus.real "${2}"
            fi
        else
            thunar


        fi
    else
        nautilus.real "${@}"
    fi
else
    thunar
fi
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
4. Make sure that you own the file[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:```

sudo chmod 755 /usr/bin/nautilus
```[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
Done![/FONT][/COLOR]

---

