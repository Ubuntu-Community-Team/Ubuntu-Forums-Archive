---
title: "Highlight color background well highlighting a thread in FF on forums"
date: 2016-02-24
forum: General Help
---

### Post by sammiev on 2016-02-24
Hi All,

Not sure if this is related to the forums here or Firefox.

I noticed while using different flavors of Ubuntu in Firefox, Firefox uses different colors for the background when the mouse is over a thread title.

I would like to change the black background to a brighter color like what is used in Ubuntu-gnome. Not sure where this is done.

A picture of Xubuntu is attached with the problem I would like to change.

Thanks

---

### Post by vasa1 on 2016-02-24
> **sammiev said:**
> Hi All,

Not sure if this is related to the forums here or Firefox.

I noticed while using different flavors of Ubuntu in Firefox, Firefox uses different colors for the background when the mouse is over a thread title.

...
Hi,

My feeling is that this setting is controlled by the gtk theme you're using. Which version of Firefox are you on? I feel that's relevant because your Firefox may be using gtk3 if your using a dev or nightly version.

I'm using the stable version, v 44, and that uses gtk2. The relevant settings are in /usr/share/themes/your_theme/gtk-2.0/gtkrc or in ~/.themes//your_theme/gtk-2.0/gtkrc.

```
# Author: Simon Steinbeiß
# Theme: MyBird --- a modified Greybird ;)
# based on "Bluebird" by Simon Steinbeiß and Pasi Lallinaho
# Description: As is the original theme, this theme is 100% free and open source.

gtk_color_scheme	= "bg_color:#404040\nselected_bg_color:#001B33\nbase_color:#222222" # Background, base.
gtk_color_scheme	= "fg_color:#000000\nselected_fg_color:#999999\ntext_color:#888888" # Foreground, text.
**gtk_color_scheme	= "tooltip_bg_color:#333333\ntooltip_fg_color:#aaaaaa" # Tooltips**
gtk_color_scheme	= "link_color:#220808" # Hyperlinks
gtk_color_scheme	= "panel_bg:#686868" # Panel bg color
gtk_color_scheme	= "fm_color:#F7F7F7\ngrey:#aaaaaa\nred:red\nblue:blue\nwhite:white"
gtk_color_scheme	= "bg_color_dark:#686868\ntext_color_dark:#FFF"
gtk_color_scheme	= "my_color_1:orange"
gtk_color_scheme	= "my_color_2:maroon"

```
My Firefox looks like Image_1

---

### Post by sammiev on 2016-02-24
Hi vasa1,

My Firefox version is 44.0.2

Think I found it and now have something to play with.

Thanks

---

### Post by vasa1 on 2016-02-24
Oops, I may have misled you. :(

Digging a bit deeper, it seems I can alter the foreground color in a stylesheet (so the foreground color will be limited to Firefox). I don't seem to be able to change the background color via a stylesheet. For that, the background color set in the gtkrc file seems to take precedence even in Firefox.

I'm a bit confused now and so will keep quiet ;)

---

### Post by sammiev on 2016-02-25
> **vasa1 said:**
> Oops, I may have misled you. :(

Digging a bit deeper, it seems I can alter the foreground color in a stylesheet (so the foreground color will be limited to Firefox). I don't seem to be able to change the background color via a stylesheet. For that, the background color set in the gtkrc file seems to take precedence even in Firefox.

I'm a bit confused now and so will keep quiet ;)

Many thanks vasa1 ;)

---

