---
title: "How do I back out / Undo these commands?"
date: 2013-10-30
forum: General Help
---

### Post by linuxology on 2013-10-30
sudo apt-add-repository ppa:alanbell/unity
sudo apt-get update
sudo apt-get install unity-window-quicklists
sudo sed -i 's/OnlyShowIn=UNITY/OnlyShowIn=Unity/g' /etc/xdg/autostart/unity-window-quicklists.desktop (This command line allows for the Unity Window Quicklists to start automatically when you log into the system.)

---

### Post by Lars Noodén on 2013-10-30
It should be something like this

```

sudo apt-get remove unity-window-quicklists
sudo apt-add-repository -r ppa:alanbell/unity
sudo apt-get update
sudo cp /etc/xdg/autostart/unity-window-quicklists.desktop /etc/xdg/autostart/unity-window-quicklists.desktop.old
sudo sed -i 's/OnlyShowIn=Unity/OnlyShowIn=UNITY/g' /etc/xdg/autostart/unity-window-quicklists.desktop 

```

It would have been good to keep a backup copy of /etc/xdg/autostart/unity-window-quicklists.desktop the first time around

---

### Post by linuxology on 2013-10-30
Thanks Lars!

---

### Post by Lars Noodén on 2013-10-30
No worries.  BTW I updated the 4th line, since I managed to leave out the "cp" but it does not matter much.  With editing files, even if the instructions don't call for it, I prefer to make a backup copy.  It is so much easier just to replace the file from the backup than to go through notes to undo changes.

---

