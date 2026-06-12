---
title: "gedit strange behavior"
date: 2013-04-14
forum: General Help
---

### Post by r.stiltskin on 2013-04-14
Just installed gedit on an old "mostly xfce" system.  History: this started out as Kubuntu 12.04, but over time Unity was installed & uninstalled, then Gnome, then Gnome Classic, but by now most of the unessential components of those have been uninstalled and the machine has been happily running an xfce desktop (with xfwm, lightdm, etc) but still some kde applications including dolphin, kate, kile, konsole.

When I select some text in gedit, either with the mouse or shift-arrow on the keyboard, instead of being highlighted the text disappears.  It's not actually being deleted, just "whited-out", because I can still cut-paste or copy-paste the invisible text (and then it becomes visible again).

I tried starting gedit from a konsole window and I get these error messages as soon as it starts up:
```

$ gedit

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_file: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_position: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_line: assertion `section != NULL' failed

(gedit:8165): Gtk-WARNING **: Theme parsing error: <data>:1:0: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_file: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_position: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_line: assertion `section != NULL' failed

(gedit:8165): Gtk-WARNING **: Theme parsing error: <data>:1:0: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_file: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_position: assertion `section != NULL' failed

(gedit:8165): Gtk-CRITICAL **: gtk_css_section_get_end_line: assertion `section != NULL' failed

(gedit:8165): Gtk-WARNING **: Theme parsing error: <data>:1:0: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

```

No additional errors are reported while opening, creating, editing or closing files.

Any ideas about what this means & what I need to install (or uninstall) to fix it?

---

### Post by vasa1 on 2013-04-14
What theme are you using? Does it cover gtk3?

---

### Post by r.stiltskin on 2013-04-14
oxygen-gtk which I believe is gtk3.

---

### Post by vasa1 on 2013-04-14
If you want you can try this:
Make a backup of gtk.css which should be in /usr/share/themes/Your_Theme/gtk-3.0 or in ~/.themes.
Then edit gtk.css to change *@define-color selected_bg_color* to an appropriate color. This line should be near the top of the file in a section called *default color scheme*. If the file is in ~/.themes, you won't need sudo or gksudo.
To see the effect, you'll have to change to another theme and back **or** log out and back in again.
If the edit doesn't do anything for you, just restore the back-up file.

---

### Post by r.stiltskin on 2013-04-14
/usr/share/themes/oxygen-gtk/gtk-3.0/gtk.css has no "@define..." entries and no section called default color scheme (or anything like that).

~/.themes directory exists but is empty.

But that gave me an idea.  In Gedit, Edit/Preferences/Font & Colors lists 5 color schemes: Classic, Cobalt, Kate, Oblivion, and Tango.  If I select Cobalt or Oblivion I get light-colored foreground text on a dark background, and then highlighted text is visible.  But those color schemes look horrible.  Is there any other way to individually set gedit's foreground/background/highlighted colors, or a package that provides additional color scheme choices?

Edit:
PS: I tried gnome-colors and the entire list of packages that come along with it:
gnome-brave-icon-theme (5.5.1-1ubuntu1)
gnome-colors (5.5.1-1ubuntu1)
gnome-colors-common (5.5.1-1ubuntu1)
gnome-dust-icon-theme (5.5.1-1ubuntu1)
gnome-human-icon-theme (5.5.1-1ubuntu1)
gnome-illustrious-icon-theme (5.5.1-1ubuntu1)
gnome-noble-icon-theme (5.5.1-1ubuntu1)
gnome-wine-icon-theme (5.5.1-1ubuntu1)
gnome-wise-icon-theme (5.5.1-1ubuntu1)

but they didn't help.  No change in gedit's Font & Colors selections.

---

### Post by vasa1 on 2013-04-14
> **r.stiltskin said:**
> /usr/share/themes/oxygen-gtk/gtk-3.0/gtk.css has no "@define..." entries and no section called default color scheme (or anything like that).

...
Interesting. Could you post the top ten lines (or a little more) of that file?

---

### Post by Dennis N on 2013-04-14
> **r.stiltskin said:**
> 
When I select some text in gedit, either with the mouse or shift-arrow on the keyboard, instead of being highlighted the text disappears.  It's not actually being deleted, just "whited-out", because I can still cut-paste or copy-paste the invisible text (and then it becomes visible again).


The problem may not have anything to do with the general theme you are using. There is a gedit xml theme file. See:

