---
title: "Annoying gnome panel handlers"
date: 2006-10-26
forum: General Help
---

### Post by hexion on 2006-10-26
In dapper I find how to delete the ugly and annoying gnome-panel handlers, or how to make that files transparent with gimp... but since edgy I don't know where are those files and how can make them invisible.

Maybe you don't understand me... please, look at my screenshot and I think it will be clear then ;)

I only was able to change the distributor-logo.

Please, any help to do so?

---

### Post by beerfan on 2006-10-26
Do they change if you use a different theme? If so then I'd look inside the theme for them. If they don't change...perhaps they're hardcoded into gnome? Just guessing...

---

### Post by hexion on 2006-10-26
I tried everything.

In dapper (gnome 2.14) is was that way, and I "hacked" one theme to make the trick. Worked... but same theme in edgy looks that ugly.

In gnome 2.16 they use SVG files... but I couldn't find the files for the handlers :(

---

### Post by beerfan on 2006-10-26
> **hexion said:**
> I tried everything.

In dapper (gnome 2.14) is was that way, and I "hacked" one theme to make the trick. Worked... but same theme in edgy looks that ugly.

In gnome 2.16 they use SVG files... but I couldn't find the files for the handlers :(

That's the problem then. SVG is an xml format for vector graphics so they could be specified in separate files, or in the code, or anywhere. You'd have to ask in the right place or go digging through the code.

---

### Post by Albi on 2006-10-28
Hi, I'm having the same problem.  Can you please clarify how to fix this?

---

### Post by hexion on 2006-10-29
> **Albi said:**
> Hi, I'm having the same problem.  Can you please clarify how to fix this?

As soon as somebody tells me :(

---

### Post by _simon_ on 2006-10-30
I was having the same kind of issue, I have black panels with grey handles which were ugly.

I've now made the handles black so they can't be seen against my black panels.

See the "HANDLES" section here:

[http://gnomethemes.org/forum/index.php?topic=67.0](http://gnomethemes.org/forum/index.php?topic=67.0)

---

### Post by hexion on 2006-10-30
> **_simon_ said:**
> I was having the same kind of issue, I have black panels with grey handles which were ugly.

I've now made the handles black so they can't be seen against my black panels.

See the "HANDLES" section here:

[http://gnomethemes.org/forum/index.php?topic=67.0](http://gnomethemes.org/forum/index.php?topic=67.0)

It doesn't work for me :(

Can you post your .gtkrc-2.0 file? are you using edgy? screenshot?

Thanks

---

### Post by _simon_ on 2006-10-31
> **hexion said:**
> It doesn't work for me :(

Can you post your .gtkrc-2.0 file? are you using edgy? screenshot?

Thanks

Hi,

Yes I'm using Edgy and I'm using clearlooks so I added the handle bit to the bottom, here's the full contents:

```

style "clearlooks-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15
  
  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 27
#  GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
#  GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
#  GtkScrollbar   ::has-secondary-forward-stepper = 1
#  GtkScrollbar   ::has-secondary-backward-stepper = 1

  GtkButton      ::child-displacement-x = 1
  GtkButton      ::child-displacement-y = 1

  WnckTasklist   ::fade-overlay-rect = 0

  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#000000" # black
  fg[PRELIGHT]      = "#000000" # black
  fg[SELECTED]      = "#ffffff" # white 
  fg[ACTIVE]        = "#000000" # black
  fg[INSENSITIVE]   = "#b5b3ac" # dark beige

  bg[NORMAL]        = "#ede9e3"
  bg[PRELIGHT]      = "#f9f7f3" # very light beige
  bg[SELECTED]        = "#5598d7" # deepsky
  bg[INSENSITIVE]   = "#efebe5" # beige
  bg[ACTIVE]        = "#dcd4c9" #"#d7d3ca" # dark beige

  base[NORMAL]      = "#ffffff" # white 
  base[PRELIGHT]    = "#5f8ec4" # dark beige
  base[ACTIVE]      = "#a69f91" # darker deepsky
  base[SELECTED]    = "#5598d7" # deepsky
  base[INSENSITIVE] = "#e8e5de" # beige

  text[NORMAL]      = "#000000" # black
  text[PRELIGHT]    = "#000000" # black
  text[ACTIVE]      = "#ffffff" # white
  text[SELECTED]    = "#ffffff" # white
  text[INSENSITIVE] = "#b5b3ac" # dark beige

  engine "clearlooks" 
  {
    #scrollbar_color   = "#76acde"
    menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle = 1       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  = 1       # 0 = candy bar, 1 = fancy candy bar, 2 = flat
    animation         = FALSE
  }
}


style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-wider" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = "#f6f4f1"
  bg[INSENSITIVE]   = "#f2efeb"
  bg[PRELIGHT]      = "#faf9f8"
}

style "clearlooks-notebook" = "clearlooks-wide"
{
  bg[NORMAL]      = "#efebe5"
  bg[INSENSITIVE] = "#efebe5"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 1
  bg[NORMAL] = "#f9f7f3"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
    fg[PRELIGHT] = "#000000"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = "#ffffff"
  text[PRELIGHT] = "#ffffff"
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
  xthickness = 1
  ythickness = 1
  fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "clearlooks-menubar" = "blackrock-default"
{
  bg[NORMAL]   = "#bacedb"
}
    

# widget styles
class "GtkWidget" style "clearlooks-default"
class "GtkButton" style "clearlooks-button"
class "GtkScale"  style "clearlooks-button"
class "GtkCombo"  style "clearlooks-button"
class "GtkRange"  style "clearlooks-wide"
class "GtkFrame"  style "clearlooks-wide"
class "GtkMenu"   style "clearlooks-menu"
class "GtkEntry"  style "clearlooks-wider"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
 
#class "GtkMenuBar" style "clearlooks-menubar"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
#widget_class "*.GtkMenuBar.*MenuItem.*" style "clearlooks-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"

style "handle"
{
  bg[NORMAL] = "#000000"
}
class "PanelAppletFrame" style "handle"

```Everything else apart from the handle bit is standard.

As you can see from my screenshot, the handles cannot be seen because they are black.


[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/th_Screenshot.jpg[/IMG]]("http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshot.jpg")

---

### Post by hexion on 2006-10-31
I did it!!!

It wasn't a problem with my theme, I had to install these packets (I realized because I had a gtk-warning each time I started gedit app)

sudo aptitude install gtk2-engines
sudo aptitude install gtk2-engines-pixbuf


The error I had was this:
(gedit:9788 ): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,


Thanks _simon_ for your help ;)  (BTW, I like your wallpaper)

**EDIT:** For if someone wants my themes, I've attached them. They are just modifications of other themes (linsta for gtk, and a vista-based one for emerald)

---

