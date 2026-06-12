---
title: "Differentiating Geany's tabs"
date: 2014-11-04
forum: General Help
---

### Post by vasa1 on 2014-11-04
Sometime ago I had a thread titled [Active tab color in Geany 1.23.1]("http://ubuntuforums.org/showthread.php?t=2184415").

I'm now using Geany 1.24.1 and have got a bit further in customizing Geany's tabs and the text color and size within the tabs. I think they can be classified as follows (assuming there are several tabs open).

[LIST=1]
[*]The active tab with unmodified document text
[*]The active tab with modified but unsaved document text
[*]The active tab with modified and saved document text; same state as #1
[*]Background tabs with unmodified document text
[*]Background tabs with modified but unsaved document text
[*]Background tabs with modified and saved document text; same state as #4
[/LIST]

Because Geany is still a gtk2 app, I altered my theme's gtkrc and made some entries in *~/.gtkrc-2.0.mine*

The changes to the gtkrc file will depend on each theme and what is provided in the section titled **style "notebook-bg"**. The lines I have are:
```

    bg[NORMAL] = shade (0.5, @bg_color)
    bg[ACTIVE] = shade (0.97, @bg_color)
    fg[ACTIVE] = mix (0.8, @fg_color, shade (0.97, @bg_color))
    fg[NORMAL] = shade (0.9, @my_color_1) # not present in original

```where 
bg_color is #555555
fg_color is #000010 and
@my_color_1 is orange

Then, in *~/.gtkrc-2.0.mine*, I have:
```
#Styling text (fg) in Geany's tabs
#Note that styling bg is done in the theme's gtkrc, not here

# Custom styles

# document status colors
style "geany-document-status-changed-style" {
    fg[NORMAL] = "#AAAAAA" #tab text when changes are made but not saved and tab is active
    fg[ACTIVE] = "#FF0000" #tab text when changes are made but not saved and tab is not in focus
}
widget "*.geany-document-status-changed" style "geany-document-status-changed-style"
style "geany" = "geany-tabs"

{
font_name = "Ubuntu Mono 14"
}
widget "GeanyMainWindow.GtkVBox.GtkVPaned.GtkHPaned.GtkNotebook.*" 
style "geany"

```
The first image, 1.png, shows Geany with several tabs open and with the tab titled "menu.xml" active but unmodified. All the other tabs are unmodified.

The second image, 2.png, shows Geany with the same tabs open in which 
I've edited "menu.xml" but not saved it; the tab is still in focus 
I've edited "Contacts" and "history.log" both of which are unsaved but not in focus.

Edit: I'm using Greybird from shimmer-themes.

---

