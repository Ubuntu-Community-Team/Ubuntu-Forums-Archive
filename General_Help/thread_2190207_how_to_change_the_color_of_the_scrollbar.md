---
title: "how to change the color of the scrollbar"
date: 2013-11-26
forum: General Help
---

### Post by tomsubt on 2013-11-26
Hi,,  Can anyone help me with this I am using ubuntu 12.04 Thanks

---

### Post by ibjsb4 on 2013-11-26
I do not know if its possible to change just the scroll bar color.  I do make system wide color changes using dconf-tools (configuration editor).  You can try playing with these settings, maybe you can come up with something you like.  Also there are some programs that will not be affected by dconf color changes.

```
sudo apt-get install dconf-tools
```

[http://antecblue.wordpress.com/2011/10/17/replace-the-orange-color-in-ubuntu-11-10-active-color/](http://antecblue.wordpress.com/2011/10/17/replace-the-orange-color-in-ubuntu-11-10-active-color/)

[http://askubuntu.com/questions/172280/how-do-i-change-the-theme-and-window-border-color](http://askubuntu.com/questions/172280/how-do-i-change-the-theme-and-window-border-color)

[http://www.colorpicker.com/](http://www.colorpicker.com/)

more here

[https://www.google.com/search?client=ubuntu&channel=fs&q=change+system+colors+ubuntu+dconf&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=change+system+colors+ubuntu+dconf&ie=utf-8&oe=utf-8)

---

### Post by tomsubt on 2013-11-26
The Dconf editor screen comes up blank and I cannot type anything into it, how do I proceed? Thanks

---

### Post by ibjsb4 on 2013-11-26
Did you navagiate to gkt-color-scheme?  Click twice on it to go to edit mode (where it is blank).

---

### Post by ibjsb4 on 2013-11-26
An after thought 

If your running compiz as a window manager (I do not) that would open up many more options and would be a subject in its self.

---

### Post by tomsubt on 2013-11-26
I dont know what compiz is, sorry, but as far as >>>Did you navagiate to gkt-color-scheme?  Click twice on it to go to edit mode (where it is blank).
The configuration screen I am seeing you cannot type into it and on the left I see names like  Apps, Ca, Com, Desktop, org, system. If I click on any of them nothing happens either.
how do I navigate to the color sceme you mentioned? Thanks

---

### Post by tomsubt on 2013-11-26
Ok  I think I found it on the left I was not clicking on the arrows just the names thats why nothing was happening, I then clicked on gkt (Demo) and changed the color to Blue but it would not stay on blue kept going back to Red. Whats wrong, am I in the right section, if so how to keep it blue? Thanks

---

### Post by ibjsb4 on 2013-11-26
Gtk>demo is not the correct path.

Org>gnome>desktop>interface>gtk-colors-scheme

---

### Post by tomsubt on 2013-11-26
Ok I went to Org>gnome>desktop>interface>gtk-colors-scheme  and highlighted the gtk colors-scheme, but when clicking on it nothing happened, how to proceed? Thanks

---

### Post by ibjsb4 on 2013-11-26
I do not think you are clicking in the right spot.

[ATTACH=CONFIG]248112[/ATTACH]

EDIT:

Made a typo.  Thats LEFT click and not right click.

---

### Post by tomsubt on 2013-11-26
Ok, Thanks, I left clicked it and I believe I set it to Blue and made it default so I restarted the pc but I do not see a change anywhere, what exactly does the color change, change?

---

### Post by ibjsb4 on 2013-11-26
Please post the entry you made in dconf.

---

### Post by mc4man on 2013-11-26
> **tomsubt said:**
> Ok, Thanks, I left clicked it and I believe I set it to Blue and made it default so I restarted the pc but I do not see a change anywhere, what exactly does the color change, change?

You may have set it wrong. When I used to use that key I found using gsettings easier than editing it in dconf-editor
The overlay scrollbar color is determined in light-themes by selected_bg_color which will also change most selected items & progress bars.

So for gsettings you go (where XXXXXX is your color
```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#XXXXXX"
```
If directly editing in dconf-editor use 

```
selected_bg_color:#XXXXXX
```

Depending on color chosen sometimes the default for selected_fg_color (white) is unsuitable, though shouldn't be for blue. If wanting to change that then add to edit or command, replacing XXXXXX as desired
```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#XXXXXX;selected_fg_color:#XXXXXX"
```

Or in dconf-editor directly like - 
```
selected_bg_color:#XXXXXX;selected_fg_color:#XXXXXX
```

Some things may change immediately, others may need a log out/in

If only wanting to change the overlay scrollbars then you'll need to edit the theme itself

---

### Post by vasa1 on 2013-11-26
IIRC, *all* applications do not use the overlay scrollbars. Apps that use gtk2 may still use conventional scrollbars. So, when you make changes to overlay scrollbar settings, make sure you look at gtk3 apps such as gedit or evince or nautilus. And, as mc4man pointed out, you may need to log out and log in for changes to gtk3 apps to take effect.

If you want to get dirty by editing .css files, look in *~/.themes/your_theme/gtk-3.0/gtk-widgets.css* or */usr/themes/your_theme/gtk-3.0/gtk-widgets.css* for a section titled overlay scrollbars. Of course, you'll backup stuff for safety first.

Here's what *one* theme's overlay scrollbar section looks like:

```
/* overlay scrollbar */
OsThumb {
    color: shade(@theme_bg_color, 0.7);
}

OsThumb:selected,
OsScrollbar:selected {
    background-color: @theme_selected_bg_color;
}

OsThumb:active,
OsScrollbar:active {
    background-color: @theme_selected_bg_color;
}

OsThumb:insensitive,
OsScrollbar:insensitive {
    background-color: shade(@theme_bg_color, 0.9);
}

```

---

### Post by tomsubt on 2013-11-27
ok, I wont be on the ubuntu pc to work on it until monday after the Holiday, So I will come back here then and pick up
where we are leaving off, Thanks Guys. see you then

---

