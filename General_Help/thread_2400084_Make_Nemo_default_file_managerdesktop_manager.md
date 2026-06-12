---
title: "Make Nemo default file manager/desktop manager"
date: 2018-09-02
forum: General Help
---

### Post by linkboy on 2018-09-02
I was wondering if there was a way to make Nemo the default file manager/desktop manager in Ubuntu Budgie 18.04. I'm not a huge fan of the layout for Nautilus and I've found that Nemo suits my needs better. 

Thank you for your time.

---

### Post by #&amp;thj^% on 2018-09-02
I did this with Gnome but it should also work with Budgie.

Set Nemo As Default File Manager.
These commands given below will disable Nautilus on Ubuntu Linux and it will stop Nautilus from handling the Desktop. To do so, run the following commands:

```
sudo apt update
gsettings set org.gnome.desktop.background show-desktop-icons false
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

Once the above commands are executed, restart.

Reset Changes; Disable Nemo As Default File Manager

Run the following command to revert the changes and reset Nautilus; stop Nemo to use as the default file manager.
```

sudo apt update
gsettings set org.gnome.desktop.background show-desktop-icons true
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```
And again Restart to see the changes.
Good Luck

---

### Post by linkboy on 2018-09-02
I did that and when I add the desktop icons back in Budgie settings, it goes right back to Nautilus until I open Nemo. As long as Nemo is open, it acts as the default file manager, but the second I close it, Nautilus takes over the desktop again. This is where I'm getting confused.

edit.
I think it might be something with Budgie because I just got Nemo to manage the desktop, but I can't add things like my home icon or trash. The minute I enable that setting in Budgie Desktop settings, it turns my Nautilus desktop back on but I can't interact with the icons.

---

### Post by #&amp;thj^% on 2018-09-02
Have you rebooted yet?
Also make sure there is nothing left with nautilus as a name in **"/etc/mime.types"** you will need to carefully review if nothing is left of nautilus. If it is, replace it by nemo.
EDIT: Also if you are curious why the wrong filemanager is started if you click on a folder icon check the actual command the starter launches.

you also have to look in the file "/usr/share/applications/mimeinfo.cache"

```

sudoedit /usr/share/applications/mimeinfo.cache
```
Look for this line "inode/directory=nautilus.desktop"

Now be sure it reads as follows
```

inode/directory=nemo.desktop
```
Again a reboot will be necessary for the change to be seen.

---

### Post by mc4man on 2018-09-02
Being the default file-manager & handling the Desktop are 2 separate things
(- whether budgie has additional issues no idea, but,

The *xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search* command sets as default file-manager
The *gsettings set org.gnome.desktop.background show-desktop-icons false *command sets the stage for nemo handling the Desktop but is not all that's needed. Additionally - 

This command should return a value of true, if not then set as true.
```
 gsettings get org.nemo.desktop show-desktop-icons
```
If not true then - 
```
gsettings set org.nemo.desktop show-desktop-icons true
```

Also the nemo-desktop command needs to be run on login. The repo package of nemo has the nemo-autostart.desktop file needed but doesn't activate it, it's instead installed to /usr/share/applications instead of /etc/xdg/autostart

So either move it there as root or copy to the  ~/.config/autostart/  folder  (create folder if need be.

Here I delay it 2 sec. to make sure login is finished before running so use I this as the autostart  .desktop
```

[Desktop Entry]
Type=Application
Name=Nemo
Comment=Start Nemo desktop at log in
Exec=nemo-desktop
AutostartCondition=GSettings org.nemo.desktop show-desktop-icons
X-GNOME-AutoRestart=true
X-GNOME-Autostart-Delay=2
NoDisplay=false
```

---

