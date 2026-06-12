---
title: "Aurora Engine Problem !"
date: 2008-05-25
forum: General Help
---

### Post by Jadephyre on 2008-05-25
okay, as the title suggests, i have a slight Problem with the Aurora Engine (Version 1.4).
I downloaded it from gnome-looks.org, extracted, compiled and so on and so forth.
All went fine and dandy with the compiling, but when i try to apply the "Ooboontoo" Theme i found [Here]("http://www.kims-area.com/?q=node/45") it looks like a plain X11 Theme.
Now i know that i need the Pixmap Engine too, and i installed it before compiling the Aurora Engine myself but even after restarting numerous times the Theme still does not display right.
Am i doing something wrong, or have I not done something that i need to do ?

I'm grateful for any help you can provide.

Oh and by the Way: The Themes that came with the Aurora Engine are working fine, that's what puzzles me most...

---

### Post by Jadephyre on 2008-05-25
anyone ???

---

### Post by ShodanjoDM on 2008-05-25
I just downloaded it and it's working fine. But I noticed that the contents of the theme's folder don't have uniform permissions. I don't know for sure if that matters though.

How about this:

Extract the theme and change the permission recursively to:

```
chmod -R 755 ooboontoo/
```

And then move the folder to your .themes or /usr/share/themes/ directory.

---

### Post by Jadephyre on 2008-05-25
thanks for the suggestion, but that didn't work either :(

i guess the Theme and the Engine just don't like me :(

---

### Post by ShodanjoDM on 2008-05-25
Ok, if you still want to try, you can use thewidgetfactory to check if there's a fault somewhere:

```
sudo aptitude install thewidgetfactory
```

then just run from the terminal:

```
twf ooboontoo
```

and see if there any errors output.

---

### Post by Jadephyre on 2008-05-25
scratch that, it did NOT display, what i saw was the theme i was using... Vision as it's called.
The rest of this Post is correct however.

When i choose the Ooboontoo Theme, and then run TWF, i get this output in the Terminal: /home/jade/.themes/ooboontoo/gtk-2.0/gtkrc:271: error: unexpected identifier `hint', expected character `}'

---

### Post by ShodanjoDM on 2008-05-26
Ok, sorry I couldn't reply sooner. 

have you installed pixbuf engine?

```
sudo aptitude install gtk2-engines-pixbuf
```

If I'm not mistaken the pixmap engine was renamed to / replaced with pixbuf engine.

---

