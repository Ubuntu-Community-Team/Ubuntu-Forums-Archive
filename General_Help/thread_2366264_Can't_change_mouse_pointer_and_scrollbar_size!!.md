---
title: "Can't change mouse pointer and scrollbar size!?!"
date: 2017-07-15
forum: General Help
---

### Post by hatetech on 2017-07-15
16.04 Mate, rx480 video card. I've been trying to find a way to increase the size of the mouse pointer and width of all scrollbars, but nothing works. The style settings in the control panel have the option for change pointer size, but it only effects Chrome and goes back to appearing small everywhere else. It makes no sense! Same with editing scrollbar width in the gtk3.0 css. It's stupid. Chrome abides by the setting, but nothing else does (Firefox, Thunderbird, Hexchat, qBittorrent, gFTP, etc).

---

### Post by Dennis N on 2017-07-15
What mouse pointer theme would that be?

---

### Post by hatetech on 2017-07-15
> **Dennis N said:**
> What mouse pointer theme would that be?

Mate, I guess. I've got it all customized. I noticed the damn thing reset again. The pointer is a little bigger now, but not big enough for my taste. Still looking for a scrollbar fix that works beyond chrome.

---

### Post by Dennis N on 2017-07-15
Ok, MATE mouse pointer theme has 3 sizes: 24,32,or48 pixels.

Create a text file **.Xresources** in your home folder with this one line specifying the size. The period at beginning of .Xresources is important, as it is a hidden file. 
```
Xcursor.size:32
```
If .Xresources already exists, add the line at the bottom. 
Reboot and see if the cursor size stays the same. If too small, edit size to 48 and reboot again.
Cursor on login screen can't be resized.

As to width of scrollbar, I can't offer any suggestion for that.

---

### Post by vasa1 on 2017-07-16
> **hatetech said:**
> 16.04 Mate, ... Same with editing scrollbar width in the gtk3.0 css. It's stupid. Chrome abides by the setting, but nothing else does (Firefox, Thunderbird, Hexchat, qBittorrent, gFTP, etc).

What did you try editing in the "gtk3.0 css" and which exact file was that? Could you post the entire path and filename?

I'm on Kubuntu 16.04 right now but here's an image showing that it should be possible to alter the scrollbar width (even in another DE).

---

### Post by hatetech on 2017-07-16
> **vasa1 said:**
> What did you try editing in the "gtk3.0 css" and which exact file was that? Could you post the entire path and filename?

I'm on Kubuntu 16.04 right now but here's an image showing that it should be possible to alter the scrollbar width (even in another DE).

I found a post with a path to a gtk3.0 css that wasn't actually valid on my system. Then I found a followup saying to put the info in "/home/username/.config/gtk-3.0/gtk.css". Like I said, it works, but only in Chrome.

```

.scrollbar {
  -GtkScrollbar-has-backward-stepper: true;
  -GtkScrollbar-has-forward-stepper: true;
  -GtkRange-slider-width: 20;
  -GtkRange-stepper-size: 20;
}

```

---

### Post by hatetech on 2017-07-17
Nothing? Come on. Somebody has to know how to get everything in proper proportions. This is stupid. The scrollbars are too skinny and the icons in the alt+tab popup are too damn small.

---

