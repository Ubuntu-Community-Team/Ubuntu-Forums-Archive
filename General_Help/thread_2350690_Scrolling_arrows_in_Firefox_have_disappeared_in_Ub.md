---
title: "Scrolling arrows in Firefox have disappeared in Ubuntu"
date: 2017-01-26
forum: General Help
---

### Post by elvis6 on 2017-01-26
A few months ago, the following incident occurred and has not resolved, and scrolling has been a major pain ever since.
All of a sudden, those 2 arrows, one at the far upper right corner and one at the far lower right corner of the Firefox browser have disappeared.
This is a huge inconvenience because those were the easiest methods to gradually, slowly scroll down a page, line by line.
If I use any other of the various methods, it moves too fast, and is very hard to control, which means over-scrolling and skipping way past the part of the page I was trying to view.
This has happened on both of the PC's I use Ubuntu on. So it's not some random glitch that happened to one PC. 
They are both running "12.04 Precise".
One of them, I have dual OS, and when I switch to the other OS and open Firefox, the scrolling arrows still appear ; So I know it is an issue with Ubuntu OS and not Firefox browser.
I attached a screenshot, with red arrows and circles pointing to where those much-needed "scrolling arrows" used to be, but now have disappeared.


So, how did this happen, and how can I recover them ?

Thanks for the help.

---

### Post by &amp;KyT$0P# on 2017-01-26
What version of Firefox?  Where did you get it?

---

### Post by elvis6 on 2017-01-26
> **halogen2 said:**
> What version of Firefox?  Where did you get it?

Firefox version 50.1.0.
As far as obtaining it, I'm almost 100% certain it just came with the Ubuntu OS, and it may have automatically upgraded to each version.

---

### Post by bearlake on 2017-01-26
Hi,

It has been like that for a few years now using Gnome or Xubuntu.

There was a work around but I didn't really care for it.

---

### Post by vasa1 on 2017-01-26
> **bearlake said:**
> ...
There was a work around but I didn't really care for it.
Details?

OP, you need to tell us which gtk theme you're using. Do you know? If it's the default Ambiance theme, the solution may lie in editing *~/.themes/MyAmbiance/gtk-3.0/gtk-widgets.css* where MyAmbiance is nothing but a copy of */usr/share/themes/Ambiance*. You could, if you're careful enough, sudo edit the system file but I choose not to.

In *gtk-widgets.css*, change the values of *has-backward-stepper* and *has-forward-stepper* from "0" to "1".```
/*************
 * scrollbar *
 *************/
.scrollbar {
    -GtkScrollbar-has-backward-stepper: 0;
    -GtkScrollbar-has-forward-stepper: 0;
    -GtkScrollbar-trough-border: 0;
    -GtkScrollbar-min-slider-length: 31;
    -GtkRange-slider-width: 10;

    background-color: @scrollbar_track_color;
    background-image: none;
    background-size: 0;
    border: none;
    border-radius: 0;
}
```

I don't use those arrows. For gradual scrolling, I prefer single-pressing the keyboard up and down arrows.

---

### Post by &amp;KyT$0P# on 2017-01-26
bearlake, you are using the Greybird GTK theme, which is **supposed** to not have scroll arrows.

vasa1, I'm pretty sure their GTK theme is indeed Ambiance.  Their screenshot looks exactly like what I get on 12.04 with Ambiance theme.  Good call. :)

---

### Post by bearlake on 2017-01-26
> **vasa1 said:**
> Details?

OP, you need to tell us which gtk theme you're using. Do you know? If it's the default Ambiance theme, the solution may lie in editing *~/.themes/MyAmbiance/gtk-3.0/gtk-widgets.css* where MyAmbiance is nothing but a copy of */usr/share/themes/Ambiance*. You could, if you're careful enough, sudo edit the system file but I choose not to.

In *gtk-widgets.css*, change the values of *has-backward-stepper* and *has-forward-stepper* from "0" to "1".```
/*************
 * scrollbar *
 *************/
.scrollbar {
    -GtkScrollbar-has-backward-stepper: 0;
    -GtkScrollbar-has-forward-stepper: 0;
    -GtkScrollbar-trough-border: 0;
    -GtkScrollbar-min-slider-length: 31;
    -GtkRange-slider-width: 10;

    background-color: @scrollbar_track_color;
    background-image: none;
    background-size: 0;
    border: none;
    border-radius: 0;
}
```

I don't use those arrows. For gradual scrolling, I prefer single-pressing the keyboard up and down arrows.

Using Ambiance theme, you lose the up and down arrows.

There was two themes that gave you the up and down arrows back, which ones, I forget now as this was a few years back.

---

### Post by bearlake on 2017-01-26
I decided to give this another try using the following.

Edit or create ~/.config/gtk-3.0/gtk.css 

added the following code:

```
*{

-GtkScrollbar-has-backward-stepper: 1;
-GtkScrollbar-has-forward-stepper: 1;

}
```

Closing Firefox and open it again to this:

---

