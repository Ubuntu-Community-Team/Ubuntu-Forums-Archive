---
title: "Xubuntu Font Color"
date: 2016-02-12
forum: General Help
---

### Post by radacheck on 2016-02-12
For desktop icons, how can I change the font color.?

---

### Post by Dennis N on 2016-02-12
> **radacheck said:**
> For desktop icons, how can I change the font color.?
Great question! Well, Xubuntu doesn't make it easy, that's for sure. I'm currently using the Numix theme in Xubuntu 15.10, and successfully customized desktop icon text color. This is how it's done:

Edit [B]/usr/share/themes/Numix/gtk-2.0/gtkrc
[/B]

Find the stanza starting at **style "xfdesktop-icon-view"**

I substitute this stanza (which I originally used long ago in Albatross Theme) for the original:

```
style "xfdesktop-icon-view" {
#   Uncomment the line below for transparent icon backgrounds.
    XfdesktopIconView::label-alpha = 0
    XfdesktopIconView::selected-label-alpha = 40
	XfdesktopIconView::shadow-x-offset = 1
	XfdesktopIconView::shadow-y-offset = 1
	XfdesktopIconView::selected-shadow-x-offset = 1
	XfdesktopIconView::selected-shadow-y-offset = 1
	XfdesktopIconView::shadow-color = @fg_color
	XfdesktopIconView::selected-shadow-color = @fg_color


	base[NORMAL] = "#30334A"
	base[SELECTED] = "#d3efef" #shade (1.4, @selected_bg_color)
	
	fg[NORMAL] = "#E2EF70"
	fg[SELECTED] = "#FFFFFF"
	fg[ACTIVE] = "#FFFFFF"

}
```

Icon text color becomes yellow. Adjust colors to your desires. If I recall correctly, it works in Greybird theme as well in Xubuntu 14.04. Possibly it will also work in your theme.

---

### Post by ajgreeny on 2016-02-12
I have a .gtkrc-2.0 text file in my home which does the same thing with the following content.  Presumably the same text file in a theme folder would work only on that theme, not across all of them.
```
# This file should be placed in your xubuntu home folder
# and name ".gtkrc-2.0"
#
gtk-menu-popup-delay=0
gtk-menu-popdown-delay = 0
gtk-menu-bar-popup-delay = 0
gtk-enable-animations = 0
gtk-timeout-expand = 10
gtk-timeout-initial = 0
gtk-timeout-repeat = 0
#
#---------------------------------------------------------------
# Section "icon background colors"
#---------------------------------------------------------------
# The following two lines *should* be left uncommented
# if we want the XFCE desktop icon backgrounds to use
# alpha blending (e.g. invisible or some % thereof)

style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0
XfdesktopIconView::selected-label-alpha = 0
XfdesktopIconView::active-label-alpha = 0
#
#---------------------------------------------------------------
# Section "icon font colors"
#---------------------------------------------------------------

# The next three lines deal with the color of the desktop icon's
# text. You can comment them out if you want you use gtk theme
# colors. Below yields white un-selected normal, green selected,
# and blue when going to another window
#
# I chose three different colors so that you can see the level
# of customization we can do.

fg[NORMAL] = "#ffffff"        #this is white
fg[SELECTED] = "#00ff00"      # this is green
fg[ACTIVE] = "#0000ff"        # this is blue

## my blue fonts to use with nuvola theme & royal blue WM
# environment. a soft shark underbelly blue color if you will.
#fg[NORMAL] = "#528AC6"
#fg[SELECTED] = "#528AC6"
#fg[ACTIVE] = "#528AC6"

}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

#---------------------------------------------------------------
# Section "xfce panel colors"
#---------------------------------------------------------------

# Use these to change the panel color.  Note this should
# be commented out entirely if you decide to use 
# Section "xfce panel background" below.

#style "panel"
#{
#this one here is grey
#bg[NORMAL] = "#909599"
# use this with nuvola theme
#bg[NORMAL] = "#64AEE0"
#xthickness = 0
#ythickness = 0
#}
#
#widget_class "*Panel*" style "panel"
#widget "*Panel*" style "panel"
#class "*Panel*" style "panel"

```

---

### Post by Dennis N on 2016-02-12
Hi ajgreeny;

Yes, this is another way to do it, and a good one. You are right in that what I posted applies to a single theme. But it also applies globally instead of to a single user. 

B.T.W., I have been using ~/.gtkrc-2.0 to theme my Whisker Menu.

I can see still another way (see EDIT below) to modify the desktop icon properties and text color (for single user) by putting the modified gtkrc into ~/.themes/Numix/gtk-2.0/ where Numix is empty except for the gtk-2.0 folder, and the gtk-2.0 folder is empty except for the gtkrc file. It will then override the global file. Rename the Numix folder if the theme is changed.

[COLOR="#696969"]EDIT: This Idea works correctly only if you have the entire intact theme folder including the modified gtkrc file in ~/.themes. The system uses the Greybird theme from ~/.themes only, and doesn't use the files in /usr/share/themes/Greybird at all. Even though the icon text does change color, the rest of the theme is not implemented. Not what I want.
[/COLOR]
Thanks for your post!

---

