---
title: "Need help changing menu text colour of a theme"
date: 2008-06-15
forum: General Help
---

### Post by Allegretto on 2008-06-15
I've been using a theme I found on GNOME-Look called simply 'Darker theme', and in general it's the best theme I've ever used. Unfortunately there's an odd design choice where the text in drop-down and right-click menus is barely visible (as per the screenshot attached), and I'm trying to change it so that it's white.

I have absoloutely no idea when it comes to creating themes, but I've done some tinkering and think the option must be somewhere in the 'gtkrc' file in the theme's folder. I've changed various options in there to #ffffff and it's changed the colour of various pieces of text in the GUI to white when I log in and out, but not the one I want.

I did manage to change the menu text to white using the GNOME Color Chooser application, but unfortunately that also changed a lot of other text to white as well, making it unreadable.

So, uh, yeah, does anyone know where the option is to edit this particular text's colour? This is the full gtkrc file... maybe it is in there and I've overlooked it.

```
style "clearlooks-default"
{
  GtkButton::default_border = { 0, 0, 0, 0 }
  GtkButton::default_outside_border = { 0, 0, 0, 0 }
  GtkRange::trough_border = 0
  GtkWidget::focus_padding = 1
  GtkPaned::handle_size = 2
  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15 # toolbar arrows
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 12
  GtkMenuBar::internal-padding = 0
  GtkTreeView::expander_size = 14
  GtkTreeView::odd_row_color = "#ffffff"
  GtkExpander::expander_size = 16
  GtkTreeView::odd_row_color = "#F2F2F2"
  GtkTreeView::even_row_color = "#fefefe"

  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#505050" # very dark brown
  fg[PRELIGHT]      = "#505050" # text on buttons (hover)
  fg[ACTIVE]        = "#505050" # text on unfocused tabs
  fg[SELECTED]      = "#ffffff" # selected text on lists
  fg[INSENSITIVE]   = "#b1b1b1" # greyed "unused" text

  bg[NORMAL]		= "#ececec" # entire background
  bg[PRELIGHT]		= "#f6f6f6" # button prelights
  bg[ACTIVE]		= "#e5e5e5" # selected taskbar items
  bg[SELECTED]		= "#686868" # ???
  bg[INSENSITIVE]	= "#e2e2e2" # greyed buttons

  base[NORMAL]		= "#ffffff" # window background
  base[PRELIGHT]	= "#000000" # menubar outline colour
  base[ACTIVE]		= "#686868" # selected item background (out of focus)
  base[SELECTED]	= "#686868" # selected hilight,tab/slider background, & menu stripe
  base[INSENSITIVE]	= "#e0e0e0" # greyed sliders

  text[NORMAL]		= "#505050" # text in general
  text[PRELIGHT]	= "#505050" # hover text (on buttons)
  text[ACTIVE]		= "#ffffff" # greyed text out of use (on highlight)
  text[SELECTED]	= "#ffffff" # selected text (on highlight)
  text[INSENSITIVE]	= "#b1b1b1" # greyed text

  engine "clearlooks" 
  {
    contrast = 1.0
    menubarstyle      = 0       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle = 0       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  = 1       # 0 = candy bar, 1 = flat 	
  }
}


style "clearlooks-progressbar" = "clearlooks-default"
{
  fg[PRELIGHT] = "#ffffff"
  xthickness = 1
  ythickness = 1

}

style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-button" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-notebook" = "clearlooks-wide"
{
  bg[NORMAL] = "#e2e2e2" # inner window background colour
  bg[ACTIVE] = "#d4d4d4" # out of focus tabs
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
  bg[NORMAL] = "#222222"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = "#ffffff"
  text[PRELIGHT] = "#ffffff"
  text[NORMAL]	= "#999999" 
  fg[NORMAL] = "#656565"
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

style "clearlooks-panel" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-combo" = "clearlooks-default"
{
  xthickness = 1
  ythickness = 2
}

style "clearlooks-panel" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
  fg[NORMAL]  			= "#ffffff"
  fg[PRELIGHT]  		= "#ffffff"
  text[NORMAL]			= "#ffffff"
  text[PRELIGHT]		= "#ffffff"
  text[ACTIVE]			= "#ffffff"
  text[SELECTED]		= "#ffffff"
  text[INSENSITIVE]		= "#ffffff"
}

style "panel-text"
{
fg[NORMAL]			= "#ffffff"
fg[PRELIGHT]  			= "#ffffff"
text[NORMAL]			= "#ffffff"
text[PRELIGHT]			= "#ffffff"
text[ACTIVE]			= "#ffffff"
text[SELECTED]			= "#ffffff"
text[INSENSITIVE]		= "#ffffff"
}

style "metacity-frame"
{
  # Normal base color
  bg[NORMAL]  = "#444444"

  # Unfocused title background color
  bg[INSENSITIVE]  =  "#444444"

  # Unfocused title text color
  fg[INSENSITIVE]  = "#dddddd"

  # Focused icon color
  #fg[NORMAL]  = { 0.2, 0.2, 0.2 }

  # Focused title background color
  bg[SELECTED]  = "#222222"

  # Focused title text color
  fg[SELECTED]  = "#ffffff"
}

# widget styles
class "GtkWidget" style "clearlooks-default"
class "GtkButton" style "clearlooks-button"
class "GtkCombo"  style "clearlooks-button"
class "GtkRange"  style "clearlooks-wide"
class "GtkFrame"  style "clearlooks-wide"
class "GtkMenu"   style "clearlooks-menu"
class "GtkEntry"  style "clearlooks-button"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkStatusbar"   style "clearlooks-wide"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"

class "MetaFrames" style "metacity-frame"
widget_class "*MenuItem.*" style "clearlooks-menu-item"

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

# panel stuff
widget "*PanelWidget*" style "panel-text"
widget "*PanelApplet*" style "panel-text"

include "panel.rc"
```

Thanks.

---

### Post by rainwalker on 2008-06-15
Try installing the app Gnome Color Chooser from Synaptic. It lets you tweak tons of colors, not just the color of text in menus.

---

### Post by Ampersand. on 2009-02-17
can you use this app to change the background color of the drop menus?

---

### Post by handy on 2009-02-17
I use Gcolor2, it allows you to click on a colour with you mouse & it gives you the hex colour code for it, amongst other things.

I wouldn't be able to tweak my gtkrc file without it, or something like it.

If you seriously want to learn about this stuff, here is a good place to start:

*_[http://www.orford.org/gtk/](http://www.orford.org/gtk/)_*

---

