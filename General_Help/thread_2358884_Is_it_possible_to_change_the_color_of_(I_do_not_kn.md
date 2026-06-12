---
title: "Is it possible to change the color of (I do not know what it's called)"
date: 2017-04-18
forum: General Help
---

### Post by offir on 2017-04-18
Is it possible to change the color of the rectangle that moves on the right side of the screen?
When moving down or up on the web page

I do not see anything 
I have to move with the mouse cursor to the right side and then it sticks out and it has a light gray color and it's hard for me to see it

---

### Post by RobGoss on 2017-04-18
I think that might be a browser thing if your using Google Chrome, you can change your theme is should get darker depending on what theme you choose

What Web browser are you using?

---

### Post by offir on 2017-04-18
i use firefox
how can i di that in firefox

---

### Post by RobGoss on 2017-04-18
I would recommend doing a Google search to find more information on how to set the different themes for Firefox I'm sure there's a settings tab for that browser

in the mean time this should help with the different theses that's are available

Firefox themes
[https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/)

The themes are add-ons I believe and you should be able to install them with just a click

Here is the help page from Mozilla
[https://support.mozilla.org/t5/Manage-preferences-and-add-ons/Use-themes-to-change-the-look-of-Firefox/ta-p/2843](https://support.mozilla.org/t5/Manage-preferences-and-add-ons/Use-themes-to-change-the-look-of-Firefox/ta-p/2843)

---

### Post by dragonfly41 on 2017-04-18
There is this add-on [https://addons.mozilla.org/en-GB/firefox/addon/noiascrollbars/](https://addons.mozilla.org/en-GB/firefox/addon/noiascrollbars/)

but note from that page that from November 2017 with a change in Firefox this might no longer work.

Don't you have a mouse with scroll?

---

### Post by offir on 2017-04-18
i know this option (different themes)
i want to change only this bar 
the rest is ok

---

### Post by cmcanulty on 2017-04-18
Have you tried this firefox add on? I love it

[http://barisderin.com/?p=287]("http://barisderin.com/?p=287")

---

### Post by vasa1 on 2017-04-18
Looks like OP has an issue with the scrollbar in Firefox which is now a gtk3 application.

I'm attaching three images.

Ambiance-pre is with the mouse pointer not over the scrollbar region. The scrollbar thumb is a thin sliver.
Ambiance-hover is with the mouse pointer (now not visible) over the scrollbar. The scrollbar thumb is now clear.
Adwaita has the scrollbar thumb clearly visible even though the mouse pointer isn't over the scrollbar region. When the mouse pointer is over the scrollbar region, the scrollbar thumb turns a nice shade of blue.

OP could consider using the Adwaita theme instead of Ambiance.

---

### Post by vasa1 on 2017-04-18
If OP is feeling adventurous enough, it's possible to hack the *gtk-widgets.css* file in the theme's folder to get a permanent broad scrollbar thumb.

I'm assuming the theme is Ambiance which is the default in Ubuntu.

Copy the Ambiance folder from */usr/share/themes* over to *~/.themes* and name it MyAmbiance so you should now have *~/.themes/MyAmbiance*. Step down to the gtk-3.0 folder in which there's *gtk-widgets.css*. **Make a backup of that file.** Now, open the file using gedit --- you don't need sudo --- and move down to where you'll see```
/*************
 * scrollbar *
 *************/

```
Then, slowly delete **all** content until you come to the next section:```
/*******************
 * scrolled window *
 *******************/

```
In place of what you've deleted, add```
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

.scrollbar.overlay-indicator {
    background-color: transparent;
}

.scrollbar:hover,
.scrollbar.dragging {
    background-color: @scrollbar_track_color;
}

.scrollbar:hover:backdrop,
.scrollbar.dragging:backdrop {
    background-color: @backdrop_selected_bg_color;
}

.scrollbar.slider {
    background-color: alpha(@selected_bg_color, 0.8);
    border-radius: 1px;
}

.scrollbar.slider:hover {
    background-color: alpha(@selected_bg_color, 0.85);
}

.scrollbar.slider:active {
    background-color: @selected_bg_color;
}

.scrollbar.slider:backdrop {
    background-color: alpha(@backdrop_filling_bg, 0.8);
}

.scrollbar.slider:hover:backdrop {
    background-color: alpha(@backdrop_filling_bg, 0.85);
}

.scrollbar.slider:active:backdrop {
    background-color: @backdrop_filling_bg;
}

```
Save the file and close the editor.

Use your distro's method (Unity tweak tool or whatever that is) to change to another theme, say, Radiance. Then switch back to MyAmbiance. This step may not even be needed. The next time you open **any** gtk3 application, including Firefox, you should see permanently visible scrollbar thumbs.

---

### Post by offir on 2017-04-18
> Don't you have a mouse with scroll? 
yes i do but I'm more comfortable moving the page with the scrollbar
the add on you suggested is good But first I want to try to do it without add on

to vasa1
I tried what was written it did not work
i use theme radiance

i copy Folder radiance to another Location so i have backup
and edit the file you said like you said 
then change to another theme and back

---

### Post by vasa1 on 2017-04-18
> **offir said:**
> ...
to vasa1
I tried what was written it did not work
i use theme radiance
...
Sorry to read that. I should mention that what I wrote was for Ambiance supplied for 16.04.

---

### Post by offir on 2017-04-18
> Sorry to read that. I should mention that what I wrote was for Ambiance supplied for 16.04. 
Thanks for trying to help
i will use what dragonfly41 recommended

---

### Post by Habitual on 2017-04-18
> **dragonfly41 said:**
> Don't you have a mouse with scroll?
May not be necessary? 
Spacebar in Browser moves one page down.
Shift+Spacebar moves up one page.

---

### Post by vasa1 on 2017-04-18
> **Habitual said:**
> May not be necessary? 
Spacebar in Browser moves one page down.
Shift+Spacebar moves up one page.
OP seems to want to use the mouse but there's page up and page down and arrow up and arrow down as well :)

---

