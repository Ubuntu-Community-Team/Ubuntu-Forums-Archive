---
title: "Turning shortcut.desktop into Executable"
date: 2019-11-26
forum: General Help
---

### Post by imzack2 on 2019-11-26
I have done both the text method, and the "gnome-desktop-item-edit" method w/ the same results.

Each time I make a shortcut.desktop file, it shows up on my desktop, but as a "Gear" and not a clickable- executable icon.

I check the properties, and it says its supposed to run as a exectuable.

I also run "sudo chmod +x shortcut.desktop"  and no change.


Has anyone else ran into this issue and resolved it?

Thanks

---

### Post by CatKiller on 2019-11-27
I think the Gnome devs removed the ability to have launchers on the desktop.

---

### Post by vanadium on 2019-11-27
Ubuntu 18.10 and up use a Gnome Shell extension to provide desktop icons. This extension is rather new and has its limitations. The "supported" way to work with application launchers is to move your .desktop file to .local/share/applications. Once done, you will find the launcher in the Application menu, so you can pin it to the dock from there. If you do not want to pin it, it will still appear readily available in front in the Application Overview, "Frequent" tab if you use it regularly. An advantage of the Application view is that is available anytime, even when your desktop is covered with windows.

---

### Post by imzack2 on 2019-11-27
Thank you Vanadium.

That worked, I was struggling w/ this for some time now.

Thanks again!

---

