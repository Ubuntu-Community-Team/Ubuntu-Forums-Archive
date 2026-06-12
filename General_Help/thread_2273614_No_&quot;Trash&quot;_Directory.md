---
title: "No &quot;Trash&quot; Directory"
date: 2015-04-14
forum: General Help
---

### Post by Jonners59 on 2015-04-14
Quite simply, I have no "Trash" directory...  How do I create one.
x86_64 14.10 utopic

---

### Post by dino99 on 2015-04-14
how to you know there is none ? check that path

sudo mkdir ~/.local/share/Trash

[http://askubuntu.com/questions/182360/trash-directory-totally-missing](http://askubuntu.com/questions/182360/trash-directory-totally-missing)

---

### Post by Impavidus on 2015-04-14
> **9d9 said:**
> how to you know there is none ? check that path

sudo mkdir ~/.local/share/Trash

[http://askubuntu.com/questions/182360/trash-directory-totally-missing](http://askubuntu.com/questions/182360/trash-directory-totally-missing)

That would give you a root owned Trash directory, which is definitely something you don't want. The first time you use the file manager (thunar, if you use Xubuntu) to move a file to trash, the trash directory should be created automatically.

---

### Post by haplorrhine on 2015-04-14
To see hidden directories beginning with a dot, use the -a option with ls.

ls -a /path/to/directory

---

### Post by Jonners59 on 2015-04-15
Thanks guys...

Simply, I know because it does not appear.  In the desk top right click, when I select "Move to Trash" I get a warning that there is no "Trash" directory.

I tried the list code, and this is what I get....  There IS a TRASH directory.... 

[HTML] ls -a ~/.local/share/
.                           mime
..                          nautilus
akonadi                     nemo
akonadi_maildir_resource_0  orage
applications                orca
backintime                  recently-used.xbel
cinnamon                    session_migration-cinnamon
contacts                    session_migration-gnome-fallback
.converted-launchers        session_migration-ubuntu
data                        session_migration-xfce
desktop-directories         sounds
eog-wallpaper.jpg           Steam
eog-wallpaper.JPG           telepathy
evolution                   totem
gegl-0.2                    tracker
gnome-do                    Trash
gnome-settings-daemon       unity-settings-daemon
gsettings-data-convert      unity-webapps
gvfs-metadata               webbrowser-app
icc                         webkit
icons                       webkitgtk
keyrings                    zeitgeist[/HTML]

I then ran the cmd to create a directory, and it said it already  existed...  Since then the "Move to Trash" option has started to  work....   Interesting.  Maybe it just needed waking up.

---

