---
title: "Editing GTK theme"
date: 2008-04-26
forum: General Help
---

### Post by Niniel on 2008-04-26
Hello,

I'm using the Solaris theme ("Modified CDE theme of Alexandr Darkman, [email]darkman@darkman.org.ua[/email] to look like gtk-motif") but I wanted to have a fully transparent panel instead of the grey menu (Applications/Places/System) that this theme comes with. So I looked around the gtkrc a bit in a effort to find a way to accomplish this.
And I did find a way - I disabled the menubar pixmap. But it has a side effect - now the menu backgrounds are flat. 

```
# menu style definition for: menu bars and popup menus
# 
# Gtk Widget(s): GtkMenuBar, GtkMenu
#

style "menu" = "default"
{

 #font = "-*-helvetica-medium-r-normal-*-14-*-*-*-*-*-iso8859-1"
 font = "sans:size=14"

 engine "pixmap"
 {
	image
	{
		function	= BOX
		recolorable	= TRUE
# disabled to achieve a fully transparent panel
# negative side effect - flat menus
#		file		= "menubar.png"
		border		= { 2, 2, 2, 2 }
		stretch		= TRUE
```

While I can live with that I am wondering if there was a better way to to get the transparent panel, one that won't flatten the menu. 
I'll attach the rc file in case somebody wants to take a look.

Thank you.

---

### Post by sdennie on 2008-04-26
Did you try right clicking on the panel and going to Properties->Background?  There are a lot of options to adjust the look of the panel there.

---

### Post by Niniel on 2008-04-26
Really? Am I missing something?
I already have the background set to Solid and then cranked transparency all the way up. But the menu section was/is governed by the theme.

---

