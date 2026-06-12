---
title: "Fix icon error"
date: 2006-11-28
forum: General Help
---

### Post by DougieFresh4U on 2006-11-28
After getting new Frostwire installed, when I shut computer down and re-boot, anerror box appears on desktop stating: Couldn't load icon. Details: "frostwire .png not found"?   Does any one know how to make this go away. I have just today, fresh installs of Dapper on 2 machines and now have same icon problem on both as I am doing both computers at the same time. Thanks :)

---

### Post by taurus on 2006-11-28
See if you have frostwire.png in /usr/share/pixmaps!  If it's somewhere else, then you need to copy/move it to /usr/share/pixmaps...

---

### Post by DoorGunner on 2006-11-28
file:///usr/share/applications/frostwire.desktop

should look like this

> [Desktop Entry]

Name=FrostWire

GenericName=P2P Gnutella client

Comment=Search and share all kinds of files on the Gnutella network

Exec=frostwire

Icon=frostwire.png

Terminal=false

Type=Application

Categories=Application;Network;P2P;Java



failing that these are the locations i have....you can substitute this in the ICON line above

/usr/share/icons/hicolor/16x16/apps/frostwire.png
/usr/share/icons/hicolor/32x32/apps/frostwire.png
/usr/share/icons/hicolor/48x48/apps/frostwire.png
/usr/share/pixmaps/frostwire.png


cheers

---

### Post by DougieFresh4U on 2006-11-28
Thank you for replies. It's not in the pix maps. I went to usr/share application/frostwire but didn't see anything about desktop there. I clicked on it and it opened frostwire. I'm a alot confused, not a little con fused, alot confused-makes sense to me :)

---

### Post by DoorGunner on 2006-11-28
The usr/share/applications/frostwire.desktop is where most desktop icons are configured. It will open your application because it is the configuration/programming behind your icon. If you look in the /usr/shar/applications file you will see all icons there.

----------------------------------------------------------------------------------------

my suggestion would be to go and copy the png for frostwire at this location to desktop.
[http://commons.wikimedia.org/wiki/Image:FrostWire.png](http://commons.wikimedia.org/wiki/Image:FrostWire.png)
you may have to rename it to say frostwire.png if it is not named so.

substitute your_name for the proper file...ie mine is /home/john/Desktop
> 
sudo mv /home/your_name/Desktop/frostwire.png /usr/share/icons/hicolor/48x48/apps/frostwire.png
sudo mv /home/your_name/Desktop/frostwire.png /usr/share/pixmaps/frostwire.png

------------------------------------------------------------------------
for some reason the icon still doesnt appear you may need to change the Icon statment in the .desktop file to be more specific

sudo gedit /usr/share/applications/frostwire.desktop

change this line
Icon=frostwire.png
 
to read

Icon=/usr/share/pixmaps/frostwire.png

save and close....now your frost wire png should exist

---

### Post by DougieFresh4U on 2006-11-28
Thank you, DoorGunner

---

