---
title: "How to change color of text cursor??"
date: 2007-06-22
forum: General Help
---

### Post by herbster on 2007-06-22
Here's my gtkrc, I'm using a theme called Murrina-GrigioProfondo which I have altered and like, but I would like to make the background in gedit black with white text, however, that makes the text cursor disappear so I don't know where I am in the document (same with renaming files in file browser windows, cursor disappears).

There is nothing in gedit's preferences. Here's my gtkrc:

```
# Murrina-GrigioProfondo v. 1.1
# created by Alessandro Spadavecchia


style "theme-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }

  GtkRange       ::trough_border     = 0 # parametri barra di scorrimento
  GtkRange       ::slider_width      = 16
  GtkRange       ::stepper_size      = 18

  GtkScrollbar   ::min_slider_length = 30
 
  GtkCheckButton ::indicator_size    = 16

  GtkMenuBar     ::internal-padding  = 2
  GtkMenuBar     ::shadow-type       = GTK_SHADOW_NONE

  GtkCheckMenuItem ::indicator-size  = 16
  
  GtkComboBox    ::appears-as-list   = FALSE
  GtkComboBox    ::arrow-size        = 7
  GtkComboBox    ::shadow-type       = GTK_SHADOW_OUT

  GtkDialog   ::action-area-border   = 4
  GtkDialog   ::button-spacing       = 6
  GtkDialog   ::content-area-border  = 3

  GtkEntry       ::inner-border      = { 1, 1, 4, 4 } #sinistra, destra, sopra, sotto 
  
  GtkTreeView    ::expander_size     = 14
  
  GtkExpander    ::expander_size     = 14
  
  GtkScale       ::slider-length     = 24
 
  GtkToolbar     ::internal-padding  = 0
  GtkToolbar     ::shadow_type       = GTK_SHADOW_NONE
  GtkToolbar     ::button-relief     = GTK_RELIEF_NONE

  GtkFrame       ::shadow_type       = GTK_SHADOW_NONE

  GtkNotebook    ::tab-curvature     = 6
  GtkNotebook    ::tab-overlap       = 4
  GtkPaned       ::handle_size       = 8
  
  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#ffffff" # testo principale
  fg[PRELIGHT]      = "#ffffff" # testo area illuminata
  fg[ACTIVE]        = "#ffffff" # testo zone attive was FFAE6B
  fg[SELECTED]      = "#F5FF8C" # testo zone selezionate
  fg[INSENSITIVE]   = "#111111" # zona non attivabile

  bg[NORMAL]        = "#333333" # fondo
  bg[PRELIGHT]      = "#cf7a00" # tasti e altri selettori illuminati
  bg[ACTIVE]        = "#000000" # zona attiva was 282828
  bg[SELECTED]      = "#FFBA6B" # aree di inserimento selezionate - anche testo 
  bg[INSENSITIVE]   = "#4e4e4e" # 
	
  base[NORMAL]      = "#444341" # sfondi aree testo, caselle, ecc.
  base[PRELIGHT]    = "#D67922" # "#8CB6FF" # 
  base[ACTIVE]      = "#D67922" # elementi selezionati delle liste
  base[SELECTED]    = "#A67044" # 
  base[INSENSITIVE] = "#696969" # 
	
  text[NORMAL]      = "#ffffff" # 
  text[PRELIGHT]    = "#ffffff" # 
  text[ACTIVE]      = "#ffffff" # 
  text[SELECTED]    = "#ffffff" # 
  text[INSENSITIVE] = "#8c8c8c" #


engine "murrine" 
  {
    scrollbarstyle = 2 # Enable or disable circles, stripes, handles
    listviewstyle = 0 # 0 = nothing, 1 = dotted
    scrollbar_color = "#cf7a00"
    hilight_ratio = 1.05
    gradients = TRUE
    contrast = 1.0
    glazestyle = 1 # 0 = flat hilight, 1 = curved hilight, 2 = concave style, 3 = top curved hilight, 4 = beryl style
    menustyle = 1
    menubarstyle = 0 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
    menubaritemstyle = 1 # 0 = menuitem look, 1 = button look
    menuitemstyle = 2 # 0 = flat, 1 = glassy, 2 = striped
    listviewheaderstyle = 2 # 0 = flat, 1 = glassy, 2 = raised
    roundness = 6 # 0 = squared, 1 = old default, more will increase roundness
    animation = TRUE # FALSE = disabled, TRUE = enabled
  }
}

style "theme-wide" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-wider" = "theme-default"
{
  xthickness = 4
  ythickness = 4
}

style "theme-entry" = "theme-wider"
{
  bg[NORMAL]        = "#5c5c5c" # linee a parti per lo scroll
  bg[PRELIGHT]      = "#A67044" # mouseover scroll
}

style "theme-button" = "theme-wider"
{
  bg[NORMAL]      = "#1e1e1e"# was 1e1e1e
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]        = "#4F4F4F" # tab selezionata
  bg[ACTIVE]        = "#2E2B28" # tab inattive
  bg[SELECTED]      = "#FFE2B8" # contorno tab attiva
}

style "theme-tasklist" = "theme-default"
{
  xthickness = 5
  ythickness = 3
}

style "theme-menu" = "theme-default"
{
  xthickness = 7
  ythickness = 5
  fg[NORMAL]        = "#ffffff" # testo menu
  fg[PRELIGHT]      = "#FFC08C"
  bg[PRELIGHT]      = "#FFC08C"
  bg[NORMAL]        = "#616161" #menu separator
  fg[INSENSITIVE]   = "#4c4c4c"	
  text[INSENSITIVE] = "#4c4c4c"
  bg[INSENSITIVE]   = "#4c4c4c"	#inactive highlight arrows  
  bg[NORMAL]        = "#000000" #menu background was 2E2B28
}

style "theme-menu-item" = "theme-default"
{
  ythickness = 5
  fg[PRELIGHT]      = "#000000"
  bg[SELECTED] 	    = "#FA9732" 
  fg[NORMAL]        = "#ffffff" # testo menu
  
}

style "theme-menubar" = "theme-default"
{
   #bg[NORMAL] = "#3c3c3c"
}

style "theme-menubar-item"
{
  ythickness = 2
}

style "theme-tree" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] = "#FFDE00" 
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 7
  ythickness = 7
  bg[NORMAL]        = "#3B3B3B"
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 1
  ythickness = 1
  #bg[NORMAL]        = "#15299E" # sfondo barra di avanzamento
  bg[SELECTED]      = "#9E5515" # barra di avanzamento

}

style "theme-combo" = "theme-button"
{
  fg[NORMAL]           		= "#f3f3f3"
  fg[PRELIGHT]    		= "#f3f3f3"
  fg[ACTIVE]     		= "#f3f3f3"
  bg[NORMAL]			= "#4c4c4c"
  bg[PRELIGHT]			= "#4a4a4a"
}

style "metacity-frame"
{
  # Focused title background color
  bg[SELECTED]  = "#3a588c" 	# Selection Blue

  # Focused title text color
  fg[SELECTED]  = "#8CB6FF" 	# light blue
}

style "panelbg"
{
  xthickness = 1
  ythickness = 1
  bg[NORMAL] = "#3c3c3c"
}

style "panelnobg"
{
  bg_pixmap[NORMAL] = ""
}

# panel stuff
class "*Panel*"        style "panelbg"
class "*Notif*"        style "panelbg"
class "*Tray*"         style "panelbg"
class "*Applet*"       style "panelbg"
class "*Manager*"      style "panelbg"
class "*Netstatus*"    style "panelbg"
class "*Panel*Dialog*" style "panelnobg"

class "MetaFrames"     style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

# widget styles
class "GtkWidget"      style "theme-default"
class "GtkButton"      style "theme-button"
class "GtkScale"       style "theme-button"
class "GtkCombo"       style "theme-button"
class "GtkRange"       style "theme-wide"
class "GtkFrame"       style "theme-wide"
class "GtkMenu"        style "theme-menu"
class "GtkEntry"       style "theme-entry"
class "GtkMenuItem"    style "theme-menu-item"
class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "*MenuBar*"      style "theme-menubar"
widget_class "*MenuItem.*" style "theme-menu-item"
widget_class "*MenuBar.*"  style "theme-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "theme-combo"
widget_class "*.GtkCombo.GtkButton"    style "theme-combo"

# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "theme-tasklist"
widget "gtk-tooltips" style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "theme-tree"
widget_class "*.GtkCTree.GtkButton" style "theme-tree"
widget_class "*.GtkList.GtkButton" style "theme-tree"
widget_class "*.GtkCList.GtkButton" style "theme-tree"
widget_class "*.GtkFrame.GtkLabel" style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"
```