### Post by Jadephyre on 2008-05-26
Pixbuf is installed :(

installed it together with the Pixmap Engine...

---

### Post by ShodanjoDM on 2008-05-26
Hmm... Strange...
Anyway, care to try my compiled aurora engine? I added the patch from here:

[http://www.gnome-look.org/content/show.php/Patch+for+Aurora+1.4?content=76134](http://www.gnome-look.org/content/show.php/Patch+for+Aurora+1.4?content=76134)

Checkinstall-ed, with a different version number (1.4-2). Let's see if it  works this time.

---

### Post by ShodanjoDM on 2008-05-26
> **Jadephyre said:**
> i get this output in the Terminal: /home/jade/.themes/ooboontoo/gtk-2.0/gtkrc:271: error: unexpected identifier `hint', expected character `}'

Hold on. Open the gtkrc file and look in line 271. Compare to this ooboontoo theme's gtkrc file below from my theme folder:

```

# Ubuntu Human-Clearlooks Colorscheme MOD
#
# Original Authors:
# Kenneth Wimar <kwwii@ubuntu.com>
# Conn O'Griofa <connogriofa@gmail.com>
#
# Modified by:
# Kim Kahns <post@kims-area.com>
#
# Feel free to modify and share!

include "panel.rc"
include "scrollbar.rc"

gtk_color_scheme = "fg_color:#101010\nbg_color:#E5E5E5\nbase_color:#fff\ntext_color:#1A1A1A\nselected_bg_color:#717171\nselected_fg_color:#1A1A1A\ntooltip_bg_color:#F5F5B5\ntooltip_fg_color:#000"

gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-large-toolbar=24,24" 

style "clearlooks-default"
{
	########
	# Style Properties
	########
	GtkButton      ::child-displacement-x = 1
	GtkButton      ::child-displacement-y = 1
	GtkButton      ::default-border       = { 0, 0, 0, 0 }
	GtkCheckButton ::indicator-size       = 14

	GtkPaned       ::handle-size          = 1

	GtkRange       ::trough-border        = 0
	GtkRange       ::slider-width         = 15
	GtkRange       ::stepper-size         = 15

	GtkScale       ::slider-length        = 30
	GtkScale       ::trough-side-details  = 0	# Restores sliders
	GtkScrollbar   ::min-slider-length    = 30

	GtkMenuBar     ::internal-padding     = 0
	GtkExpander    ::expander-size        = 16
	GtkToolbar     ::internal-padding     = 1
	GtkTreeView    ::expander-size        = 14
	GtkTreeView    ::vertical-separator   = 0

	# Glow the tasklist by changing the color, instead of overlaying it with a rectangle
	WnckTasklist   ::fade-overlay-rect    = 0

	xthickness = 1
	ythickness = 1

#GtkToolbar::space-style=GTK_TOOLBAR_SPACE_EMPTY
GtkToolbar::space-size = 0
#GtkWidget::wide-separators = TRUE

GtkDialog::action-area-border = 2
GtkDialog::button-spacing = 3
GtkDialog::content-area-border = 1
       GtkScrolledWindow::scrollbar-spacing = 0
        GtkScrolledWindow::scrollbars-within-bevel  = 1
GtkEntry::inner-border= { 2, 2, 2, 2 }
GtkWidget:: focus-line-width =0

GtkMenu::horizontal-padding = 0
GtkMenu::vertical-padding = 8
GtkMenu::vertical-offset = 0
GtkMenu::horizontal-offset = -1

#	GtkToolbar ::shadow-type = GTK_SHADOW_NONE
#	GtkMenuBar ::shadow-type = GTK_SHADOW_NONE


	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]	  = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (0.90, @bg_color)
	base[SELECTED]    = shade (1.55, @selected_bg_color)
	base[INSENSITIVE] = @bg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)

	engine "aurora" 
	{
	  menubarstyle    = 0 # 0 = flat, 1 = gradient, 2 = sunken
	  curvature       = 0
	  arrowsize       = 0.9 # controls combo_arrow circle size.  Diameter set by (11 + 2 * arrowsize)
	  old_arrowstyle  = FALSE #set to TRUE for original circled arrows
	  animation       = TRUE # FALSE = disabled, TRUE = enabled
	}
}

style "clearlooks-wide"
{
	bg[SELECTED]	  = @selected_bg_color
	xthickness = 2
	ythickness = 2
}

style "clearlooks-wider"
{
	bg[SELECTED]	  = @selected_bg_color
	xthickness = 3
	ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
	xthickness = 4
	ythickness = 3
	bg[NORMAL]        = shade (1.08, @bg_color)
	bg[PRELIGHT]      = shade (1.04, @bg_color)
	bg[ACTIVE]        = shade (0.92, @bg_color)
	engine "pixmap"
	{
		# Default button
		image
		{
		    function			= BOX
		    detail				= "buttondefault"
		    recolorable			= TRUE
			file            	= "Menu-Menubar/tbutton-pressed.png"
		    border				= { 7,7,7,7 }
		    stretch				= TRUE
		}
		
		# Button (mouse over)
		image
		{
			function			= BOX
		    state				= PRELIGHT
		    recolorable			= TRUE
			file            	= "Menu-Menubar/tbutton-hover.png"
		    border				= { 7,7,7,7 }
		    stretch				= TRUE
		}
		
		# Button (pressed)
		image
		{
		    function			= BOX
		    state				= ACTIVE
			file            	= "Menu-Menubar/tbutton-pressed.png"
		    border				= { 7,7,7,7 }
		    stretch				= TRUE
		}	
		
		# Button (disabled = user can't click)
		image 
		{
		    function			= BOX
		    state				= INSENSITIVE
			file            	= "Menu-Menubar/tbutton-off.png"
		    border				= { 7,7,7,7 }
		    stretch				= TRUE
		}
		
		# Button (normal)
		image 
		{
		    function			= BOX
			file            	= "Menu-Menubar/tbutton.png"	
		    border				= { 7,7,7,7 }
		    stretch				= TRUE
		}	
	}
}

style "toolbar2"		
{


	engine "pixmap"
	{
		# toolbar background
		image
		{
			function = BOX
			state = NORMAL
			file = "Menu-Menubar/toolbar2.png"
			border	= { 6, 6, 3,3}
			stretch	= TRUE
    	}
 	}
}
class "GtkToolbar"   style "toolbar2" 
class "*BonoboDockItem" style "toolbar2"
widget_class "*BonoboDockItem" style "toolbar2"

class "*HandleBox" style "toolbar2"
widget_class "*HandleBox" style "toolbar2"

class "*Toolbar" style "toolbar2"
widget_class "*Toolbar" style "toolbar2"

#widget_class "*Nautilus*Tool*GtkButton*"	style "clearlooks-button"
#widget_class "*Nautilus*Tool*GtkToggleButton*"	style "clearlooks-button"


style "pane"		
{
	bg[NORMAL]        = "#BCBCBC"
	bg[PRELIGHT]        = "#BCBCBC"
	bg[SELECTED]        = "#BCBCBC"
	engine "industrial"
	{

 	}
}
class "*Paned"   style "pane" 



style "menubar"		
{
	xthickness = 0
	ythickness = 0
	bg[NORMAL]        = shade (0.85, @selected_bg_color)
	engine "pixmap"
	{
		# Menubar background
		image
		{
			function = BOX
			state = NORMAL
			file = "Menu-Menubar/menubar.png"
			border	= { 8, 8, 8, 8}
			stretch	= TRUE
    	}
		image
		{
			function = BOX
			recolorable = TRUE
			state = PRELIGHT
			file = "Menu-Menubar/menubar-item.png"
			border = { 4, 4, 4, 4 }
			stretch = TRUE
		}
 	}
}

class "GtkMenuBar" 		        style "menubar"

style "clearlooks-notebook"
{
	xthickness = 3
	ythickness = 3
	bg[NORMAL]        = "#F1ECD1"
	#bg[NORMAL]        = shade (1.10, @bg_color)
	bg[ACTIVE]   = shade (0.88, "#F1ECD1")
	bg[SELECTED] = "#C79C37"

	engine "clearlooks" 
	{
		style              = GUMMY
		radius		   = 2.0
		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "clearlooks-tasklist" = "clearlooks-wide"
{
}

style "clearlooks-menu" = "clearlooks-wider"
{
	xthickness = 0
	ythickness = 0
	bg[NORMAL] = "#ffffff"
	engine "pixmap"
	{
		# Menu background
		image
		{
		    function 		= BOX
		    recolorable 	= TRUE
		    detail 			= "menu"
		    file 			= "Menu-Menubar/menu.png"
		    border 			= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
	}
}

style "clearlooks-menu-item" = "clearlooks-wider"
{
	fg[PRELIGHT] = "#ffffff"
	bg[PRELIGHT] = @bg_color
	bg[SELECTED] = @bg_color
	fg[NORMAL] = "#353535"

#font_name = "DejaVu Sans Book 9"

	xthickness = 4
	ythickness = 3

	engine "pixmap"
	{
		# Menuitem background (mouse over)
		image
		{	
		    function = BOX
		    recolorable = TRUE
		    file = "Menu-Menubar/menuitem.png"
		    border = { 4, 4, 4, 4 }
		    stretch = TRUE
		}
		
		# Menu separator
		image 
        {
        	function        = HLINE
	 		recolorable     = TRUE
	 		file            = "Menu-Menubar/menu-separator.png"
			border          = { 0, 0, 0, 0 }
			stretch         = TRUE
      	}
	}
}

style "clearlooks-separator-menu-item"
{
	xthickness = 0
	ythickness = 4
}

style "clearlooks-treeview"
{
	bg[SELECTED] = @selected_bg_color

	engine "clearlooks" {
		hint = "treeview"
	}
}



style "TreeView"
{
	GtkTreeView::allow-rules          = 1
	GtkTreeView::even-row-color       = @base_color
	GtkTreeView::grid-line-pattern    = "\1\1" 
	GtkTreeView::grid-line-width      = 1
	GtkTreeView::odd-row-color        = "#E4F0F7"
	GtkTreeView::tree-line-pattern    =  "\1\1" 
	GtkTreeView::tree-line-width      = 1

	bg[NORMAL]      = @bg_color
	bg[PRELIGHT]    = @bg_color
	bg[ACTIVE]      = @selected_bg_color
	bg[SELECTED]    = @selected_bg_color
	bg[INSENSITIVE] = @bg_color



	base[NORMAL]      = @base_color
	base[PRELIGHT]    = @base_color
	base[ACTIVE]      = @selected_bg_color
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @base_color

	fg[NORMAL]      = @text_color
	fg[PRELIGHT]    = "#ffffff"
	fg[ACTIVE]      = "#ffffff"
	fg[SELECTED]    = "#ffffff"
	fg[INSENSITIVE] = "#ffffff"

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = "#000"
	text[ACTIVE]      = "#ffffff"
	text[SELECTED]    = "#ffffff"
	text[INSENSITIVE] = "#c3dbff"

	engine "pixmap"
	{
		image
		{
			function = FLAT_BOX
			state    = SELECTED
			border   = {2,2,2,2}
			file     = "Tree/selected.png"
		}
	}
}


class "GtkTreeView" style "TreeView"
#class "GtkTreeView" binding "TreeView"


widget_class "*GtkCTree*" style "TreeView"
widget_class "*GtkList*" style "TreeView"
widget_class "*GtkCList*" style "TreeView"
widget_class "*.ETree.*" style "TreeView"

style "nauTreeView"
{
	
	GtkTreeView::even-row-color       = @bg_color
	GtkTreeView::odd-row-color        = @base_color
}
widget_class "*Nautilus*GtkTreeView*" style "nauTreeView"

style "nauline" = "clearlooks-default"
{

	engine "pixmap"
	{
    # Vertical spearator
    image
    {
		function		= VLINE
		recolorable		= TRUE
		file			= "Lines/line-v.png"
		border			= { 1, 1, 0, 0 }
		stretch			= TRUE
    }
    
    # Horizontal separator
    image
    {
		function		= HLINE
		recolorable		= TRUE
		file			= "Lines/line-h.png"
		border			= { 0, 0, 1, 1 }
		stretch			= TRUE
    }
	}


}
widget_class "*Nautilus*GtkToolbar*" style "nauline"

style "naupan" 
{

	engine "pixmap"
	{
    image
    {
      function			= SHADOW
      shadow			= IN
      recolorable		= FALSE
      file				= "Shadows/shadow-in.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-out.png"
       border			= { 1, 1, 1, 1 }
       stretch			= TRUE
    }

    image
    {
       function			= SHADOW
       shadow			= ETCHED_IN
       recolorable		= TRUE
       file				= "Shadows/frame1.png"				
       border			= { 2, 2, 2, 2 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= ETCHED_OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-none.png"
       border			= { 2, 2, 17, 2 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW_GAP
       recolorable		= TRUE
       file				= "Shadows/frame1.png"
       border			= { 2, 2, 2, 2 }
       stretch			= TRUE
       gap_start_file	= "Shadows/frame1.png"
       gap_start_border	= { 2, 0, 2, 0 }
       gap_end_file		= "Shadows/frame1.png"
       gap_end_border	= { 0, 2, 2, 0 }
       gap_side			= TOP
    }

	    image
	    {
		    function		= HANDLE
		    recolorable		= TRUE
		    overlay_file	= "Shadows/shadow-none.png"
		    overlay_stretch	= FALSE
		    orientation		= HORIZONTAL
	    }
	    
	    # Handle image for vertical handel
	    image
	    {
		    function		= HANDLE
		    recolorable		= TRUE
		    overlay_file	= "Shadows/shadow-none.png"
		    overlay_stretch	= FALSE
		    orientation		= VERTICAL
	    }


    }


}
widget_class "*Nautilus*GtkFrame" style "naupan"


style "entry" = "clearlooks-default"
{
	xthickness = 3
	ythickness = 3
	GtkWidget::interior_focus	= 0
	engine "pixmap"
	{
    image
    {
      function			= FOCUS
      recolorable			= TRUE
      file				= "Shadows/entry-in.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	
 image
    {
      function			= BOX
      recolorable			= TRUE
	shadow			= IN
      state				= NORMAL
      file				= "Shadows/entry.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	

image
    {
      function			= BOX
      recolorable			= TRUE
	shadow			= OUT
      state				= NORMAL
      file				= "Shadows/entry.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	

  image
   {
     function		= SHADOW
     detail			= "entry"
     shadow		= IN
     recolorable		= FALSE
     file			= "Shadows/entry.png"
     border			= { 3,3,3,3 }
     stretch		= TRUE
   }
	}

}

class "GtkEntry"           			style "entry"
class "GtkText"           			style "entry"
class "GtkTextView"           			style "entry"
class "GtkEditable"           			style "entry"
class "GtkOldEditable" 				style "entry"




style "clearlooks-treeview-header" #= "clearlooks-default"
{
	bg[SELECTED] = mix(0.50, shade (1.05,@selected_bg_color), @tooltip_bg_color)
	#bg[NORMAL] = "#ff0000"
	#text[PRELIGHT] = "#ffffff"
	#fg[PRELIGHT] = "#ffffff"
	xthickness = 5
	ythickness = 1
	engine "pixmap" 
	{
		# Normal
    	image
      	{
        	function        = BOX
			recolorable     = TRUE
			shadow          = OUT
			state			= NORMAL
			file            = "ListHeaders/list_header.png"
			border          = { 2, 2, 2, 2 }
			stretch         = TRUE
   		}

		# Prelight / Mouseover
    	image
   		{
       		function        = BOX
			recolorable     = TRUE
			state			= PRELIGHT
			file            = "ListHeaders/list_header-prelight.png"
			border          = { 2, 2, 2, 2 }
			stretch         = TRUE
   		}

		# Active
		image
      	{
        	function       	= BOX
			recolorable     = TRUE
			state			= ACTIVE
			file			= "ListHeaders/list_header-pressed.png"
			border          = { 2, 2, 2, 2 }
			stretch         = TRUE
   		}

		# Selected
		image
   		{
       		function        = BOX
			recolorable     = TRUE
			state			= SELECTED
			file			= "ListHeaders/list_header-prelight.png"
			border          = { 2, 2, 2, 2 }
			stretch         = TRUE
   		}
  	}
}

style "toolbuttons" = "default"

{

	xthickness = 4
	ythickness = 3

	GtkWidget::focus_padding = 2

	engine "pixmap" 
	{
		# Toolbar button
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state				= NORMAL
			file            	= "Menu-Menubar/tbuttontb.png"
		    border				= { 7,7,7,7 }
			stretch         	= TRUE
		}
		
		# Toolbar button (mouse over)
		image
		{
			function      		= BOX
			recolorable    		= TRUE
			state				= PRELIGHT
			file            	= "Menu-Menubar/tbutton-hover.png"
		    border				= { 7,7,7,7 }
			stretch       		= TRUE
		}



		# Toolbar button (clicked)
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state				= ACTIVE
			file            	= "Menu-Menubar/tbutton-pressed.png"
		    border				= { 7,7,7,7 }
			stretch         	= TRUE
		}  
		
		# Toolbar button (disabled)
		image
		{
			function      		= BOX
			recolorable    		= TRUE
			state				= INSENSITIVE
			file            	= "Menu-Menubar/tbutton-off.png"
		    border				= { 7,7,7,7 }
			stretch       		= TRUE
		}  
	}
}

widget "*Tool*GtkToggleButton" style "toolbuttons"
widget "*Tool*GtkButton" style "toolbuttons"


style "spinbutton" = "entry"
{

	xthickness = 4
	ythickness = 3

  	engine "pixmap"
  	{
  		# Arrow
    	image
    	{
     		function	= ARROW
    	}

		# Up
		image
		{
		    function		= BOX
		    state 			= NORMAL
		    detail			= "spinbutton_up"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-up.png"
		    overlay_stretch	= FALSE
		}

		# Up (mouse over)
		image
		{
		    function		= BOX
		    state 			= PRELIGHT
		    detail			= "spinbutton_up"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-up-prelight.png"
		    overlay_stretch	= FALSE
		}

		# Up (disabled)
		image
		{
		    function		= BOX
		    state 			= INSENSITIVE
		    detail			= "spinbutton_up"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-up-disable.png"
		    overlay_stretch	= FALSE
		}

		# Up (mouse over)
		image
		{
		    function		= BOX
		    state 			= ACTIVE
		    detail			= "spinbutton_up"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-up-prelight.png"
		    overlay_stretch	= FALSE
		}


		# Down
		image
		{
		    function		= BOX
		    state 			= NORMAL
		    detail			= "spinbutton_down"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-down.png"
		    overlay_stretch	= FALSE
		}
		
		# Down (mouse over)
		image
		{
		    function		= BOX
		    state 			= PRELIGHT
		    detail			= "spinbutton_down"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-down-prelight.png"
		    overlay_stretch	= FALSE
		}

		# Down (disabled)
		image
		{
		    function		= BOX
		    state 			= INSENSITIVE
		    detail			= "spinbutton_down"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-down-disable.png"
		    overlay_stretch	= FALSE
		}

		# Down (mouse over)
		image
		{
		    function		= BOX
		    state 			= ACTIVE
		    detail			= "spinbutton_down"
		    recolorable		= TRUE
		    file			= "Spin/spin.png"
		    border			= { 0, 0, 0, 0 }
		    stretch			= TRUE
			overlay_file	= "Spin/spin-down-prelight.png"
		    overlay_stretch	= FALSE
		}
	}
}

style "clearlooks-frame-title"
{
	fg[NORMAL] = lighter (@fg_color)
}

style "clearlooks-tooltips" = "clearlooks-wider"
{
	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
}

style "clearlooks-progressbar"
{
	xthickness = 1
	ythickness = 2

	fg[PRELIGHT] = @selected_fg_color
	bg[SELECTED] = "#b1cdda"

	engine "aurora"
	{

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
	bg[SELECTED] = "#b1cdda"
}

style "notebook"		= "default"
{

  xthickness            			= 5
  ythickness            			= 3

GtkNotebook::tab-overlap = 6

  #bg[NORMAL] = "#ffffff"
  #bg[INSENSITIVE] = "#EFEFEF"
  text[SELECTED]	= "#000000"
  #base[SELECTED]   	= "#969696" #

  engine "pixmap" 
    {
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE
	state			= ACTIVE
	file				= "Tabs/tab-bottom.png"
	border			= { 4,4,4,4}
	stretch			= TRUE
	gap_side			= TOP
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE
	state			= ACTIVE
	file				= "Tabs/tab-top.png"
	border			= { 4,4,4,4}
	stretch			= TRUE
	gap_side			= BOTTOM
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE
	state			= ACTIVE
	file				= "Tabs/tab-left.png"
	border			= { 4,4,4,4}
	stretch			= TRUE
	gap_side			= RIGHT
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE
	state			= ACTIVE
	file				= "Tabs/tab-right.png"
	border			= { 4,4,4,4}
	stretch			= TRUE
	gap_side			= LEFT
      }	
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE

	file				= "Tabs/tab-top-active.png"
	border			= { 6,6,6,6}
	stretch			= TRUE
	gap_side			= BOTTOM
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE

	file				= "Tabs/tab-bottom-active.png"
	border			= { 6,6,6,6}
	stretch			= TRUE
	gap_side			= TOP
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE

	file				= "Tabs/tab-left-active.png"
	border			= { 6,6,6,6}
	stretch			= TRUE
	gap_side			= RIGHT
      }
    image 
      {
        function			= EXTENSION
	recolorable		= TRUE

	file				= "Tabs/tab-right-active.png"
	border			= { 6,6,6,6}
	stretch			= TRUE
	gap_side			= LEFT
      }
#
# How to draw boxes with a gap on one side (ie the page of a notebook)
#
    image 
      {
        function			= BOX_GAP
	recolorable		= TRUE
	file				= "Tabs/notebook-top.png" 
	border			= { 7, 7, 7, 7 }
	stretch			= TRUE
	gap_file			= "Others/null2.png"
	gap_border     		= { 5, 5, 5, 5 }
	gap_start_file		= "Others/null.png"
	gap_start_border	= { 0, 0, 0, 0 }
	gap_end_file		= "Others/null.png"
	gap_end_border	= { 0, 0, 0, 0 }
	gap_side			= TOP
      }
    image 
      {
        function			= BOX_GAP
	recolorable		= TRUE
	file				= "Tabs/notebook-bottom.png"
	border			= { 7, 7, 7, 7 }
	stretch			= TRUE
	gap_file			= "Others/null3.png"
	gap_border		= { 5, 5, 5, 5  }
	gap_start_file		= "Others/null.png"
	gap_start_border	= { 10, 10, 5, 5 }
	gap_end_file		= "Others/null.png"
	gap_end_border	= { 10, 10, 5, 5 }
	gap_side			= BOTTOM
      }
    image 
      {
        function			= BOX_GAP
	recolorable		= TRUE
	file				= "Tabs/notebook-left.png"
	border			= { 7, 7, 7, 7 }
	stretch			= TRUE
	gap_file			= "Others/null4.png"
	gap_border		= { 5, 5, 5, 5  }
	gap_start_file		= "Others/null.png"
	gap_start_border	= { 0, 0, 2, 0 }
	gap_end_file		= "Others/null.png"
	gap_end_border	= { 0, 2, 1, 0 }
	gap_side			= LEFT
      }
    image 
      {
        function			= BOX_GAP
	recolorable		= TRUE
	file				= "Tabs/notebook-right.png" 
	border			= { 7, 7, 7, 7 }
	stretch			= TRUE
	gap_file			= "Others/null5.png"
	gap_border		= {  5, 5, 5, 5  }
	gap_start_file		= "Others/null.png"
	gap_start_border	= { 1, 2, 3, 4 }
	gap_end_file		= "Others/null.png"
	gap_end_border	= { 0, 0, 0, 2 }
	gap_side			= RIGHT
      }
#
# How to draw the box of a notebook when it isnt attached to a tab
#
    image 
      {
        function			= BOX
	recolorable		= TRUE
	file				= "Tabs/notebook-top.png"
	border			= { 7, 7, 7, 7 }
	stretch			= TRUE
	#gap_side			= TOP
      }
  }
}


class "GtkNotebook"      			style "notebook"

style "radio" #= "clearlooks-default"
{
  engine "pixmap" 
    {
	#This is the image used to draw an unchecked box.
        image 
	{
            function        = OPTION
            recolorable     = TRUE
            state = NORMAL
            shadow          = OUT
            overlay_file    = "Check-Radio/option1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = OPTION
            recolorable     = TRUE
            state = PRELIGHT
            shadow          = OUT
            overlay_file    = "Check-Radio/option1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = OPTION
            recolorable     = TRUE
            state = ACTIVE
            shadow          = OUT
            overlay_file    = "Check-Radio/option1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = OPTION
            recolorable     = TRUE
            state = INSENSITIVE
            shadow          = OUT
            overlay_file    = "Check-Radio/option5.png"
            overlay_stretch = FALSE
        }

	#This is the image used to draw a selected (checked) box.
        image 
	{
            function        = OPTION
            recolorable     = TRUE
	    state = NORMAL
            shadow          = IN
            overlay_file    = "Check-Radio/option2.png"
            overlay_stretch = FALSE
        }

  image 
	{
            function        = OPTION
            recolorable     = TRUE
	    state = PRELIGHT
            shadow          = IN
            overlay_file    = "Check-Radio/option2.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = OPTION
            recolorable     = TRUE
	    state = ACTIVE
            shadow          = IN
            overlay_file    = "Check-Radio/option2.png"
            overlay_stretch = FALSE
        }


     image 
	{
            function        = OPTION
            recolorable     = TRUE
	    state = INSENSITIVE
            shadow          = IN
            overlay_file    = "Check-Radio/option6.png"
            overlay_stretch = FALSE
        }

	#Use this image to draw the highlight when a line with a check box
	#is moused over.
	image 
	{
          function        = FLAT_BOX
            recolorable     = TRUE
      stretch			= TRUE
            file            = "Check-Radio/checklight.png"
          border          = { 2, 2, 2, 2 }
        }

    }
}

style "check"
{
  engine "pixmap" 
    {
	#This is the image used to draw an unchecked box.
        image 
	{
            function        = CHECK
            recolorable     = TRUE
            state = NORMAL
            shadow          = OUT
            overlay_file    = "Check-Radio/check1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = CHECK
            recolorable     = TRUE
            state = PRELIGHT
            shadow          = OUT
            overlay_file    = "Check-Radio/check1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = CHECK
            recolorable     = TRUE
            state = ACTIVE
            shadow          = OUT
            overlay_file    = "Check-Radio/check1.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = CHECK
            recolorable     = TRUE
            state = INSENSITIVE
            shadow          = OUT
            overlay_file    = "Check-Radio/check5.png"
            overlay_stretch = FALSE
        }

	#This is the image used to draw a selected (checked) box.
        image 
	{
            function        = CHECK
            recolorable     = TRUE
	    state = NORMAL
            shadow          = IN
            overlay_file    = "Check-Radio/check2.png"
            overlay_stretch = FALSE
        }

  image 
	{
            function        = CHECK
            recolorable     = TRUE
	    state = PRELIGHT
            shadow          = IN
            overlay_file    = "Check-Radio/check2.png"
            overlay_stretch = FALSE
        }

 image 
	{
            function        = CHECK
            recolorable     = TRUE
	    state = ACTIVE
            shadow          = IN
            overlay_file    = "Check-Radio/check2.png"
            overlay_stretch = FALSE
        }


     image 
	{
            function        = CHECK
            recolorable     = TRUE
	    state = INSENSITIVE
            shadow          = IN
            overlay_file    = "Check-Radio/check6.png"
            overlay_stretch = FALSE
        }

	#Use this image to draw the highlight when a line with a check box
	#is moused over.
	image 
	{
          function        = FLAT_BOX
            recolorable     = TRUE
      stretch			= TRUE
            file            = "Check-Radio/checklight.png"
          border          = { 2, 2, 2, 2 }
        }

    }
}





style "clearlooks-nautilus-location"
{
	bg[NORMAL] = mix(0.50, shade (1.05,@selected_bg_color), @tooltip_bg_color)
}

style "metacity-frame"
{
	bg[SELECTED] = mix (0.25, @fg_color, @selected_bg_color)
}

widget_class "*Gedit*Panel*GtkToggleButton" style "clearlooks-default"
widget "*Gedit*.tasklist-button" style "clearlooks-default"

#########################################
# Matches
#########################################

# theme radio buttons and checkmarks

class "GtkCheckButton"     			style "check"
class "GtkRadioButton"     			style "radio"
class "GtkRadioMenuItem"    		style "radio"
class "GtkCheckMenuItem"   		style "check"

# keep proper colour for Metacity
class "MetaFrames" 					style "metacity-frame"
class "GtkWindow"    			    		style "metacity-frame"

# theme default style is applied to every widget
class "GtkWidget"    					style "clearlooks-default"

# Increase the x/ythickness in some widgets
###########class "GtkToolbar"   					style "clearlooks-default" 
class "GtkRange"     					style "clearlooks-wide"
class "GtkFrame"     					style "clearlooks-wide"
class "GtkSeparator" 					style "clearlooks-wide"
#class "GtkEntry"     					style "clearlooks-wider"

class "GtkSpinButton"  					style "spinbutton"
class "GtkScale"       					style "clearlooks-scale"
#class "GtkVScale"      					style "clearlooks-vscale"
#class "GtkHScale"      					style "clearlooks-hscale"
class "GtkScrollbar"   					style "scroll"
#class "GtkVScrollbar"  					style "clearlooks-vscrollbar"
#class "GtkHScrollbar"  					style "clearlooks-hscrollbar"

# General matching following, the order is choosen so that the right styles override each other
# eg. progressbar needs to be more important then the menu match.

# This is not perfect, it could be done better
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
###widget_class "*<GtkNotebook>*<GtkEventBox>"     	style "clearlooks-notebook"
###widget_class "*<GtkNotebook>*<GtkDrawingArea>"  	style "clearlooks-notebook"
###widget_class "*<GtkNotebook>*<GtkLayout>"       	style "clearlooks-notebook"

widget_class "*<GtkButton>"      			style "clearlooks-button"
###widget_class "*<GtkNotebook>"    			style "clearlooks-notebook"
widget_class "*<GtkStatusbar>*"  			style "clearlooks-statusbar"

#widget_class "*<GtkComboBoxEntry>*"			style "clearlooks-comboboxentry"
#widget_class "*<GtkCombo>*"         			style "clearlooks-comboboxentry"

##########widget_class "*<GtkMenuBar>*"           		style "clearlooks-menubar"
widget_class "*<GtkMenu>*"              		style "clearlooks-menu"
widget_class "*<GtkMenuItem>*"          		style "clearlooks-menu-item"
widget_class "*<GtkSeparatorMenuItem>*" 		style "clearlooks-separator-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>" 			style "clearlooks-frame-title"
####widget_class "*.<GtkTreeView>*"        			style "clearlooks-treeview"

widget_class "*<GtkProgressBar>"       			style "clearlooks-progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" 		style "clearlooks-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"    		style "clearlooks-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"     		style "clearlooks-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"    		style "clearlooks-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"    			style "clearlooks-treeview-header"
widget_class "*.ETree.ECanvas"    			style "clearlooks-treeview-header"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" 					style "clearlooks-tooltips"

###################################################
# Special cases and work arounds
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" 			style : highest "clearlooks-nautilus-location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
style "clearlooks-combobox-text-color-workaround"
{
	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>"		style "clearlooks-combobox-text-color-workaround"

style "clearlooks-menuitem-text-is-fg-color-workaround"
{
	text[NORMAL]        = @fg_color
	text[PRELIGHT]      = @selected_fg_color
	text[SELECTED]      = @selected_fg_color
	text[ACTIVE]        = @fg_color
	text[INSENSITIVE]   = darker (@bg_color)
}

widget "*.gtk-combobox-popup-menu.*"   			style "clearlooks-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the
# base color set.
style "clearlooks-fg-is-text-color-workaround"
{
	fg[NORMAL]      = @text_color
	fg[PRELIGHT]    = @text_color
	fg[ACTIVE]      = @selected_fg_color
	fg[SELECTED]    = @selected_fg_color
	fg[INSENSITIVE] = darker (@bg_color)
	bg[SELECTED]    = @selected_bg_color
}

widget_class "*<GtkListItem>*" 				style "clearlooks-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree
# Only match GtkCList and not the parent widgets, because that would also change the headers.

widget_class "*<GtkCList>" 				style "clearlooks-fg-is-text-color-workaround"

style "clearlooks-evo-new-button-workaround"
{

	engine "clearlooks"
	{
		toolbarstyle = 0
	}
}
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "clearlooks-evo-new-button-workaround"


```

---

### Post by fredbird67 on 2008-05-26
ShodanjoDM, many, many thanks for providing the solution to properly display Aurora themes on here!  I had seen so many people upload them to Gnome-Look but never could get 'em to look right for the life of me!

It was getting so discouraging I was honestly considering leaving GNOME for another desktop environment or maybe even one of the more minimalist window managers even though I have half a gig of RAM on here, because what's the point of downloading a GTK theme if refuses to work for you?

But thanks to you, ShodanjoDM, IT WORKS PERFECTLY! :)

Fred in St. Louis

---

### Post by Jadephyre on 2008-05-26
@ShodanjoDM
mine looks exactly the same... something's very very wrong i suppose.
I'll install your Engine next and hope for the best.

EDIT:
Installed ShodanjoDM's Engine to no avail... something is seriously effed up here on my side i guess, seeing as everyone can use Ooboontoo and i can't.
I guess i should skip this Theme altogether, it's not worth the hassle i guess...

---

