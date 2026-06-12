---
title: "Nautilus - change left sidebar (panel) color"
date: 2014-10-01
forum: General Help
---

### Post by bokiscout on 2014-10-01
I was using Faience theme ([http://www.noobslab.com/2014/06/faience-theme-is-now-available-for.html](http://www.noobslab.com/2014/06/faience-theme-is-now-available-for.html)) and at first it was fine, then it become bugy in Nautilus:

[IMG]http://imagizer.imageshack.us/a/img840/4879/6of.png[/IMG]


I have read tha this due to some gtk 3.10 and gtk 3.12 incompatibility... If there is a way to fix it fine. I'll rather do that than anything else, I love the theme on my Ubuntu 14.04. (.1 maby - tell me how to check this).


If above is not possible I would like to change the colour of left sidebar (panel) color of Zukitwo theme from courent to #d3dae2:
[ATTACH=CONFIG]256894[/ATTACH]



here is the gtk2/gtkrc:
```
# Author: lassekongo83 
# 
# This library is free software; you can redistribute it and/or 
# modify it under the terms of the GNU Lesser General Public 
# License as published by the Free Software Foundation; either 
# version 2.1 of the License, or (at your option) any later version. 
# 
# See the file COPYING for the full license text. 
 
# NOTE: Uncommenting means to delete the "#" at the beginning of a line. Commenting means to add a "#" at the beginning of a line. The "#" tells the theme wether to ignore the specified line or not. 
 
# These are the defined colors for the theme. 
gtk_color_scheme = "bg_color:#d4d4d4\nselected_bg_color:#6699CC\nbase_color:#F7F7F7" # Background, base. 
gtk_color_scheme = "fg_color:#2c2c2c\nselected_fg_color:#f5f5f5\ntext_color:#2c2c2c" # Foreground, text. 
gtk_color_scheme = "tooltip_bg_color:#F5F5B5\ntooltip_fg_color:#000000" # Tooltips. 
gtk_color_scheme = "link_color:#08c" # Hyperlinks 
gtk_color_scheme = "bg_color_dark:#3f3f3f\ntext_color_dark:#FFF" # Dark colors 
 
### EXTERNAL FILES ### 
include "widgets/panel.rc"    # This includes the file that handles the panels. 
 
### MISC ### 
gtk-icon-sizes        = "gtk-button=16,16" # This makes button icons smaller. 
gtk-button-images    = 0 # Enables icons in buttons 
gtk-toolbar-style    = 0 # Disables text in toolbar 
gtk-auto-mnemonics    = 1 # Disables ugly lines under menu items 
 
#################### 
## Default Styles ## 
#################### 
 
style "murrine-default" { 
    GnomeHRef    ::link_color            = @link_color         
    GtkHTML        ::link-color            = @link_color 
     GtkIMHtmlr    ::hyperlink-color        = @link_color 
    GtkIMHtml    ::hyperlink-color        = @link_color 
    GtkWidget    ::link-color            = @link_color 
    GtkWidget    ::visited-link-color        = @text_color 
 
    GtkButton    ::child-displacement-x        = 1 
    GtkButton    ::child-displacement-y        = 1 
    GtkButton    ::default-border        = { 0, 0, 0, 0 } 
    GtkButtonBox    ::child-min-height        = 26 
    GtkCheckButton    ::indicator-size        = 15 
     
    GtkWidget    ::new-tooltip-style        = 1 
    GtkWidget    ::focus-line-width        = 1 
    GtkWidget    ::focus-padding            = 0 # Keeping this at 0 prevents the Firefox tabs from jumping a few pixels when you create a new tab. Set the value locally if needed. 
 
    GtkImage    ::x-ayatana-indicator-dynamic    = 1 
 
    GtkScrollbar    ::has-backward-stepper        = 0   
    GtkScrollbar    ::has-forward-stepper        = 0 
    GtkScrollbar    ::min-slider-length        = 15 
    GtkScrollbar    ::slider-width            = 13 
    GtkScrollbar    ::trough-border            = 0 
    GtkScrollbar    ::activate-slider        = 1 
 
    GtkScrolledWindow ::scrollbar-spacing        = 0 
    GtkScrolledWindow ::scrollbars-within-bevel    = 1 
 
    GtkPaned    ::handle-size            = 6 
 
    GtkRange    ::trough-border            = 0 
    GtkRange    ::slider-width            = 11 
    GtkRange    ::stepper-size            = 0 
    GtkRange    ::stepper_spacing        = 0 
    GtkRange    ::trough-under-steppers        = 0 
 
    GtkScale    ::slider-length            = 16 
    GtkScale    ::slider-width            = 16 
 
    GtkMenuBar    ::internal-padding        = 0 
    GtkExpander    ::expander-size            = 16 
    GtkToolbar    ::internal-padding        = 0 
    GtkTreeView    ::expander-size            = 6 
    GtkTreeView    ::indent-expanders        = 1 
    GtkTreeView    ::vertical-separator        = 1 
    GtkNotebook    ::tab-overlap            = -1 
 
    GtkMenu        ::horizontal-padding        = 0 
    GtkMenu        ::vertical-padding        = 0 
    GtkMenuItem    ::horizontal-padding        = 0 
 
    WnckTasklist    ::fade-overlay-rect        = 0 
    # The following line hints to gecko (and possibly other appliations) 
    # that the entry should be drawn transparently on the canvas. 
    # Without this, gecko will fill in the background of the entry. 
    GtkEntry    ::honors-transparent-bg-hint    = 1 
    GtkEntry    ::state-hint            = 0 
    GtkEntry    ::progress-border        = { 2, 2, 2, 2 } 
 
    GtkProgressBar    ::min-horizontal-bar-height    = 16 
    GtkProgressBar    ::min-vertical-bar-width    = 16 
     
    #GtkToolbar    ::shadow-type = GTK_SHADOW_NONE # Makes toolbars flat and unified. 
    #GtkMenuBar    ::shadow-type = GTK_SHADOW_NONE # Makes menus flat and unified. 
    GtkMenuBar    ::window-dragging        = 1 
    GtkToolbar    ::window-dragging        = 1 
 
    # The little ugly gripper at the bottom right needs to go. 
    GtkWindow    ::resize-grip-height        = 0 
    GtkWindow    ::resize-grip-width        = 0 
 
    xthickness = 1 
    ythickness = 1 
 
    ### Color Definitions ### 
 
    fg[NORMAL]        = @fg_color 
    fg[PRELIGHT]        = @fg_color 
    fg[SELECTED]        = @selected_fg_color 
    fg[ACTIVE]        = @fg_color 
    fg[INSENSITIVE]        = darker (@bg_color) 
    bg[NORMAL]        = @bg_color 
    bg[PRELIGHT]        = shade (1.02, @bg_color) 
    bg[SELECTED]        = @selected_bg_color 
    bg[INSENSITIVE]        = @bg_color 
    bg[ACTIVE]        = shade (1.04, @bg_color) 
    base[NORMAL]        = @base_color 
    base[PRELIGHT]        = shade (0.95, @bg_color) 
    base[ACTIVE]        = shade (0.92, @selected_bg_color) 
    base[SELECTED]        = shade (0.93, @selected_bg_color) 
    base[INSENSITIVE]    = @bg_color 
    text[NORMAL]        = @text_color 
    text[PRELIGHT]        = @text_color 
    text[ACTIVE]        = @selected_fg_color 
    text[SELECTED]        = @selected_fg_color 
    text[INSENSITIVE]    = darker (@bg_color) 
 
    ### Murrine Settings ### 
     
    engine "murrine" { 
        animation        = FALSE 
        arrowstyle        = 1            # 0 = normal arrows, 1 = filled arrows         
        border_shades        = {1.0, 0.8}        # gradient to draw on border         
        colorize_scrollbar    = FALSE         
        comboboxstyle        = 0            # 0 = normal combobox, 1 = colorized combobox below arrow         
        contrast        = 0.4             # 0.8 for less contrast, more than 1.0 for more contrast on borders 
        default_button_color    = shade (1.12, @selected_bg_color) 
        focus_color        = @selected_bg_color 
        focusstyle        = 3 
        glazestyle        = 1            # 0 = flat highlight, 1 = curved highlight, 2 = concave style, 3 = top curved highlight, 4 = beryl highlight 
        gradient_shades        = {1.1,1.1,0.94,0.94}    # Sets the gradients on the widgets. 
        glowstyle        = 0            # 0,1,2,3,4 
        glow_shade        = 1.1 
        highlight_shade        = 1.0            # set highlight amount for buttons or widgets 
        lightborder_shade    = 1.1            # sets lightborder amount for buttons or widgets 
        lightborderstyle    = 0            # 0 = lightborder on top side, 1 = lightborder on all sides 
        listviewheaderstyle    = 1            # 0 = flat, 1 = glassy, 2 = raised 
        listviewstyle        = 1            # 0 = nothing, 1 = dotted 
        menubaritemstyle    = 0            # 0 = menuitem look, 1 = button look 
        menubarstyle        = 2            # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped 
        menuitemstyle        = 0            # 0 = flat, 1 = glassy, 2 = striped 
        menustyle        = 0            # 0 = no vertical menu stripe, 1 = display vertical menu stripe 
        prelight_shade        = .95            # shade level for scrollbar's slider, comboboxstyle(1), and prelight state with gradient_colors         
        reliefstyle        = 2            # 0 = flat, 1 = inset, 2 = shadow, 3 = shadow with gradient, 4 = stronger shadow with gradient 
        rgba            = FALSE            # FALSE = disabled, TRUE = enabled 
        roundness        = 2            # 0 = squared, 1 = old default, more will increase roundness 
        scrollbarstyle        = 0            # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles 
        separatorstyle        = 1            # 0 = Hard seperators 1 = Smooth seperators 
        sliderstyle        = 0            # 0 = nothing added, 1 = handles 
        stepperstyle        = 1            # 0 = standard, 1 = integrated stepper handles, 2 = unknown 
        progressbarstyle    = 1            # 0 = nothing, 1 = stripes, 2 = lines 
        shadow_shades        = {0.5, 0.0}        # gradient for shadows.         
        textstyle        = 0            # 0 = normal text, 1 = inset. Very resource heavy! 
        toolbarstyle        = 2            # 0 = flat, 1 = glassy, 2 = gradient         
        trough_shades        = {0.98, 1.06}        # draw gradient on trough of GtkScrollbar and GtkProgressbar 
    } 
} 
 
### THEME MODULES ### 
 
style "murrine-dark" { 
    base[NORMAL]        = @bg_color_dark 
    base[PRELIGHT]        = shade (0.95, @bg_color_dark) 
    base[INSENSITIVE]    = @bg_color_dark 
    bg[NORMAL]        = @bg_color_dark 
    bg[PRELIGHT]        = shade (1.02, @bg_color_dark) 
    bg[SELECTED]        = shade (0.90, @selected_bg_color) 
    bg[INSENSITIVE]        = @bg_color_dark 
    bg[ACTIVE]        = shade (1.04, @bg_color_dark) 
    fg[NORMAL]        = @text_color_dark 
    fg[PRELIGHT]        = @text_color_dark 
    fg[SELECTED]        = @text_color_dark 
    fg[ACTIVE]        = @text_color_dark 
    fg[INSENSITIVE]        = darker (@bg_color) 
    text[NORMAL]        = @text_color_dark 
    text[PRELIGHT]        = @text_color_dark 
    text[ACTIVE]        = @text_color_dark 
    text[SELECTED]        = @text_color_dark 
    text[INSENSITIVE]    = darker (@bg_color_dark) 
} 
 
style "murrine-thin"        = "murrine-default"    { xthickness = 0 ythickness = 0 } 
style "murrine-wide"        = "murrine-default"    { xthickness = 2 ythickness = 2 } 
style "murrine-wider"        = "murrine-default"    { xthickness = 3 ythickness = 3 } 
style "murrine-widest"        = "murrine-default"    { xthickness = 4 ythickness = 4 } 
style "murrine-thin-dark"    = "murrine-dark"    { xthickness = 0 ythickness = 0 } 
style "murrine-wide-dark"    = "murrine-dark"    { xthickness = 2 ythickness = 2 } 
style "murrine-wider-dark"    = "murrine-dark"    { xthickness = 3 ythickness = 3 } 
style "murrine-widest-dark"    = "murrine-dark"    { xthickness = 4 ythickness = 4 } 
 
################### 
## Widget Styles ## 
################### 
 
style "murrine-entry" = "murrine-wider" { 
    bg[SELECTED] = mix (0.4, @selected_bg_color, @base_color) 
    fg[SELECTED] = @text_color 
} 
 
style "murrine-button" = "murrine-wider" { 
    bg[NORMAL]    = shade (1.06, @bg_color)  
    bg[PRELIGHT]    = shade (1.13, @bg_color)   
    bg[ACTIVE]    = shade (0.85, @bg_color) 
    bg[SELECTED]    = shade (1.0, @selected_bg_color)   
    bg[INSENSITIVE]    = shade (0.95, @bg_color) 
 
      engine "murrine" { 
        contrast        = .8 
        lightborder_shade    = 1.9 
        roundness        = 2 
        border_shades        = {0.95, 0.8} 
        shadow_shades        = {1.0, 0.1} 
    } 
} 
 
style "murrine-notebook-bg" { 
    bg[NORMAL] = shade (1.1, @bg_color) 
    bg[ACTIVE] = shade (0.97, @bg_color) 
    fg[ACTIVE] = mix (0.8, @fg_color, shade (0.97, @bg_color)) 
} 
 
style "murrine-notebook" = "murrine-notebook-bg" { 
    xthickness = 2 # Width of tabs and notebook borders. 
    ythickness = 1 # Height of tabs and notebook borders. 
 
    engine "murrine" { 
        contrast        = .8 
        gradient_shades        = {1.28,1.28,0.87,0.87} 
        focusstyle        = 2 
        lightborder_shade    = 1.16 
        roundness        = 4 
    } 
} 
 
style "notebook-close" { stock["gtk-close"] = {{ "widgets/Others/close.png", *, *, * }} } # Close icon on tabs 
 
style "murrine-menubar" = "murrine-default" { 
    ythickness    = 0 
    bg[NORMAL]    = @bg_color 
    fg[NORMAL]    = @fg_color 
    fg[PRELIGHT]    = @fg_color 
    fg[SELECTED]    = @fg_color 
} 
 
style "murrine-menubar-menuitem" = "murrine-wider" { 
    xthickness    = 6 
    bg[PRELIGHT]    = @selected_bg_color 
    bg[SELECTED]    = @bg_color 
 
    engine "murrine" { 
        contrast = .0  
        roundness = 0 
        border_shades = { 1.0, 0.8 } 
        gradient_shades = {1.0, 1.0, 0.85, 0.85} 
    } 
} 
 
style "murrine-menu" { 
    xthickness = 0 
    ythickness = 0 
 
    bg[NORMAL] = @base_color 
 
    engine "murrine" { 
        border_shades = { 1.2, 1.0 } 
        roundness = 0 # Roundness of menu items. 
        textstyle = 0 
    } 
} 
 
style "murrine-menu-item" = "murrine-wider" { 
    xthickness = 2 
    ythickness = 3 
 
    bg[SELECTED] = shade (0.95, @selected_bg_color) 
    bg[PRELIGHT] = shade (0.95, @selected_bg_color) 
    fg[PRELIGHT] = @selected_fg_color 
 
    engine "murrine" { 
        border_shades = { 1.2, 1.0 } 
        roundness = 0 
        textstyle = 0 
    } 
} 
 
# This style is there to modify the separator menu items. The goals are: 
# 1. Get a specific height. 
# 2. The line should go to the edges (ie. no border at the left/right) 
style "murrine_separator_menu_item" { 
    bg[NORMAL] = @base_color # Remove for visible separators. 
    xthickness = 1 
    ythickness = 0 
 
    GtkSeparatorMenuItem::horizontal-padding = 0 
    GtkWidget::wide-separators = 1 
    GtkWidget::separator-width = 1 
    GtkWidget::separator-height = 7 
     
    engine "murrine" { 
        contrast = 0.6 # Set the contrast to 0.6 for visible separators. 
        separatorstyle = 0 
    } 
} 
 
style "murrine-treeview" { 
    GtkTreeView::odd_row_color    = shade (0.97, @base_color) 
    GtkTreeView::even_row_color    = @base_color 
 
      engine "murrine" { roundness = 0 } # This makes treeview progressbars square. 
} 
 
style "murrine-treeview-header" = "murrine-button" { 
    xthickness = 2 
    ythickness = 0 
     
    bg[NORMAL]    = shade (0.98, @bg_color) # Color for treeview headers. 
    bg[PRELIGHT]    = shade (1.10, @bg_color) # Color for treeview header prelight. 
    bg[ACTIVE]    = shade (0.85, @bg_color) # Color for pressed-treeview. 
       
    engine "murrine" { 
        roundness        = 0  # This makes treeview progressbars square. 
        contrast        = .8 
        lightborder_shade    = 1.0 
        border_shades        = { 1.1, 1.1 } 
        gradient_shades        = {1.0,1.0,1.1,1.1} 
    } 
} 
 
style "murrine-frame-title" { fg[NORMAL] = lighter (@fg_color) } 
 
style "murrine-tooltips" = "murrine-wider" { 
    bg[NORMAL] = @tooltip_bg_color 
    fg[NORMAL] = @tooltip_fg_color 
    engine "murrine" {textstyle = 0} 
} 
 
style "murrine-progressbar" = "murrine-thin" { 
    bg[NORMAL]    = shade (1.06, @bg_color)  
    bg[ACTIVE]    = shade (0.85, @bg_color) 
    bg[SELECTED]    = shade (1.0, @selected_bg_color)   
    bg[INSENSITIVE]    = shade (0.95, @bg_color) 
 
    engine "murrine" { 
        contrast        = 1.0 
        lightborder_shade    = 1.2 
        trough_shades        = { 1.06, 1.16} 
        gradient_shades        = {0.95,0.95,1.1,1.1} 
        border_shades        = { 1.1, 1.1 } 
        roundness        = 0 
    } 
} 
 
style "murrine-statusbar" { 
    xthickness = 2 
} 
 
style "murrine-comboboxentry" { engine "murrine" { contrast = .4 }} 
 
style "murrine-spinbutton" {  
    bg[ACTIVE] = shade (0.85, @bg_color) # Color for pressed-spinbuttons.  
} 
 
style "murrine-scale" = "murrine-wider" { 
    bg[NORMAL]    = shade (1.06, @bg_color)  
    bg[PRELIGHT]    = shade (1.2, @bg_color)   
    bg[ACTIVE]    = shade (0.85, @bg_color) 
    bg[SELECTED]    = shade (1.0, @selected_bg_color)   
    bg[INSENSITIVE]    = shade (0.95, @bg_color) 
     
    engine "murrine" { 
        roundness    = 7 
        contrast    = .8 
        border_shades    = {1.0, 1.0} 
        trough_shades    = {1.06, 1.16} 
    } 
} 
 
style "pixmap-scale" { 
    engine "pixmap" { 
    image 
        { 
            function    = BOX 
            detail        = "trough" 
            file        = "widgets/Scale/trough-horizontal.png" 
            border        = { 2, 2, 0, 0 } 
            stretch        = TRUE 
            orientation    = HORIZONTAL 
        } 
    image 
        { 
            function    = BOX 
            detail        = "trough" 
            file        = "widgets/Scale/trough-vertical.png" 
            border        = { 0, 0, 2, 2 } 
            stretch        = TRUE 
            orientation    = VERTICAL 
        } 
 
# Horizontal 
 
    image 
        { 
            function    = SLIDER 
            state           = NORMAL 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider.png" 
            overlay_stretch    = FALSE 
            orientation    = HORIZONTAL 
        } 
    image 
        { 
            function    = SLIDER 
            state           = PRELIGHT 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider-hover.png" 
            overlay_stretch    = FALSE 
            orientation    = HORIZONTAL 
        } 
    image 
        { 
            function    = SLIDER 
            state           = INSENSITIVE 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider-ins.png" 
            overlay_stretch    = FALSE 
            orientation    = HORIZONTAL 
        } 
 
# Vertical 
 
    image 
        { 
            function    = SLIDER 
            state           = NORMAL 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider.png" 
            overlay_stretch    = FALSE 
            orientation    = VERTICAL 
        } 
    image 
        { 
            function    = SLIDER 
            state           = PRELIGHT 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider-hover.png" 
            overlay_stretch    = FALSE 
            orientation    = VERTICAL 
        } 
    image 
        { 
            function    = SLIDER 
            state           = INSENSITIVE 
            file        = "widgets/Others/null.png" 
            border        = { 0, 0, 0, 0 } 
            stretch        = FALSE 
            overlay_file    = "widgets/Scale/slider-ins.png" 
            overlay_stretch    = FALSE 
            orientation    = VERTICAL 
        } 
 
# Function below removes ugly boxes 
    image 
        { 
            function    = BOX 
            file            = "widgets/Others/null.png" 
            border          = { 3, 3, 3, 3 } 
            stretch         = TRUE 
        } 
 
    } 
} 
 
style "murrine-scrollbar" { 
    bg[NORMAL]    = shade (0.90, @bg_color) 
    bg[SELECTED]    = shade (0.6, @base_color) 
    bg[ACTIVE]    = shade (0.8, @bg_color) 
    bg[PRELIGHT]    = shade (0.8, @bg_color) 
     
    engine "murrine" { 
        roundness    = 8 
        border_shades    = {0.80, 0.80} 
        contrast    = 0.0 
    } 
} 
 
style "murrine-sidebar" { 
    xthickness = 0 
    ythickness = 0 
 
    base[NORMAL]    = @bg_color 
    bg[NORMAL]    = @bg_color 
    text[NORMAL]    = @text_color 
 
    font_name    = "Regular" 
 
    GtkTreeView::odd_row_color    = @bg_color 
    GtkTreeView::even_row_color    = @bg_color 
 
    engine "murrine" { listviewstyle = 0 } 
} 
 
style "murrine-toggleswitch" = "murrine-wider" { 
    ythickness = 4 
 
    bg[ACTIVE]    = shade (0.80, @bg_color) 
    bg[NORMAL]    = shade (1.15, @bg_color) 
    bg[PRELIGHT]    = shade (1.13, @selected_bg_color) 
    bg[SELECTED]    = shade (0.75, @selected_bg_color) 
    bg[INSENSITIVE]    = shade (0.98, @bg_color) 
     
    engine "murrine" { 
        contrast        = 1.25 
        lightborderstyle    = 1 
    } 
} 
 
style "murrine-radiocheck" = "murrine-wider" { 
    bg[NORMAL]    = shade (1.06, @bg_color)  
    bg[PRELIGHT]    = shade (1.06, @bg_color)   
    bg[ACTIVE]    = shade (0.85, @bg_color) 
    bg[SELECTED]    = shade (1.0, @selected_bg_color)   
    bg[INSENSITIVE]    = shade (0.95, @bg_color) 
 
      engine "murrine" { 
        contrast        = .8 
        lightborder_shade    = 1.9 
    } 
} 
 
style "murrine-radiocheck-menu" { 
    fg[PRELIGHT]    = @selected_fg_color 
    text[PRELIGHT]    = @selected_fg_color 
         
    engine "murrine" {} 
} 
 
style "murrine-toolbar" = "murrine-thin" { 
    bg[NORMAL] = @bg_color 
    ythickness = 3 
} 
 
style "pixmap-sidebar-handle-left" { 
    GtkPaned::handle-size = 1 
 
    engine "pixmap" { 
        image { function = HANDLE file = "/widgets/Others/handle.png" stretch = TRUE border = { 0, 0, 0, 0 } } 
    } 
} 
 
############################################################################### 
# The following part of the gtkrc applies the different styles to the widgets. 
############################################################################### 
 
# Murrine default style is applied to every widget. 
class "GtkWidget"    style "murrine-default" 
 
# Increase the x/ythickness in some widgets. 
class "GtkFrame"    style "murrine-wide" 
class "GtkEntry"    style "murrine-entry" 
class "GtkSeparator"    style "murrine-wide" 
class "GtkCalendar"    style "murrine-wide" 
class "GtkInfoBar"    style "murrine-default" 
class "GtkIconView"    style "murrine-default" 
 
class "GtkToolbar"    style "murrine-toolbar" 
 
class "GtkSpinButton"    style "murrine-spinbutton" 
class "GtkScale"    style "pixmap-scale" 
class "GtkVScale"    style "pixmap-scale" 
class "GtkHScale"    style "pixmap-scale" 
 
class "GtkScrollbar"    style "murrine-scrollbar" 
class "GtkVScrollbar"    style "murrine-scrollbar" 
class "GtkHScrollbar"    style "murrine-scrollbar" 
 
widget "*ToggleSwitch*"    style "murrine-toggleswitch" 
 
widget "*SidebarHandleLeft"    style "pixmap-sidebar-handle-left" 
widget "*SidebarContent"    style "murrine-sidebar" 
 
# General matching following, the order is choosen so that the right styles override each other eg. progressbar needs to be more important then the menu match. 
 
# This is not perfect, it could be done better (That is modify *every* widget in the notebook, and change those back that we really don't want changed) 
widget_class "*<GtkNotebook>*<GtkEventBox>"        style "murrine-notebook-bg" 
widget_class "*<GtkNotebook>*<GtkDrawingArea>"        style "murrine-notebook-bg" 
widget_class "*<GtkNotebook>*<GtkLayout>"        style "murrine-notebook-bg" 
widget_class "*<GtkNotebook>*<GtkViewport>"        style "murrine-notebook-bg" 
widget_class "*<GtkNotebook>*<GtkScrolledWindow>"    style "murrine-notebook-bg" 
widget_class "*<GtkNotebook>*<GtkLabel>"        style "murrine-notebook-bg" 
 
widget_class "*<GtkButton>"    style "murrine-button" 
widget_class "*<GtkNotebook>"    style "murrine-notebook" 
widget_class "*<GtkNotebook>*"    style "notebook-close" 
widget_class "*<GtkStatusbar>*"    style "murrine-statusbar" 
 
widget_class "*<GtkComboBoxEntry>*"        style "murrine-comboboxentry" 
widget_class "*<GtkCombo>*"            style "murrine-comboboxentry" 
 
widget_class "*<GtkMenuBar>*"            style "murrine-menubar" 
widget_class "*<GtkMenu>*"            style "murrine-menu" 
widget_class "*<GtkMenuItem>*"            style "murrine-menu-item" 
widget_class "*<GtkSeparatorMenuItem>*"        style "murrine_separator_menu_item" 
widget_class "*<GtkMenuBar>*<GtkMenuItem>*"    style "murrine-menubar-menuitem" 
 
widget_class "*.<GtkFrame>.<GtkLabel>"        style "murrine-frame-title" 
widget_class "*.<GtkTreeView>*"            style "murrine-treeview" 
 
widget_class "*<GtkProgress>"            style "murrine-progressbar" 
widget_class "*<GtkProgressBar>"        style "murrine-progressbar" 
 
widget_class "*<GtkRadioButton>*"        style "murrine-radiocheck" 
widget_class "*<GtkCheckButton>*"        style "murrine-radiocheck" 
class "GtkCheckMenuItem"            style:highest "murrine-radiocheck-menu" 
class "GtkRadioMenuItem"            style:highest "murrine-radiocheck-menu" 
 
# Treeview header 
widget_class "*.<GtkTreeView>.<GtkButton>"    style "murrine-treeview-header" 
widget_class "*.<GtkCTree>.<GtkButton>"        style "murrine-treeview-header" 
widget_class "*.<GtkList>.<GtkButton>"        style "murrine-treeview-header" 
widget_class "*.<GtkCList>.<GtkButton>"        style "murrine-treeview-header" 
 
################################ 
# FIXME: This will not work if one embeds eg. a button into the tooltip. 
################################ 
widget "gtk-tooltip*" style "murrine-tooltips" 
 
################################################### 
# SPECIAL CASES AND WORKAROUNDS 
################################################### 
 
# Wrokaround style for places where the text color is used instead of the fg color. 
style "text_is_fg_color_workaround" { 
    text[NORMAL]      = @fg_color 
    text[PRELIGHT]    = @fg_color 
    text[SELECTED]    = @selected_fg_color 
    text[ACTIVE]      = @fg_color 
    text[INSENSITIVE] = darker (@bg_color) 
} 
 
# Workaround style for menus where the text color is used instead of the fg color. 
style "menuitem_text_is_fg_color_workaround" { 
    text[NORMAL] = @fg_color 
    text[PRELIGHT] = @selected_fg_color 
    text[SELECTED] = @selected_fg_color 
    text[ACTIVE] = @fg_color 
    text[INSENSITIVE] = darker (@bg_color) 
} 
 
# Workaround style for places where the fg color is used instead of the text color. 
style "fg_is_text_color_workaround" { 
    fg[NORMAL]        = @text_color 
    fg[PRELIGHT]      = @text_color 
    fg[SELECTED]      = @selected_fg_color 
    fg[ACTIVE]        = @selected_fg_color 
    fg[INSENSITIVE]   = darker (@bg_color) 
} 
 
# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646 
# Note that this work around assumes that the combobox is _not_ in appears-as-list mode. 
widget_class "*.<GtkComboBox>.<GtkCellView>" style "text_is_fg_color_workaround" 
# This is the part of the workaround that fixes the menus 
widget "*.gtk-combobox-popup-menu.*" style "menuitem_text_is_fg_color_workaround" 
 
# Work around the usage of GtkLabel inside GtkListItems to display text. 
# This breaks because the label is shown on a background that is based on the base color. 
widget_class "*<GtkListItem>*" style "fg_is_text_color_workaround" 
# GtkCList also uses the fg color to draw text on top of the base colors. 
widget_class "*<GtkCList>" style "fg_is_text_color_workaround" 
# Nautilus when renaming files, and maybe other places. 
widget_class "*<EelEditableLabel>" style "fg_is_text_color_workaround" 
 
# Thickness for indicator menu items 
widget "*IdoEntryMenuItem*" style "murrine-wide" 
 
# XFCE desktop icon text looks weird when murrine textstyle is on. 
style "xfdesktop-icon-view" { engine "murrine" { textstyle = 0 }} 
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view" 
 
widget "xfwm4-tabwin*" style "murrine-dark" 
 
# Invisible toolbar separator 
style "murrine-toolseparator" { 
    xthickness = 0 
      ythickness = 0 
 
    engine "pixmap" { 
        image { 
            function    = BOX 
            file        = "widgets/Others/null.png" 
            border        = { 2, 2, 2, 2 } 
            stretch        = TRUE 
            } 
     } 
} 
class "GtkSeparatorToolItem" style "murrine-toolseparator" 
 
### EXTERNAL FILES ### 
include "chromium.rc"    # Chromium styling 
include "thunar.rc"    # Thunar styling
```



here is the gtk3/gnome-application.css
```
@define-color documents_emblem_bg #3465a4;
@define-color documents_collection_bg #d3d7cf;
@define-color gedit_not_found_bg rgb (237, 54, 54);
@define-color gedit_not_found_fg white;

* {
    -GtkIMHtml-hyperlink-color: @link_color;
    -GtkHTML-link-color: @link_color;

    -WnckTasklist-fade-overlay-rect: 0;
}

/****************
 * Applications *
 ****************/

/*
 * Evolution
 */

/* needed for webkit/GtkStyle/Evolution compatibility */
GtkHTML:active,
GtkHTML:active:backdrop {
    color: @theme_unfocused_selected_fg_color;
    background-color: @theme_unfocused_selected_bg_color;
}

/*
 * Sushi
 */

/* used by gnome-font-viewer and sushi */
SushiFontWidget {
    padding: 6px 12px;
}

/*
 * GNOME Terminal
 */

VteTerminal {
    background-color: @theme_base_color;
    color: @theme_fg_color;
}

TerminalWindow GtkNotebook.notebook {
    border-bottom-width: 0;
    border-right-width: 0;
    border-left-width: 0;
}

/*
 * Nautilus
 */

.nautilus-canvas-item {
    border-radius: 5px;
}

.nautilus-desktop.nautilus-canvas-item {
    color: @theme_selected_fg_color;
    text-shadow: 1px 1px black;
}

.nautilus-desktop.nautilus-canvas-item:active {
    color: @theme_text_color;
}

.nautilus-desktop.nautilus-canvas-item:selected {
    color: @theme_selected_fg_color;
}

.nautilus-desktop.nautilus-canvas-item:active,
.nautilus-desktop.nautilus-canvas-item:prelight,
.nautilus-desktop.nautilus-canvas-item:selected {
    text-shadow: none;
}

.nautilus-desktop.nautilus-canvas-item:selected:backdrop {
    color: @theme_unfocused_selected_fg_color;
}

NautilusWindow .sidebar .frame {
    border-style: none;
}

NautilusWindow .sidebar row:hover {
    background-color: shade (@theme_bg_color, 0.95);
}

NautilusWindow * {
    -GtkPaned-handle-size: 1;
}

NautilusWindow .pane-separator {
    background-image: url("assets/null.png");
}

NautilusWindow > GtkGrid > .pane-separator,
NautilusWindow > GtkGrid > .pane-separator:hover {
    border-width: 0 1px 0 0;
    border-style: solid;
    border-color: @borders;
    background-color: @sidebar_bg;
    color: shade (@theme_bg_color, 0.9);
}

NautilusNotebook.notebook {
    border-right-width: 0;
    border-left-width: 0;
    border-bottom-width: 0;
}

NautilusNotebook .frame {
    border-width: 0;
}

NautilusToolbar .button {
    icon-shadow: 0 1px @button_text_shadow;
}

NautilusToolbar .button:active {
    icon-shadow: 0 1px @button_active_text_shadow;
}

NautilusToolbar .button:insensitive,
NautilusToolbar .button:active *:insensitive {
    icon-shadow: none;
}

NautilusQueryEditor .search-bar.toolbar {
    border-top-width: 0;
    border-bottom-width: 0;
}

NautilusQueryEditor .toolbar {
    padding-top: 3px;
    padding-bottom: 2px;

    border-width: 1px 0 0 0;
    border-style: solid;
}

NautilusQueryEditor .toolbar:nth-child(2) {
    border-color: @borders;
}

NautilusQueryEditor .toolbar:last-child,
NautilusQueryEditor .search-bar.toolbar:only-child {
    border-bottom-width: 1px;
    border-bottom-color: @borders;
}

NautilusQueryEditor .toolbar:backdrop:nth-child(2) {
    border-color: @unfocused_borders;
}

/*
 * Gedit
 */

GeditWindow * {
    -GtkPaned-handle-size: 1;
}

GeditWindow .pane-separator,
GeditWindow .pane-separator:hover {
    border-width: 0 1px 1px 1px;
    border-style: solid;
    border-color: @borders;
    background-color: @sidebar_bg;
    background-image: url("assets/null.png");
    color: @borders;
}

.gedit-headerbar-paned:backdrop {
    background-image: url("assets/null.png");
}

.gedit-document-panel {
    background-color: @sidebar_bg;
}

.gedit-document-panel-group-row,
.gedit-document-panel-group-row:hover {
    border-top: 1px solid shade(@sidebar_bg, 0.90);
    background-color: @sidebar_bg;
}

.gedit-document-panel-document-row:hover {
    background-color: shade(@sidebar_bg, 0.95);
}

.gedit-document-panel-document-row:selected,
.gedit-document-panel-document-row:selected:hover {
    background-color: @theme_selected_bg_color;
}

/* sidepane close button styling (copied from the gtk tab close button) */
.gedit-document-panel .list-row .button {
    color: transparent;
    border-image: none;
    background-image: none;
    background-color: transparent;
    border-radius: 3px;
    border-style: solid;
    border-color: transparent;
    border-width: 1px;
    padding: 1px;
    icon-shadow: none;
}

.gedit-document-panel .prelight-row .button  {
    color: mix(@theme_fg_color, @sidebar_bg, 0.6);
    border-color: alpha(black, 0.1);
    transition: all 200ms ease-in;
}

.gedit-document-panel .list-row .button:hover,
.gedit-document-panel .prelight-row .button:hover {
    color: @theme_fg_color;
    border-color: alpha(black, 0.1);
    transition: all 200ms ease-in;
}

.gedit-document-panel .prelight-row .button:active {
    color:  @button_active_text;
    background-color: alpha(black, 0.08);
    box-shadow: inset 0 1px alpha(black, 0.05);
    icon-shadow: 0 1px @button_active_text_shadow;

    border-color: alpha(black, 0.27)
        alpha(black, 0.13)
        alpha(black, 0.13)
        alpha(black, 0.13);
}

.gedit-document-panel .prelight-row .button:backdrop {
    color: mix(@theme_unfocused_fg_color, @theme_unfocused_base_color, 0.7);
    icon-shadow: none;
}

.gedit-document-panel .prelight-row .button:backdrop:hover {
    color: @theme_unfocused_fg_color;
    transition: all 200ms ease-out;
}

.gedit-document-panel-dragged-row {
    border: 1px solid @borders;
    background-color: shade(@sidebar_bg, 0.90);
    color: @theme_fg_color;
}

.gedit-document-panel-placeholder-row {
    border: none;
    background-color: mix(@sidebar_bg, @theme_selected_bg_color, 0.20);
    transition: all 200ms ease-in;
}

GeditStatusbar {
    border-top: 1px solid @borders;
}

GeditStatusbar GeditSmallButton,
GeditStatusMenuButton {
    text-shadow: none;
}

GeditStatusbar GeditSmallButton.button:backdrop,
GeditStatusbar GeditSmallButton.button:backdrop:hover,
GeditStatusbar GeditSmallButton.button,
GeditStatusbar GeditSmallButton.button:hover,
GeditStatusbar GeditSmallButton.button:active,
GeditStatusbar GeditSmallButton.button:active:hover,
GeditStatusMenuButton.button:backdrop,
GeditStatusMenuButton.button:backdrop:hover,
GeditStatusMenuButton.button,
GeditStatusMenuButton.button:hover,
GeditStatusMenuButton.button:active,
GeditStatusMenuButton.button:active:hover {
    border-image: none;
    border-style: solid;
    border-width: 0 1px;
    border-radius: 0;
    padding: 1px 8px 2px 4px;
}

GeditStatusbar GeditSmallButton.button:hover,
GeditStatusbar GeditSmallButton.button:active,
GeditStatusbar GeditSmallButton.button:active:hover,
GeditStatusMenuButton.button:hover,
GeditStatusMenuButton.button:active,
GeditStatusMenuButton.button:active:hover {
    border-color: @borders;
}

GeditStatusbar GeditSmallButton.button:active,
GeditStatusMenuButton.button:active {
    background-image: linear-gradient(to bottom,
        @borders,
        shade(@theme_bg_color, 0.95));
    background-color: transparent;
    color: @theme_selected_fg_color;
    text-shadow: 0 1px @button_text_shadow;
}

GeditStatusbar GeditSmallButton.button:backdrop,
GeditStatusbar GeditSmallButton.button:backdrop:hover,
GeditStatusMenuButton.button:backdrop,
GeditStatusMenuButton.button:backdrop:hover {
    border-color: @unfocused_borders;
}

GeditViewFrame .gedit-search-slider {
    background-color: @theme_base_color;
    padding: 6px;
    border-color: shade (@notebook_tab_gradient_b, 0.80);
    border-radius: 0 0 3px 3px;
    border-width: 0 1px 1px 1px;
    border-style: solid;
}

GeditViewFrame .gedit-search-slider .not-found {
    color: @gedit_not_found_fg;
    background-image: none;
    background-color: @gedit_not_found_bg;
}

GeditViewFrame .gedit-search-slider .not-found:selected {
    background-color: @theme_selected_bg_color;
    color: @theme_selected_fg_color;
}

GeditFileBrowserWidget .toolbar {
    padding: 3px;
    border-bottom: 1px solid @borders;
    box-shadow: inset 0 3px alpha(black, 0.03), inset 0 2px alpha(black, 0.03), inset 0 1px alpha(black, 0.03);
    background-color: shade(@theme_bg_color, 0.95);
}

.gedit-search-entry-occurrences-tag {
    color: shade (@theme_unfocused_fg_color, 0.8);
    margin: 2px;
    padding: 2px;
}

/*
 * GNOME Documents
 */

.documents-dropdown,
.documents-dropdown .view {
    background-color: shade (@theme_bg_color, 1.02);
}

.documents-dropdown.frame {
    padding: 6px;
    border-width: 0 1px 1px 1px;
    border-style: solid;
    border-radius: 0 0 5px 5px;
}

.documents-dropdown .view.radio,
.documents-dropdown .view.radio:focused,
.documents-dropdown .view.radio:selected {
    background-image: none;
    background-color: alpha(@theme_base_color, 0.0);
}

.documents-dropdown .view.radio:active,
.documents-dropdown .view.radio:active:focused,
.documents-dropdown .view.radio:active:prelight {
    background-image: url("assets/sidebar-radio-checked.svg");
}

.documents-dropdown .view.radio:prelight {
    background-image: url("assets/sidebar-radio-prelight.svg");
}

.documents-dropdown .view.radio:active:selected,
.documents-dropdown .view.radio:active:selected:focused {
    background-image: url("assets/sidebar-radio-selected.svg");
}

.documents-dropdown .view.radio:selected:prelight,
.documents-dropdown .view.radio:selected:focused {
    background-image: url("assets/sidebar-radio-selected-prelight.svg");
}

.documents-load-more.button {
    border-image: none;
    border-color: @borders;
    border-width: 1px 0 0;
    border-radius: 0;
}

.documents-scrolledwin.frame {
    border-width: 1px 0 0;
    border-radius: 0;
}

.documents-icon-bg {
    background-color: @documents_emblem_bg;
    border-radius: 4px;

    color: @theme_base_color;
}

.documents-collection-icon {
    background-color: @documents_collection_bg;
    border-radius: 8px;
}

.documents-counter {
    background-image: url('assets/dnd-counter.svg');
    background-size: contain;
    background-color: transparent;
    color: @theme_base_color;
    font: bold;
}

.documents-favorite.button:active,
.documents-favorite.button:active:hover {
    color: shade(@theme_selected_bg_color, 1.20);
}

.documents-entry-tag {
    background-color: @entry_tag_bg;
    color: @entry_tag_fg;

    border-radius: 4px;
    border-width: 0;

    margin: 2px;
    padding: 4px;
}

.documents-entry-tag:hover {
    background-color: shade(@entry_tag_bg, 1.10);
    color: @entry_tag_fg;
}

.documents-entry-tag.button,
.documents-entry-tag.button:hover,
.documents-entry-tag.button:active,
.documents-entry-tag.button:active:hover {
    background-color: transparent;
    background-image: none;
    border-image: none;
    border-width: 0;
}

.documents-entry-tag.button:hover {
    color: shade(@entry_tag_bg, 2.10);
}

/*
 * Baobab
 */

.cell.baobab-level-cell,
.cell.baobab-level-cell:hover,
.cell.baobab-level-cell:selected,
.cell.baobab-level-cell:selected:hover {
    border-color: darker(@borders);
    border-width: 1px;
    border-radius: 3px;
    border-style: solid;
    background-color: white;
}

.cell.baobab-level-cell.fill-block,
.cell.baobab-level-cell.fill-block:selected,
.cell.baobab-level-cell.fill-block:selected:hover {
    background-color: #edd400;
}

.cell.baobab-level-cell.fill-block.level-low,
.cell.baobab-level-cell.fill-block.level-low:hover {
    background-color: #73d216;
}

.cell.baobab-level-cell.fill-block.level-high,
.cell.baobab-level-cell.fill-block.level-high:hover {
    background-color: #cc0000;
}

.cell.baobab-level-cell.fill-block:backdrop,
.cell.baobab-level-cell.fill-block:hover:backdrop,
.cell.baobab-level-cell.fill-block.level-low:backdrop,
.cell.baobab-level-cell.fill-block.level-high:backdrop {
    background-color: @theme_unfocused_text_color;
}

.cell.baobab-cell-error {
    color: @error_color;
}

.cell.baobab-cell-warning {
    color: @warning_color;
}

.cell.baobab-cell-warning:selected,
.cell.baobab-cell-error:selected {
    color: @theme_selected_fg_color;
}

.cell.baobab-cell-warning:backdrop,
.cell.baobab-cell-error:backdrop,
.cell.baobab-cell-warning:selected:backdrop,
.cell.baobab-cell-error:selected:backdrop {
    color: @theme_unfocused_text_color;
}

BaobabWindow.background GtkStack > GtkGrid > GtkScrolledWindow.frame {
    border-radius: 0;
    border-width: 0 1px 0 0;
}

BaobabWindow GtkInfoBar.warning,
BaobabWindow GtkInfoBar.error { 
    border-bottom-width: 1px;
    border-bottom-style: solid;
    border-bottom-color: @borders;
}

BaobabRingschart {
    background-color: @theme_bg_color;
    padding: 13px 13px 13px 13px;
}

BaobabRingschart.subfolder-tip {
    border-radius: 3px;
    border-style: none;
    padding: 3px 3px 3px 3px;

    background-color: alpha(@theme_tooltip_bg_color, 0.90);
    color: @theme_tooltip_fg_color;

    text-shadow: 1px 1px black;
}

/*
 * Epiphany
 */

EphyToolbar .entry:first-child,
EphyToolbar .entry:focus:first-child,
EphyToolbar .entry:backdrop:first-child {
    border-image-width: 3px 0 3px 3px;
    border-right-width: 0;
    border-bottom-right-radius: 0;
    border-top-right-radius: 0;
    padding-left: 4px;
    padding-right: 4px;
}

EphyToolbar .entry:last-child,
EphyToolbar .entry:focus:last-child,
EphyToolbar .entry:backdrop:last-child {
    border-image-width: 3px 3px 3px 0;
    border-left-width: 0;
    border-bottom-left-radius: 0;
    border-top-left-radius: 0;
    padding-left: 4px;
    padding-right: 4px;
}

EphyToolbar .entry:focus {
    box-shadow: inset 1px 2px alpha(@theme_selected_bg_color, 0.1),
        inset 1px 1px alpha(@theme_selected_bg_color, 0.1),
        inset 0 -1px alpha(@theme_selected_bg_color, 0.2);
}

EphyToolbar .entry:focus:last-child {
    box-shadow: inset 0 2px alpha(@theme_selected_bg_color, 0.1),
        inset 0 1px alpha(@theme_selected_bg_color, 0.1),
        inset -1px -1px alpha(@theme_selected_bg_color, 0.2);
}

EphyToolbar .location-entry .button {
    color: @internal_element_color;
    -GtkButton-child-displacement-y: 0;
    border-image-source: url("borders/entry.png");
    border-image-slice: 3 3 3 3;
    border-image-repeat: stretch;
    border-width: 2px;
    border-radius: 3px;
    padding-left: 4px;
    padding-right: 4px;
    box-shadow: inset 1px 0 @inset_dark_color,
        inset 0 1px @entry_inset,
        inset 0 2px alpha(@entry_inset, 0.4);
}

EphyToolbar .location-entry .button:last-child {
    border-image-width: 3px 3px 3px 0;
    border-left-width: 0;
    border-bottom-left-radius: 0;
    border-top-left-radius: 0;
}

EphyToolbar .location-entry .button:first-child {
    border-image-width: 3px 0 3px 3px;
    border-right-width: 0;
    border-bottom-right-radius: 0;
    border-top-right-radius: 0;
    /* flip the box-shadow division*/
    box-shadow: inset -1px 0 @inset_dark_color,
        inset 0 1px @entry_inset,
        inset 0 2px alpha(@entry_inset, 0.4);
}

EphyToolbar .location-entry .button,
EphyToolbar .location-entry .button:hover {
    icon-shadow: none;
    background-image: -gtk-gradient(linear,
        left top, left bottom,
        from(@entry_background_a),
        to(@entry_background_b));
}

EphyToolbar .location-entry .button:active,
EphyToolbar .location-entry .button:active:hover {
    background-image: -gtk-gradient(linear,
        left top, left bottom,
        from(shade(@entry_background_a, 0.9)),
        to(@entry_background_b));
}

EphyToolbar .location-entry .button:hover,
EphyToolbar .location-entry .button:active {
    color: @theme_text_color;
}

EphyNotebook.notebook {
    border-width: 1px 0 1px 0;
}

EphyNotebook.notebook tab {
    border-width: 0;
}

EphyToolbar.toolbar .button {
    padding-left: 4px;
    padding-right: 4px;
}

#ephy-page-menu-button.active-menu {
    background-image: none;
    background-color: @menu_bg_color;

    border-image: none;
    border-color: @menu_bg_color;
    border-radius: 3px;
}

EphyOverview GtkScrolledWindow {
    background-color: @theme_base_color;
}

EphyOverview GtkScrolledWindow:backdrop {
    background-color: @theme_unfocused_base_color;
}

/* sets top and bottom borders on the main scrolled window for toolbar visual
 * division and search/downloadbar */
EphyWindow.background EphyEmbed.vertical GtkScrolledWindow.frame {
    border-color: @borders;
    border-width: 1px 0;
    border-radius: 0;
}

/* removes any border from the overview scrolled window, since it's overlaid */
EphyWindow.background EphyEmbed.vertical EphyOverview .documents-scrolledwin {
    border-style: none;
}

/* remove top and bottom borders from the main scrolled window when inside a notebook tab */
EphyWindow.background EphyNotebook.notebook EphyEmbed.vertical GtkScrolledWindow {
    border-top-width: 0;
    border-bottom-width: 0;
}

/* remove bottom borders from the  main scrolled window when no bars at the bottom of the screen are shown */
EphyWindow.background EphyEmbed.vertical GtkScrolledWindow,
EphyWindow.background  {
    border-bottom-width: 0;
}

/*
 * GNOME Contacts
 */

/* Line at top in contacts pane, similar to .documents-scrolledwin.frame */
.contacts-spinner.frame {
    border-width: 0 1px 0 0;
    border-style: solid;
    border-color: @borders;
    border-image: none;
    border-radius: 0;
    padding: 0;
}

/* Background color in contacts pane, similar to .documents-main-view.view */
.contacts-main-view.view {
    background-color: #f1f2f1;
}

.contacts-suggestion {
    background-color: #D3D7CF;
    border-radius: 4px;
}

/* Border on the right in the left menu toolbar */
.contacts-left-header-bar:dir(ltr) {
    border-right-width: 1px;
}

.contacts-left-header-bar:dir(rtl) {
    border-left-width: 1px;
}

.contacts-left-header-bar:dir(ltr),
.contacts-right-header-bar:dir(rtl) {
    border-top-right-radius: 0;
}

.contacts-right-header-bar:dir(ltr),
.contacts-left-header-bar:dir(rtl) {
    border-top-left-radius: 0;
}

.contacts-avatar-frame.frame {
    border-width: 1px 1px 0 1px;
    border-style: solid;
    border-color: @borders;
    border-image: none;
    border-radius: 0;
    padding: 0;
}

.main-avatar-frame.frame {
    border-width: 1px;
    border-style: solid;
    border-color: @borders;
    border-radius: 6px;
}

/* Primary toolbar with no line at top to avoid conflicts with frame border */
ContactsWindow .primary-toolbar.toolbar {
    border-width: 0 0 1px 0;
}

.contacts-button:active {
    border-color: #000000;
    border-image: none;
}

.contacts-entry {
    box-shadow: none;
    border-image: none;
    border-width: 1px;
    border-radius: 4px;
    border-style: solid;
    border-color: #bbbeb7;
    background-image: none;
    background-color: #ffffff;
}

.contacts-entry:selected,
.contacts-entry:selected:focus {
    background-color: @theme_selected_bg_color;
    color: @theme_selected_fg_color;
}

.contacts-entry.contacts-postal-entry {
    border-radius: 0 0 0 0;
    border-width: 1px 1px 0 1px;
}

.contacts-entry.contacts-postal-entry:nth-child(first) {
    border-radius: 4px 4px 0 0;
}

.contacts-entry.contacts-postal-entry:nth-child(last) {
    border-radius: 0 0 4px 4px;
    border-width: 1px;
}

.button.contacts-square {
    padding: 0px;
}

.contacts-combo .button {
    border-image: none;
    border-width: 1px;
    border-style: solid;
    border-color: #bbbeb7;
    background-image: none;
    background-color: #ffffff;
}

.toolbar.contacts-edit-toolbar {
    padding: 6px;
    background-color: #E2E4E2;
    border-width: 1px 0 0 0;
    border-style: solid;
    border-color: @borders;
    border-image: none;
}

.toolbar.contacts-edit-toolbar .button {
    padding-left: 6px;
    padding-right: 6px;
}

.toolbar.contacts-selection-toolbar {
    border-width: 1px 0 0 0;
    border-style: solid;
    border-color: @borders;
    border-image: none;
}

.contacts-watermark {
    color: #bebebe;
    text-shadow: 1px 1px alpha(white, 0.6);
}

/*
 * GNOME Photos
 */

.photos-icon-bg {
    icon-shadow: 0 1px #000000;
}

/*
 * Gucharmap
 */

GucharmapChartable:active,
GucharmapChartable:focus,
GucharmapChartable:selected {
    background-color: @theme_selected_bg_color;
    color: @theme_selected_fg_color;
}

/*
 * Evince
 */

EvWindow.background > GtkBox.vertical > GtkPaned.horizontal > GtkBox.vertical > GtkScrolledWindow.frame {
    border-width: 0;
    border-radius: 0;
}

EvWindow.background EvSidebar.vertical .frame {
    border-width: 1px 0 0;
    border-radius: 0;
}

EvWindow.background EvSidebar.vertical .notebook {
    border-width: 1px 0 0;
}

EvWindow.background EvSidebarAnnotations.vertical GtkToolPalette > GtkToolItemGroup > .button { 
    border-image: none;
    border-radius: 0;
    border-style: solid;
    border-width: 0 0 1px;
    border-color: @borders;
}

EvWindow.background EvSidebar.vertical .notebook .frame {
    border-width: 0;
}

EvWindow .pane-separator, 
EvWindow .pane-separator:hover {
    border-width: 0 1px;
    border-style: solid;
    border-color: @borders;
    background-color: shade(@theme_bg_color, 0.95);
    color: @borders;
}

EvWindow.background EggFindBar.toolbar {
    border-width: 1px 0 0;
    border-style: solid;
    border-color: @borders;
}

/* gcalctool */

MathWindow.background > GtkBox.vertical > GtkBox.vertical > GtkScrolledWindow {
    padding: 4px;
    background-color: @theme_base_color;
    border-radius: 3px;
}

MathWindow.background > GtkBox.vertical > GtkBox.vertical > GtkScrolledWindow:backdrop {
    padding: 4px;    
    background-color:  @theme_unfocused_base_color;
    border-radius: 3px;
}

/*
 * GNOME Bluetooth
 */

GtkEntry.entry.pin-entry {
    font: regular 50;
    padding-left: 25px;
    padding-right: 25px;
}

GtkLabel.pin-label {
    font: regular 50;
}

/*
 * Fallback Mode Panel
 */

.gnome-panel-menu-bar,
PanelApplet > GtkMenuBar.menubar,
PanelToplevel,
PanelWidget,
PanelAppletFrame,
PanelApplet {
    background-color: @os_chrome_bg_color;
    background-image: none;
    color: @os_chrome_fg_color;
}

ClockBox,
.gnome-panel-menu-bar.menubar,
PanelApplet > GtkMenuBar.menubar {
    font: bold;
}

.gnome-panel-menu-bar.menubar .menuitem:hover,
PanelApplet > GtkMenuBar.menubar .menuitem:hover {
    text-shadow: 0 1px @os_chrome_bg_color;
}

.gnome-panel-menu-bar.menubar .menu,
PanelApplet > GtkMenuBar.menubar .menu {
    font: regular;
}

.gnome-panel-menu-bar.menubar .menu:hover,
PanelApplet > GtkMenuBar.menubar .menu:hover {
    text-shadow: none;
}

.gnome-panel-menu-bar .menuitem:hover,
PanelApplet > GtkMenuBar.menubar .menuitem:hover,
.gnome-panel-menu-bar .menuitem:hover,
PanelApplet > GtkMenuBar.menubar .menuitem:hover {
    background-color: @os_chrome_selected_bg_color;
    color: @os_chrome_selected_fg_color;
}

.gnome-panel-menu-bar .menuitem:hover,
PanelApplet > GtkMenuBar.menubar .menuitem:hover {
    color: @os_chrome_selected_fg_color;
}

PanelApplet .button,
PanelApplet .button:hover {
    padding: 4px;

    border-image: none;
    border-width: 0;
    border-radius: 0;

    background-image: none;
    background-color: @os_chrome_bg_color;

    color: @os_chrome_fg_color;
    text-shadow: none;
}

PanelApplet .button:active:hover,
PanelApplet .button:active {
    border-image: none;
    background-image: none;
    background-color: @os_chrome_selected_bg_color;
    border-width: 0;
    border-radius: 0;
}

PanelApplet:hover {
    color: @os_chrome_selected_fg_color;
}

PanelApplet:active,
PanelApplet:hover:active {
    color: @os_chrome_selected_fg_color;
    text-shadow: 0 1px @os_chrome_bg_color;
}

WnckPager {
    background-color: lighter(@os_chrome_selected_bg_color);
}

NaTrayApplet {
    -NaTrayApplet-icon-padding: 12;
    -NaTrayApplet-icon-size: 16;
}

/*
 * Fail Whale
 */

GsmFailWhaleDialog {
    background-color: @os_chrome_bg_color;
    background-image: none;
    color: @os_chrome_fg_color;
}

GsmFailWhaleDialog .button,
GsmFailWhaleDialog .button:active {
    border-image: none;
    border-color: @borders;
    border-width: 1px;
}


/****************
 * Widgets      *
 ****************/

/*
 * Floating Bar
 */

.floating-bar {
    background-image: linear-gradient(to bottom, 
        @theme_base_color 20%, 
        shade(@theme_base_color, 0.9)
        );
    background-color: @theme_base_color;
    border-color: @borders;

    color: @theme_text_color;
    text-shadow: 0 1px @button_text_shadow;

    border-radius: 3px;
    border-width: 1px;
    border-style: solid;
    box-shadow: inset 1px 1px @inset_light_color, -1px -1px @inset_light_color;
}

.floating-bar.top {
    border-top-width: 0;
    border-top-right-radius: 0;
    border-top-left-radius: 0;
}

.floating-bar.right {
    border-right-width: 0;
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
}

.floating-bar.bottom {
    border-bottom-width: 0;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
}

.floating-bar.left {
    border-left-width: 0;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
}

.floating-bar.bottom.right {
    box-shadow: inset 1px 1px @inset_light_color;
}

.floating-bar.bottom.left {
    box-shadow: inset -1px 1px @inset_light_color;
}

.floating-bar:backdrop {
    background-color: @theme_unfocused_base_color;
    border-color: shade(@theme_unfocused_base_color, 0.9);
    background-image: none;
    box-shadow: none;
}

.floating-bar .button {
    background-color: alpha (@theme_base_color, 0.0);
    background-image: none;

    border-style: none;
    border-image: none;

    -GtkButton-image-spacing: 0;
    -GtkButton-inner-border: 0;
}

/* FIXME: why do we still need this? */
GtkClutterOffscreen {
    background-color: @theme_bg_color;
    color: @theme_fg_color;
}

/*
 * Egg
 */

EggListBox {
    background-color: @list_box_bg;
}

EggListBox:hover {
    background-color: @content_view_bg;
}

EggListBox:selected {
    background-color: @theme_selected_bg_color;
}


/*
 * Content view
 */

.content-view.subtitle {
    font: 9;
    padding: 0px 12px 0px 12px;
}

.content-view.view.rubberband {
    background-color: alpha (@theme_selected_bg_color, 0.35);

    border-color: @theme_selected_bg_color;
    border-style: solid;
    border-width: 1px;
    border-radius: 0px;
}

.content-view.view {
    background-color: @content_view_bg;
}

.content-view.view:insensitive {
    background-color: @theme_unfocused_base_color;
    background-image: none;
}

.content-view.view:selected {
    background-color: @theme_selected_bg_color;
    background-image: none;
}

.content-view.view:selected:backdrop {
    background-color: @theme_unfocused_selected_bg_color;
    background-image: none;
}

/* FIXME: EggListBox should set the .cell style class on
 * the background it renders for the children, like
 * GtkIconView and GtkTreeView do */
.content-view.cell {
    background-color: transparent;
    background-image: none;
}

EggListBox.content-view:hover,
.content-view.cell:hover {
    background-color: @theme_bg_color;
}

EggListBox.content-view:selected,
EggListBox.content-view:active,
.content-view.cell:selected,
.content-view.cell:active {
    background-color: @theme_selected_bg_color;
    background-image: none;
}

EggListBox.content-view:selected:backdrop,
.content-view.cell:selected:backdrop {
    background-color: @theme_unfocused_selected_bg_color;
    background-image: none;
}

GdMainIconView.content-view {
    -GdMainIconView-icon-size: 40;
}

GtkIconView.content-view.cell.check,
GtkIconView.content-view.cell.check:backdrop {
    background-image: url("assets/grid-selection-unchecked.svg");
    background-color: transparent;
}

GtkIconView.content-view.cell.check:active {
    background-image: url("assets/grid-selection-checked.svg");
    background-color: transparent;
}

/* Make spinner visible on both dark and bright backgrounds w/o making
 * it look ugly/weird.
 */
GdMainIconView.content-view.cell:active {
    color: gray;
}

.content-view.view.check,
.content-view.view.check:active {
    background-color: transparent;
}

.content-view.view .separator:backdrop {
    color: @theme_unfocused_bg_color;
}

GtkIconView.content-view.check:hover,
GtkIconView.content-view.check:insensitive,
GtkIconView.content-view.check:backdrop,
GtkIconView.content-view.check:selected {
    background-color: transparent;
}

/* used by Documents and Evince */
.content-view.document-page {
    border-style: solid;
    border-width: 3px 3px 6px 4px;
    border-image: url("assets/thumbnail-frame.png") 3 3 6 4;
}

/*
 * App Notifications
 */

.app-notification {
    border-style: solid;
    border-color: @app_notification_border;
    border-width: 0 1px 1px 1px;
    border-radius: 0 0 5px 5px;
    padding: 8px;

    background-image: linear-gradient(to bottom,
        @app_notification_a,
        @app_notification_b 18%,
        @app_notification_c);

    color: @theme_text_color;
    text-shadow: 0 1px @primary_toolbar_button_text_shadow;
}
```

I guess the change have to be done inside one of this two files.

---

### Post by tamir2 on 2015-01-07
The same question. How to change the color? Only I have another theme - Numix. But I think the general principle of one for all themes. However, all instructions on the Internet related to Ubuntu 12.04. But for ubuntu 14.04 I have not found. Can anyone help?

---

### Post by tamir2 on 2015-01-07
Also, I have a question about the color of icons in the sidebar. And the highlight color icons in the sidebar, I asked this question here - [http://ubuntuforums.org/showthread.php?t=2259057](http://ubuntuforums.org/showthread.php?t=2259057)

---

