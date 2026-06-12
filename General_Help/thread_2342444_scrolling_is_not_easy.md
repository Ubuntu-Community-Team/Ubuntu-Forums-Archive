---
title: "scrolling is not easy"
date: 2016-11-06
forum: General Help
---

### Post by Richard-S on 2016-11-06
The scrolling column on the right of the screen is so narrow that it is annoying to get the mouse cursor on it. How do i make it wider? And there are no up and down arrows to click on to scroll incrementally. If I click at the bottom it scrolls immediately all the way to the bottom. How do I get it to scroll down gradually?

And the "X" up in the top left to close a window is so tiny I can hardly see it. How do I make it larger?

Richard

---

### Post by fizikz on 2016-11-06
If you hover your cursor on the scroll bar area, the bar should get wider, making it easier to grab.

It's also possible to disable the "overlay" scrollbars to keep the normal scrollbars at all times. 

From [https://ubuntuforums.org/showthread.php?t=2323881](https://ubuntuforums.org/showthread.php?t=2323881), assuming you're on Ubuntu 16.04, run:

```
echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment
```

---

### Post by vasa1 on 2016-11-07
> **Richard-S said:**
> The scrolling column on the right of the screen is so narrow that it is annoying to get the mouse cursor on it. How do i make it wider? And there are no up and down arrows to click on to scroll incrementally. If I click at the bottom it scrolls immediately all the way to the bottom. How do I get it to scroll down gradually?

And the "X" up in the top left to close a window is so tiny I can hardly see it. How do I make it larger?

Richard
Re. "there are no up and down arrows to click on to scroll incrementally", many themes don't have these. You'll have to search for a theme that does. Even then you may need to edit the theme's *gtk-widgets.css* to change ```
    -GtkScrollbar-has-backward-stepper: false;
    -GtkScrollbar-has-forward-stepper: false;

```
to```
    -GtkScrollbar-has-backward-stepper: true;
    -GtkScrollbar-has-forward-stepper: true;

```
Re. "If I click at the bottom it scrolls immediately all the way to the bottom. How do I get it to scroll down gradually?", you need to switch to legacy scrolling. Add```
gtk-primary-button-warps-slider=false
```to *~/.config/gtk-3.0/settings.ini* and to */etc/gtk-3.0/settings.ini*.

Re. "And the "X" up in the top left to close a window is so tiny I can hardly see it. How do I make it larger?", that may depend on your window manager theme. I get round the issue by pressing alt+spacebar and then c (for close).

---

### Post by Richard-S on 2016-11-07
Thank you for your excellent help.

Richard

---