[http://ubuntuforums.org/showthread.php?t=1974376](http://ubuntuforums.org/showthread.php?t=1974376)

and **post #4** may be your solution.

---

### Post by r.stiltskin on 2013-04-15
@vasa1: Here is the entire file gtk.css:
```
/*
* this file is part of the oxygen gtk engine
* Copyright (c) 2010 Hugo Pereira Da Costa <hugo@oxygen-icons.org>
* Copyright (c) 2010 Ruslan Kabatsayev <b7.10110111@gmail.com>
*
* This library is free software; you can redistribute it and/or
* modify it under the terms of the GNU Lesser General Public
* License as published by the Free Software Foundation; either
* version 2 of the License, or( at your option ) any later version.
*
* This library is distributed in the hope that it will be useful,
* but WITHOUT ANY WARRANTY; without even the implied warranty of
* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
* Lesser General Public License for more details.
*
* You should have received a copy of the GNU Lesser General Public
* License along with this library; if not, write to the Free
* Software Foundation, Inc., 51 Franklin St, Fifth Floor, Boston,
* MA 02110-1301, USA.
*/

/*
INFO: css border and padding ordering is either:
   - all-sides;
   - top/bottom left/right;
   - top left/right bottom;
   - top right bottom left;
*/

* {
    -GtkPaned-handle-size: 3px;
    -GtkButton-child_displacement_x: 0px;
    -GtkButton-child_displacement_y: 0px;

    -GtkButton-default_border: 0px;
    -GtkButton-default_outside_border: 0px;
    -GtkButton-inner-border: 1px 2px 0px;

    -GtkCalendar-inner-border: 0px;
    -GtkCalendar-horizontal-separation: 0px;
    -GtkComboBox-appears-as-list: 1px;


    -GtkMenu-horizontal-padding: 3px;
    -GtkMenu-vertical-padding: 5px;
    -GtkMenu-horizontal-offset: -7px;
    -GtkMenuBar-internal-padding: 0px;

    -GtkScrolledWindow-scrollbar-spacing: 1px;

    -GtkCheckButton-indicator-size: 18px;
    -GtkCheckMenuItem-indicator-size: 16px;
    -GtkExpander-expander-size: 15px;
    -GtkTreeView-expander-size: 15px;

    -GtkTreeView-allow-rules: 1px;

    -GtkStatusbar-shadow-type: GTK_SHADOW_NONE;

    -GtkWindow-resize-grip-height: 0px;
    -GtkWindow-resize-grip-width: 0px;

    /*
    Apparently the following have become obsolete
    -GtkTreeView-row-ending-details: 1px;
    -GtkStatusbar-has-resize-grip: false;
    -GtkEntry-honors-transparent-bg-hint: 1px;
    */

    engine: oxygen-gtk;
}

GtkScrolledWindow { border-width: 1px; }

/* customize border styles */
.toolbar { border-style: none; }
.menubar { border-style: none; }
GtkStatusBar { border-style: none; }

/*
    TODO:
    look at default values from GtkCssProvider for better style definitions
    (class based, rather than widget based)
*/

/* specialization of default widgets style properties */
GtkToggleButton { -GtkButton-inner-border: 1px 0px 0px; }

GtkScale {
    -GtkRange-slider-width: 23px;
    -GtkScale-slider-length: 21px;
}

GtkScrollbar {
    -GtkRange-stepper-size: 12px;
    -GtkRange-trough-border: 0px;
}

/* entries */
/* do not change unless also changing Entry_SideMargin in OxygenStyle.h */
GtkEntry {
    padding: 2px 5px;
}

/* menuitems padding */
GtkMenuBar {
    padding: 1px;
    border-width: 0px;
}
GtkMenuBar>GtkMenuItem { padding: 2px 5px; }
GtkMenu>GtkMenuItem { padding: 5px 1px; }
GtkMenu>GtkSeparatorMenuItem { padding: 1px 1px; }

/* menu toolbutton */
GtkMenuToolButton, GtkMenuToolButton * {
    border-width: 0px;
    -GtkButton-focus-padding: 0px;
    -GtkWidget-focus-line-width: 0px;
}

/* notebooks */
GtkNotebook { padding: 4px 6px 0px 6px; }

/* option menu */
GtkOptionMenu { padding: 0px 4px; }

/* separators */
GtkSeparator { border-width: 3px; }

/* frames */
GtkFrame { padding: 1px; }
GtkScrolledWindow { padding: 1px; }
GtkViewport { padding: 1px; }
GtkProgressBar { padding: 0px; }

/* combo boxes */
GtkComboBox { padding: 0px 0px; }
GtkComboBox>GtkFrame { padding: 0px 0px 0px 4px; }
GtkComboBox>GtkEntry {
    padding: 2px 5px;
}
/* headers */
GtkTreeView>GtkButton { border-width: 0px 2px; }
GtkList>GtkButton { border-width: 0px 2px; }

NautilusPathBar>GtkToggleButton{ padding: 0px 10px 0px 0px; }

```

---

### Post by r.stiltskin on 2013-04-15
@Dennis N:
Good find.   Thanks, that is indeed the key to at least a partial solution.  I edited the /usr/share/gtksourceview-3.0/styles/classic.xml file, adding these 3 lines which were clearly lacking:
```
  <style name="selection"  foreground="white" background="grey"/>
  <color name="grey"       value="#808080"/>
  <color name="white"      value="#000000"/>

```
so now the selected text appears in white characters on a grey background.  Not scintillating but at least visible.

That still doesn't do anything about all those gtk_css_section... errors and theme parsing errors, which presumably are due to defects in the gtk.css file, but gedit seems to be functioning correctly so far.

---

### Post by vasa1 on 2013-04-24
> **r.stiltskin said:**
> @Dennis N:
Good find.   Thanks, that is indeed the key to at least a partial solution.  I edited the /usr/share/gtksourceview-3.0/styles/classic.xml file, adding these 3 lines which were clearly lacking:
```
  <style name="selection"  foreground="white" background="grey"/>
  <color name="grey"       value="#808080"/>
  <color name="white"      value="#000000"/>

```
so now the selected text appears in white characters on a grey background.  Not scintillating but at least visible.

That still doesn't do anything about all those gtk_css_section... errors and theme parsing errors, which presumably are due to defects in the gtk.css file, but gedit seems to be functioning correctly so far.

@r.stiltskin, if you don't mind, I suggest marking this thread as [SOLVED] :) My reason is that Dennis N has pointed the way to your main problem. The other problem regarding "funnies" in the terminal is a longstanding issue not specific to gedit. Many programs throw up all sorts of errors (in the terminal) even though these programs work as expected otherwise as you have observed for gedit.

It's your call but the solution pointed out by Dennis N has helped me as well! I've just installed gedit and gedit-plugins (no recommends) on Lubuntu to see markdown stuff.

---

