---
title: "Changing editor pane background"
date: 2005-07-17
forum: General Help
---

### Post by RyaninZion on 2005-07-17
How in the world do you effectively alter the background color of the editor pane for applications such as Bluefish?  I understand that I can use a .gtkrc-2.0 file to change the base color for all gtk apps... but then, in Bluefish, I get an altered background color in the editor pane AND the file browser.

Is there not an easy way to ONLY changed the background color of the editor pane in Bluefish?

---

### Post by ketiko on 2005-07-18
What does the theme code that you changed look like?

The theme file should show something like:

style "bluefish"
{
 # For up and down arrows grouped together at right side
 GtkNotebook::has_secondary_forward_stepper = 1
 GtkNotebook::has_secondary_backward_stepper = 1
 
 # **Editor background** color 
 # (background of editor view)
 base[NORMAL]="**#fcfff5**"

}

I believe you just change the color there, but I'm not sure.

Here is a reference.
[BlueFish](http://66.102.7.104/search?q=cache:Dbyl5tTKYkEJ:bluefish.openoffice.nl/manual/ch03s06.html+change%2Bbackground%2Bbluefish&hl=en&client=firefox-a)

Scroll down to the "**Editor Appearance**" 

Sorry that this is the cached page.  I got it from google, but the real page it down I guess.

---

### Post by RyaninZion on 2005-07-19
[QUOTE=ketiko]What does the theme code that you changed look like?

The theme file should show something like:

style "bluefish"
{
 # For up and down arrows grouped together at right side
 GtkNotebook::has_secondary_forward_stepper = 1
 GtkNotebook::has_secondary_backward_stepper = 1
 
 # **Editor background** color 
 # (background of editor view)
 base[NORMAL]="**#fcfff5**"

}

I believe you just change the color there, but I'm not sure.

Here is a reference.
[BlueFish](http://66.102.7.104/search?q=cache:Dbyl5tTKYkEJ:bluefish.openoffice.nl/manual/ch03s06.html+change%2Bbackground%2Bbluefish&hl=en&client=firefox-a)

Scroll down to the "**Editor Appearance**" 

Sorry that this is the cached page.  I got it from google, but the real page it down I guess.[/QUOTE]
 That is the reference I followed before.  And I made a very similar addition to the theme file to what you did above.  The problem is that it colors not only the background of the editor pane, but also the background of the file browser/project viewer pane.  Not to mention the background of every other GTK program on my computer.

---

