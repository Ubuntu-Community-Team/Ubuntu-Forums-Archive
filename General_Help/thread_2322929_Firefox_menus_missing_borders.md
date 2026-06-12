---
title: "Firefox menus missing borders"
date: 2016-05-01
forum: General Help
---

### Post by ccrs8 on 2016-05-01
In Firefox 46.0 on Xubuntu 16.04, the menus (from the menu bar or the pop-up menu upon a right-click) are missing their borders.  It's not terribly annoying most of the time, but when the menus have nested sub-items, once it expands things get a bit messy.  Any ideas how to fix this?  I'm pretty sure this started happening just upon upgrading to Firefox 46.0.

[ATTACH=CONFIG]268758[/ATTACH]

[ATTACH=CONFIG]268757[/ATTACH]

 Edit: I'm using Classic Theme Restorer add-on (hence the retro look), but this is also happening when I start Firefox in safe mode with all add-ons disabled.

---

### Post by ZoiaGuyver on 2016-05-01
Not really sure of how to fix that.. 

Looks like it could be something to do with the theme you're using. Firefox 46 brought in some changes to better support GTK3 so that may be causing some of the problems.

---

### Post by vasa1 on 2016-05-01
> **ZoiaGuyver said:**
> Not really sure of how to fix that.. 

Looks like it could be something to do with the theme you're using. Firefox 46 brought in some changes to better support GTK3 so that may be causing some of the problems.

Yes, you could play with different gtk3 themes. Make sure you use a theme which is written for the gtk version present in your OS. I'm on 16.04 and the gtk3 version is 3.18.

Or: you could fix your theme. If you're interested, I'll post details. Right now, I'm a little busy.

---

### Post by Dennis N on 2016-05-01
It doesn't look like the compositor is enabled. It will shade around the borders and improve the situation greatly.

Settings > Window Manager Tweaks > Compositor

and check in the box to enable it.

---

### Post by vasa1 on 2016-05-01
@Dennis N, I made the borders thick by tweaking Greybird's gtk-widgets.css:```
/********
 * menu *
 ********/
GtkTreeMenu.menu,
GtkMenuToolButton.menu,
GtkComboBox .menu {
    background-color: @menu_bg_color;
}

.primary-toolbar .menu,
.primary-toolbar .button .menu,
.toolbar .menu,
.toolbar .primary-toolbar .menu,
.header-bar .menu,
.header-bar .primary-toolbar .menu,
.menu {
    padding: 0;
    border-radius: 0;
    border-width: 5px; **/*was 1px*/**
    border-style: solid;
    border-color: @darkblue;**/*was shade(@menu_bg_color, 0.7);*/**
    background-color: @menu_bg_color;
    color: @menu_fg_color;
}
```

---

### Post by Dennis N on 2016-05-01
Wow, those really stand out. I would go a bit less -- 3 px? I think the Xubuntu compositor is not enabled in ccrs8's case. I'd be surprised if it was. It helps a lot.

---

### Post by vasa1 on 2016-05-01
> **Dennis N said:**
> Wow, those really stand out. I would go a bit less -- 3 px? I think the Xubuntu compositor is not enabled in ccrs8's case. I'd be surprised if it was. It helps a lot.
Oh, I made those so that it would be very obvious. I stay with the commented out default values.

I use Compton but in a very minimal way, mostly to get a true transparency in the terminal and to have inactive windows dimmer. I also use it to make the mahjongg and google chrome screens somewhat transparent against a dark background so that the whiteness doesn't make my eyes bloodshot.

---

### Post by ccrs8 on 2016-05-01
Thanks for all of the replies.  I think it is definitely something with my theme (or what appears to now be called a "style" in 16.04?).  Anyway, I am using the "Raleigh" theme, but when changing to some of the other four listed in the Style tab of the Appearance setting window, it looks like two of the the themes do show menu borders in Firefox while two don't.  So probably a theme issue?

You are correct, I do not have the compositor turned on.  That was by choice - I like things very, very simple and plain (my desktop is a plain color, no icons, etc - I consider Windows 2000 to be the epitome of desktop design).  But I turned it on to check it out, and yes - once I turned it on and then checked to show shadows on pop-up windows, that did make a world of difference.  Still no border, but the shadows had the same impact as a border.  Thanks for the recommendation.

---

