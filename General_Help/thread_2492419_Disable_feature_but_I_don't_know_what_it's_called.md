---
title: "Disable feature but I don't know what it's called"
date: 2023-11-10
forum: General Help
---

### Post by matthewbaynham on 2023-11-10
I've just updated to a the latest version of Ubuntu 23.10 and there is something that I find really annoying but I don't know what it's called so I can't just look it up.

As I move window around the screen, it doesn't matter if it's LibreOffice or Terminal window this goes for any app, as the window gets to the edge of the desktop it will want to change size and shape.  Whilst the mouse button is still pressed and I'm dragging the window to the corner, there is an orange glow and as I release the mouse button the window snaps to be either left half of the screen, or the top half of the screen or some other size and shape that I don't want.

I just want the windows to stay the same size and shape as I drag them around the screen.

This is really annoying because I have loads of windows open and I want to be able to position these windows next to each other, but then when Ubuntu decides it'll change the size and shape of the window it covers the other windows that I want to be next to it.

I just want to switch off this feature.

How do I switch it off?

Or what is it called so I can look it up on DuckDuckGo?

---

### Post by tea for one on 2023-11-10
Is it this: gnome-shell-extension-ubuntu-tiling-assistant

---

### Post by matthewbaynham on 2023-11-10
Fantastic thank you for that.

I just ran...
```
gnome-extensions disable [EMAIL="tiling-assistant@ubuntu.com"]tiling-assistant@ubuntu.com[/EMAIL]
```
...and it's perfect.

---

### Post by dragonfly41 on 2023-11-10
To address your requirement about tile management (since your original point is solved) I point you to this website which is for the editor I use, but also in top menu explore X-Tile.

[https://www.giuspen.net/cherrytree/](https://www.giuspen.net/cherrytree/)

[https://www.giuspen.net/x-tile/](https://www.giuspen.net/x-tile/)

---

