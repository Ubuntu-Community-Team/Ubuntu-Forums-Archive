---
title: "Hugin panorama editor"
date: 2022-06-02
forum: General Help
---

### Post by JamButty on 2022-06-02
Just installed Jammy and find no way to install Hugin panorama editor, which I have used for many years now. After making sure universe is in place and updated, command line attempt gives
[PHP]E: Package 'hugin' has no installation candidate[/PHP] 
and it no longer exists in the standard GUI "Ubuntu Software". I understood that Jammy is going whole hog on Snaps, but previously snap apps appeared in the standard catalogue.
Must I install "snap store"? The reviews make that look about as appealing as anthrax.

---

### Post by TheFu on 2022-06-02
[https://askubuntu.com/questions/1404204/how-to-install-hugin-in-ubuntu-22-04-jammy-jellyfish](https://askubuntu.com/questions/1404204/how-to-install-hugin-in-ubuntu-22-04-jammy-jellyfish) says that Hugin is available as either a flatpak or an AppImage.

---

### Post by JamButty on 2022-06-02
Trying the flatpack route as described in that article and get this error:```
flatpak install flathub net.sourceforge.Hugin

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/fred/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

Looking for matches…
error: No remote refs found similar to ‘flathub’


```
is there a syntax error in the Askubuntu article?

---

### Post by JamButty on 2022-06-02
ok, found better info, fixing plugins/repositories now.

---

### Post by JamButty on 2022-06-02
Ok, seems to be working now. That article left out two important bits:```
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
followed by a reboot.

---

