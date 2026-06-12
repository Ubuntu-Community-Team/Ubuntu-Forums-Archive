---
title: "(gtk theming) Change coloring of lxpanel workspace switcher only?"
date: 2016-07-07
forum: General Help
---

### Post by &amp;KyT$0P# on 2016-07-07
How to change the coloring of the lxpanel workspace switcher, but *only* the workspace switcher?  I'm using a slightly modified version of the Greybird theme.

Some screenshots - selected workspace is on the left, unselected on the right.

This is what it looks like: [screenshot deleted]
On my monitor that's really hard to distinguish, so I'd like to make it look more like this: [screenshot deleted]

(I see some code for re-coloring XFCE's workspace switcher, but that code doesn't seem to affect the lxpanel workspace switcher...)

---

### Post by vasa1 on 2016-07-09
I don't use lxpanel and I don't use workspaces and so can't answer the theming question.

But I do have a shortcut that exposes the workspaces. I wonder if it maybe useful.
```
    <keybind key="W-Menu">        # show desktops
      <action name="ShowMenu"><menu>client-list-combined-menu</menu></action>
    </keybind>
```
This is what it looks like ...

---

### Post by &amp;KyT$0P# on 2016-07-09
Thanks vasa1 that is very useful to me, although not so much for this issue...  You've solved my 16.04 workspace mess :D

---

### Post by &amp;KyT$0P# on 2016-07-13
Opened gnome-system-log and found the dates to be invisible.  Well, not quite, but I'm certain that's a side effect of changing theme...

Is there any software that can fill in the blank "[DOM Inspector]("https://addons.mozilla.org/seamonkey/addon/dom-inspector-6622/") is to SeaMonkey as ________ is to GTK2/GTK3"?

---

### Post by vasa1 on 2016-07-15
[https://wiki.gnome.org/Projects/GTK%2B/Inspector](https://wiki.gnome.org/Projects/GTK%2B/Inspector) ?

---

### Post by &amp;KyT$0P# on 2016-07-15
That looks promising, thanks, but it's too new for Lubuntu 14.04 :( So I grabbed the project it linked, gtkparasite, and successfully built it for GTK 2.  However, when I try to use it following the instructions on its website:
```
export GTK_MODULES='gtkparasite'
lxpanel --profile Lubuntu
```
lxpanel runs without gtkparasite and I get this error:
```
Gtk-Message: Failed to load module "gtkparasite"
```

How to make gtkparasite module visible to GTK 2 application?

---

### Post by &amp;KyT$0P# on 2016-07-28
On the other hand, gtkparasite does work with gtk 3 apps, meaning gnome-system-log :D
However, it doesn't install to the right location, I "fixed" it like this:
```
sudo mv -v /usr/local/lib/gtk-3.0/modules /usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0
```

Of course, there's probably a way to just change the install location at build time, but so far not noticing any issues.

Now to figure out how to inspect the dates in gnome-system-log... :-k

---

### Post by &amp;KyT$0P# on 2016-07-28
Solved the gnome-system-log issue a different way.  The Lubuntu-dark-panel theme has a file called "gnome-system-log.css"
```
/usr/share/themes/Lubuntu-dark-panel/gtk-3.0/apps/gnome-system-log.css
```

So I copied it in my theme's apps directory, and added this line to gtk.css:
```
@import url("apps/gnome-system-log.css");
```

Now the dates are readable again  :KS


But I couldn't get gtkparasite to go deeper than showing the GtkTextView, yet based on playing with the themes and seeing the contents of the gnome-system-log.css, there looks to be more levels to go down.  How did the Lubuntu-dark-panel people figure out what to put in that gnome-system-log.css file?

---

### Post by &amp;KyT$0P# on 2016-08-11
Solution is to add this to apps/xfce-panel.rc
```
# for lxpanel workspace switcher
widget "*pager*"                        style "workspace-switcher"

```

Now the workspace switcher can be themed like the Greybird devs intended, but that's not quite enough - the lxpanel workspace switcher apparently does some styling of its own (it darkens some theme colors in its backgrounds).  We can edit the [FONT=Courier New]style "workspace-switcher"[/FONT] part of the same file to dial up the theme color's brightness a bit, so it would looks like this:
```
style "workspace-switcher" = "theme-panel"
{
        bg[SELECTED]    = shade (1.02, @selected_bg_color)
}

```

Problem solved, for me at least.  Thanks again to all who helped.  :KS

---

