---
title: "Windows 10 -like desktop window snapping shortcut style? (17.10, Wayland Gnome)"
date: 2017-11-19
forum: General Help
---

### Post by jarvo2 on 2017-11-19
What's the best way of having windows 10 -ish style of windows management in Gnome Wayland GUI? 

I'm using a Kwin script at my KDE desktop, similiar as this [https://github.com/koenhausmans/kwin-quick-tiling-windows10/blob/master/contents/code/main.js](https://github.com/koenhausmans/kwin-quick-tiling-windows10/blob/master/contents/code/main.js) , but modified for my preferences.

one of the examples from the Kwin script:
> 

var QuickTileUpwards = function() {
    if (_IsWindowTiledToLeft()) {
        if (_IsWindowTiledToTop()) {
            workspace.slotWindowMaximize();
        } else if (_IsCurrentWindowVerticallyMaximized()) {
            workspace.slotWindowQuickTileTopLeft();
        } else if (_IsWindowTiledToBottom()) {
            workspace.slotWindowQuickTileLeft();
        }
    } else if (_IsWindowTiledToRight()) {
        if (_IsWindowTiledToTop()) {
            workspace.slotWindowMaximize();
        } else if (_IsCurrentWindowVerticallyMaximized()) {
            workspace.slotWindowQuickTileTopRight();
        } else if (_IsWindowTiledToBottom()) {
            workspace.slotWindowQuickTileRight();
        }
    } else {
        workspace.slotWindowMaximize();
    }
}


Any help is appreciated.

-Joonas

---