Any help appreciated :)

---

### Post by moore.bryan on 2007-06-23
[I]have you tried editing your ~/.Xdefaults file?  perhaps you could put two lines in as such:
```
gedit*background:black
gedit*color:white

```
don't know if that'll work, but it might be worth a shot...
[/I]

---

### Post by herbster on 2007-06-23
> **moore.bryan said:**
> [I]have you tried editing your ~/.Xdefaults file?  perhaps you could put two lines in as such:
```
gedit*background:black
gedit*color:white

```
don't know if that'll work, but it might be worth a shot...
[/I]

I don't have a ~/.Xdefaults file. I tried .xdefaults too, empty. Should I create it and put those lines in, and if so, do I logout and back in or how to activate the change?

TY!

---

### Post by moore.bryan on 2007-06-24
*you can create the file; just make sure it's ".Xdefaults" and NOT ".xdefaults," ".xDefaults," ".XDEFAULTS," or anything like that.  when you've created it, put those lines in it, log-out of your xsession (CTRL+ALT+BACKSPACE), and log back in either choosing the session from your manager or typing "startx" at the cli.*

---

### Post by dashun on 2007-09-05
How about whacking this bit of config
```

style "user-font"
{
	GtkTextView::cursor-color = "white"
	GtkEntry::cursor-color = "white"
}
widget_class "*" style "user-font"

```
or just the two lines of style somewhere in your gtkrc where apprioriate?

---

