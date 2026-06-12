---
title: "Opera + libqt3c102-mt"
date: 2005-05-08
forum: General Help
---

### Post by tread on 2005-05-08
I installed opera8.0-shared, and I had to install libqt3c102-mt. It now runs fine, and no other qt/kde libraries are needed. However, the font size on the menu and the rightclick context menu are really small. The rest, the sidebar, the tab-names, everything looks fine. It's just the menubar thats really tiny.

[Screenshot of the problem](http://www.d.umn.edu/~salu0005/wallpapers/Screenshot.png) 
Any idea how I can increase that font size? 
Thanks.

---

### Post by tread on 2005-05-08
Never mind, I found the answer. Damn, this is the second time I am doing this - answering my own question. I should think a bit more before I post :)

Anyway, for someone who is still interested in knowing the answer:
Go to Tools->Preferences->Advanced->Fonts. Change the InterfaceMenu font.

---

### Post by 23meg on 2005-05-08
opera for linux uses qt widgets for its menus, so if it's not possible to tweak font sizes from within opera (check out if you can do it from preferences/advanced/fonts), you'll have to find a way to adjust the default font size for qt widgets. it must be possible to do this from kde control panel if you have kde installed, but otherwise you'll have to install custom qt themes, i guess.

if all fails, try opera's statically compiled qt version.

(edit: you beat me to it, it seems. and answering your own question is fine as long as it's not something terribly obvious or one that has been answered a million times; it makes it possible for other people who encounter the problem in the future to find the solution by doing a search.)

---

### Post by anders on 2005-07-19
In case anyone else is wondering how to set the appearance of qt apps if you don't have kde installed. Use the qtconfig tool, it's in the qt3-qtconfig package.

---

