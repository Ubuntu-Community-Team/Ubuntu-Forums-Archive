---
title: "Resizing windows - limitation? [Lubuntu 18.04]"
date: 2018-09-19
forum: General Help
---

### Post by doskey123 on 2018-09-19
Hi, I have recently installed Lubuntu 18.04 on my old Lifebook 7210. I had to apply some fixes to lower the boottime from 1.2min to 14s, but I'm very satisfied with the performance now. 

However, I have run into a problem with resizing the windows. On Windows 7, I can easily resize nearly every window to even a ridiculous small size. On Lubuntu there seems to be a rather large minimum width that the windows need to keep at any time. I think it is related to the upper menu bar, as I can only resize e.g. AbiWord and Audacious to the end of the upper menu bar text (in Abiword that is "Hilfe" / "Help"). 

Because of this, If I place two AbiWord windows next to each other, they overlap (see attachment). This is not good for my productivity as I cannot see the full page of my second file while working on the first file.

What - if any - is the best practice to change this? I have found posts for old Lubuntu versions, but I am not sure if these fixes would still work / if they apply to my problem.

---

### Post by howefield on 2018-09-19
Thread moved to the "*General Help*" forum.

---

### Post by Dennis N on 2018-09-19
On Abiword, I believe you are correct in that the minimum width is determined by the need to show all the menu bar titles. You could use Libre Office Writer, which will work in a narrower window.  Abiword won't hide the menu item names (at least on the version I looked at in 16.04).

Likewise, I think audacious window is limited by the toolbar icons and their combined width. It used to have the arrow at the right like Libre Office, but that was taken out in recent versions. But you wouldn't want two audacious windows anyway. Put it in another work space if you don't like overlap.

---

### Post by Holger_Gehrke on 2018-09-19
Abiword uses GTK+. You can put a file 'gtk.css' into '~/config/gtk-3.0/' and style the menu bar to use a narrower font and less space between the items on the menu. As far as I can see in the GTK inspector (GTK_DEBUG=interactive abiword) abiword does not give it's window or its other elements names or classes one could use as application-specific selectors, so this would change all programs using GTK 3 that have the same object hierarchy in their UI. With
```

window>box>menubar {
  font-family:"PT Sans Narrow";
  font-size: 12px;
}

window>box>menubar>menuitem {
  padding-left:3px;
  padding-right:3px;
}

```
in the 'gtk.css' I got the menu ending at about the middle of the font-size toolbar item.

Holger

---

