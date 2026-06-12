---
title: "GTK 2.x themes"
date: 2008-03-16
forum: General Help
---

### Post by Hazed on 2008-03-16
I am running an Emerald Theme called Aero-Aqua Dark (Righty), and it is suggested to use it with the Clearlooks Human Dark GTK 2.x theme.

So I downloaded it from Gnome-Look and installed it, then tried to change to it and I just have a basic theme. Everything is blocky, it looks like it couldn't apply the theme correctly and so gave me a basic default theme instead.

I tried using Terminal to do a

```
emerald --replace
```

to see if that fixed it, but when I do, i get this error message:

```
/home/tom/.themes/Clearlooks Human Dark/gtk-2.0/gtkrc:75: error: unexpected identifier `reliefstyle', expected character `}'
```

Anyone have any ideas?

---

### Post by banewman on 2008-03-16
In the file 
/home/tom/.themes/Clearlooks Human Dark/gtk-2.0/gtkrc  - line 75
there is a } missing going from the error.
Can you paste the gtkrc file?
:)

---

### Post by Ub1476 on 2008-03-16
It  might be that you do not have the gtk-engines the theme requires. Search for "pixmap" and "clearlooks" in Synaptic. I also suppose you extracted the downloaded .tar.gz archive and made a tar.gz archive of the "Clearlooks Human Dark" folder, then navigate to this through theme installer?

---

### Post by Hazed on 2008-03-16
Sure:

# Set GtkSettings color scheme property.
# This can be overriden (via an xsetting) with eg. the gnome-appearance-properties.
gtk_color_scheme = "fg_color:#D4D4D4\nbg_color:#333333\nbase_color:#474747\ntext_color:#D4D4D4\nselected_bg_color:#fc9a58\nselected_base_color:#edb35a\nselected_fg_color:#fff"
gtk-icon-sizes = "panel-menu=24,24"

style "clearlooks-default"
{
	########
	# Style Properties
	########
	GtkButton      ::child-displacement-x = 0
	GtkButton      ::child-displacement-y = 1
	GtkButton      ::default-border       = { 0, 0, 0, 0 }
	GtkCheckButton ::indicator-size       = 14

	GtkPaned       ::handle-size          = 6

	GtkRange       ::trough-border        = 0
	GtkRange       ::slider-width         = 15
	GtkRange       ::stepper-size         = 15

	GtkScale       ::slider-length        = 31
	GtkScale       ::trough-side-details  = 1
	GtkScrollbar   ::min-slider-length    = 35
        GtkScrolledWindow ::scrollbar-spacing  = 2

	GtkMenuBar     ::internal-padding     = 0
	GtkExpander    ::expander-size        = 16
	GtkToolbar     ::internal-padding     = 1
	GtkTreeView    ::expander-size        = 14
	GtkTreeView    ::vertical-separator   = 0

	GtkMenu        ::horizontal-padding   = 0
	GtkMenu        ::vertical-padding     = 0
	GtkTreeView::odd_row_color = mix(0.98, shade (0.93,@base_color), @selected_bg_color)
	GtkEntry::cursor_color = @text_color
	GtkTextView::cursor_color = @text_color

	# Glow the tasklist by changing the color, instead of overlaying it with a rectangle
	WnckTasklist   ::fade-overlay-rect    = 0

	xthickness = 1
	ythickness = 1


  fg[NORMAL]       	=  @fg_color
  fg[ACTIVE]       	=  @fg_color
  fg[PRELIGHT]     	=  @selected_fg_color
  fg[SELECTED]     	=  @selected_fg_color
  fg[INSENSITIVE]  	=  "#575757"

  bg[NORMAL]       	=  @bg_color
  bg[ACTIVE]        	=  shade (1.025,@bg_color)
  bg[PRELIGHT]     	=  shade (1.10,@bg_color)
  bg[SELECTED]	    	=  @selected_bg_color
  bg[INSENSITIVE]  	=  shade (1.025,@bg_color) 

  base[NORMAL]     	=  @base_color
  base[ACTIVE]     	=  shade (0.65,@base_color) 
  base[PRELIGHT]   	=  @base_color
  base[SELECTED]	=  @selected_base_color
  base[INSENSITIVE]	=  shade (1.025,@bg_color)

  text[NORMAL]     	=  @text_color
  text[ACTIVE]		=  shade (0.65,@text_color)
  text[PRELIGHT]   	=  @selected_fg_color
  text[SELECTED]   	=  @selected_fg_color
  text[INSENSITIVE]	=  shade (1.70,@bg_color)

	engine "clearlooks" 
	{
		#Comment out scrollbar_color and uncomment colorize_scrollbar for colorful scrollbars.
		#colorize_scrollbar = TRUE
		scrollbar_color = "#454545"
		reliefstyle       = 1
		menubarstyle      = 2     # 0 = flat, 1 = sunken, 2 = flat gradient
		toolbarstyle      = 1      # 0 = flat, 1 = enable effects
		animation         = TRUE
		style             = GUMMY
		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "clearlooks-wide"
{
	xthickness = 2
	ythickness = 2
}

style "clearlooks-wider"
{
	xthickness = 3
	ythickness = 3
}

style "clearlooks-button"
{
	xthickness   = 3
	ythickness   = 3

	bg[NORMAL]   =  shade (1.35,@bg_color)
	bg[ACTIVE]   =  shade (0.85,@bg_color)
	bg[PRELIGHT] =  mix(0.95, shade (1.35,@bg_color), @selected_bg_color)

}

style "clearlooks-notebook-bg"
{
	bg[NORMAL] =  shade (1.15,@bg_color)
	fg[ACTIVE] =  shade (0.6,@fg_color)
	bg[ACTIVE] =  shade (1.15,@bg_color)
	bg[SELECTED] =  shade (0.5,@selected_bg_color)
}

style "clearlooks-notebook" = "clearlooks-notebook-bg"
{
	xthickness = 3
	ythickness = 3
}

style "clearlooks-tasklist"
{
	xthickness = 5
	ythickness = 3
}

style "clearlooks-menu"
{
	xthickness = 0
	ythickness = 0

	engine "clearlooks" {
		radius = 0.0
	}
}

style "clearlooks-menu-item"
{
	xthickness = 2
	ythickness = 3
	bg[SELECTED] = @selected_bg_color
	fg[PRELIGHT] 	 =  @selected_fg_color
	text[PRELIGHT] =  @selected_fg_color
}

style "clearlooks-separator-menu-item"
{
	GtkSeparatorMenuItem::horizontal-padding = 0
	GtkWidget::wide-separators = 1
	GtkWidget::separator-width = 1
	GtkWidget::separator-height = 5
	xthickness = 1
	ythickness = 0
}

style "clearlooks-treeview"
{
	engine "clearlooks" {
		hint = "treeview"
	}
}

# Based on the default style so that the colors from the button
# style are overriden again.
style "clearlooks-treeview-header" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 1
	bg[NORMAL]   =  shade (1.1,@bg_color)
	bg[PRELIGHT] = shade (1.75,@bg_color)
	bg[ACTIVE]   =  mix(0.65, shade (1.1,@bg_color), @selected_bg_color)
	engine "clearlooks" {
		hint = "treeview-header"
	}
}

style "clearlooks-frame-title"
{
	fg[NORMAL] = lighter (@fg_color)
}

style "clearlooks-tooltips"
{
	xthickness = 4
	ythickness = 4

	bg[NORMAL]   =  @selected_bg_color
	fg[NORMAL]   =  @selected_fg_color
}

style "metacity-frame" = "clearlooks-default"
{
	bg[SELECTED] = @bg_color

}

style "clearlooks-progressbar"
{
	xthickness = 1
	ythickness = 1

	bg[NORMAL] =  shade (1.4,@bg_color)
	fg[PRELIGHT] = @selected_fg_color

	engine "clearlooks" {
		radius = 1.0
		hint	= "progressbar"
	}
}

style "clearlooks-statusbar"
{
	engine "clearlooks"
	{
		hint	= "statusbar"
	}
}

style "clearlooks-comboboxentry"
{
	# NOTE:
	# If you set the appears-as-list option on comboboxes in the theme
	# you should set this hint on the combobox instead.
	engine "clearlooks"
	{
		hint	= "comboboxentry"
	}
}

style "clearlooks-spinbutton"
{
	engine "clearlooks"
	{
		hint	= "spinbutton"
	}
}

style "clearlooks-scale"
{
	bg[NORMAL]   =  shade (1.35,@bg_color)
	bg[PRELIGHT]   =  shade (1.35,@bg_color)
	engine "clearlooks"
	{
		hint	= "scale"
	}
}

style "clearlooks-hscale"
{
	engine "clearlooks"
	{
		hint	= "hscale"
	}
}

style "clearlooks-vscale"
{
	engine "clearlooks"
	{
		hint	= "vscale"
	}
}

style "clearlooks-scrollbar"
{
	engine "clearlooks"
	{
		hint	= "scrollbar"
	}
}

style "clearlooks-hscrollbar"
{
	engine "clearlooks"
	{
		hint	= "hscrollbar"
	}
}

style "clearlooks-vscrollbar"
{
	engine "clearlooks"
	{
		hint	= "vscrollbar"
	}
}

style "clearlooks-menubar"
{
	engine "clearlooks"
	{
		hint	= "menubar"
	}
}

style "clearlooks-nautilus-location"
{
	bg[NORMAL] = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}

#########################################
# Matches
#########################################

# Clearlooks default style is applied to every widget
class "GtkWidget"    style "clearlooks-default"

# Increase the x/ythickness in some widgets
class "GtkToolbar"   style "clearlooks-default" 
class "GtkRange"     style "clearlooks-wide"
class "GtkFrame"     style "clearlooks-wide"
class "GtkSeparator" style "clearlooks-wide"
class "GtkEntry"     style "clearlooks-wider"
class "MetaFrames"   style "metacity-frame"
class "GtkWindow"    style "metacity-frame"

class "GtkSpinButton"  style "clearlooks-spinbutton"
class "GtkScale"       style "clearlooks-scale"
class "GtkVScale"      style "clearlooks-vscale"
class "GtkHScale"      style "clearlooks-hscale"
class "GtkScrollbar"   style "clearlooks-scrollbar"
class "GtkVScrollbar"  style "clearlooks-vscrollbar"
class "GtkHScrollbar"  style "clearlooks-hscrollbar"

# General matching following, the order is choosen so that the right styles override each other
# eg. progressbar needs to be more important then the menu match.

# This is not perfect, it could be done better
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"     style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>"  style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkLayout>"       style "clearlooks-notebook-bg"

widget_class "*<GtkButton>"      style "clearlooks-button"
widget_class "*<GtkNotebook>"    style "clearlooks-notebook"
widget_class "*<GtkStatusbar>*"  style "clearlooks-statusbar"

widget_class "*<GtkComboBoxEntry>*" style "clearlooks-comboboxentry"
widget_class "*<GtkCombo>*"         style "clearlooks-comboboxentry"

widget_class "*<GtkMenuBar>*"           style "clearlooks-menubar"
widget_class "*<GtkMenu>*"              style "clearlooks-menu"
widget_class "*<GtkMenuItem>*"          style "clearlooks-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>" style "clearlooks-frame-title"
widget_class "*.<GtkTreeView>*"        style "clearlooks-treeview"

widget_class "*<GtkProgressBar>"       style "clearlooks-progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" style "clearlooks-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"    style "clearlooks-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"     style "clearlooks-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"    style "clearlooks-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"    style "clearlooks-treeview-header"
widget_class "*.ETree.ECanvas"    style "clearlooks-treeview-header"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" style "clearlooks-tooltips"

###################################################
# Special cases and work arounds
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "clearlooks-nautilus-location"

# Work around for [http://bugzilla.gnome.org/show_bug.cgi?id=382646](http://bugzilla.gnome.org/show_bug.cgi?id=382646)
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
style "clearlooks-combobox-text-color-workaround"
{
	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = shade (1.70,@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>"   style "clearlooks-combobox-text-color-workaround"

# Work around the evolution "New" button bug by making the toolbar flat.
# [http://bugzilla.gnome.org/show_bug.cgi?id=446953](http://bugzilla.gnome.org/show_bug.cgi?id=446953)
# Maybe remove this workaround in unstable releases.
style "clearlooks-evo-new-button-workaround"
{

	engine "clearlooks"
	{
		toolbarstyle = 0
	}
}
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "clearlooks-evo-new-button-workaround"

---

### Post by Hazed on 2008-03-16
I did a search in Synaptics for Clearlooks and found a theme called Darklooks. Which, I believe, is the same theme as Clearlooks Human Dark. And it works :)

Thanks!

---

