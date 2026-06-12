---
title: "Color of scrollbars, Xubuntu 16.04, Numix, Greybird"
date: 2017-01-05
forum: General Help
---

### Post by gojira2016 on 2017-01-05
I am using Xubuntu 16.04 with
Window manager --> Style --> Numix
Appearance --> Style --> Greybird

I want to change the color of the scrollbars on the windows (because I have difficulties seeing them against the background... would like to change them to red or purple).

Is this possible? If yes, how?

---

### Post by Keith_Helms on 2017-01-05
Is it possible?  Yes, I believe so.

Is it easy?  No, I don't think so.

Unless there's an easier way I haven't discovered, you would have to go into /usr/share/themes, then Greybird, then gtk-3.0 and edit the color settings in gtk.css and the slidebar settings in gtk-widgets.css.  There are a LOT of slidebar settings - a couple of dozen.

```
grep slide gtk-widgets.css
    -GtkRange-slider-width: 9;
    -GtkScrollbar-min-slider-length: 50;
GtkSwitch.slider {
GtkSwitch.slider:insensitive {
    -GtkRange-slider-width: 13;
    -GtkScale-slider-length: 13;
.scale.slider {
.scale.slider:hover {
.scale.slider:insensitive {
.scale.slider.vertical {
.scale.slider.vertical:hover {
.scale.slider.vertical:insensitive {
.scale.slider.fine-tune:active,
.scale.slider.fine-tune:active:hover,
.scale.slider.fine-tune.horizontal:active,
.scale.slider.fine-tune.horizontal:active:hover {
    -GtkRange-slider-width: 5px;
.scrollbar.overlay-indicator:not(.dragging):not(.hovering) .slider {
.scrollbar.slider,
.scrollbar.slider.vertical,
.scrollbar.slider.horizontal,
.scrollbar.slider:hover,
.scrollbar.slider.vertical:hover {
.scrollbar.slider.horizontal:hover {
.scrollbar.slider.fine-tune:prelight:active {
GtkSwitch.slider {
GtkSwitch.slider:focus {
GtkSwitch.slider:insensitive {
.osd .scale.slider {
.osd .scale.slider:hover {
.osd .scale.slider:insensitive {
.osd .scrollbar.slider {
.osd .scrollbar.slider:hover {
.osd .scrollbar.slider:active,
.osd .scrollbar.slider:checked {
```

I played around with the colors and I was able to get my background to change from white to red, but I was not able to get the scrollbar color to change.  It looks like it would take a fair amount of reading plus some trial and error to get it to work.

---

### Post by vasa1 on 2017-01-05
There are two tweaks to make the scrollbars more visible, one for gtk2 apps and one for gtk3 apps.

For gtk2 apps first backup the entire Greybird theme folder, and then run ```
sudo -H mousepad /usr/share/themes/Greybird/gtk-2.0/gtkrc
```
Scroll down, ~ line 428, till you see this:

```
style "scrollbar"
{
	GtkScrollbar::stepper-size	= 0
	GtkScrollbar::arrow-scaling	= 0.0

	bg[NORMAL]	= @bg_color

	bg[ACTIVE]	= shade (1.75, @base_color)
	bg[PRELIGHT]	= shade (0.8, @bg_color)
	bg[INSENSITIVE]	= shade (0.75, @bg_color)

```
and change it to
```
style "scrollbar"
{
	GtkScrollbar::stepper-size	= 0
	GtkScrollbar::arrow-scaling	= 0.0

	bg[NORMAL]	= shade (0.5, @bg_color)

	bg[ACTIVE]	= shade (0.5, @bg_color)
	bg[PRELIGHT]	= shade (0.5, @bg_color)
	bg[INSENSITIVE]	= shade (0.5, @bg_color)

```This just makes the scrollbar more visible at all times.

A little more work is needed if you want to change the color! Do you really need different colors or just better contrast?

We take a similar approach for gtk3 apps. Run ```
sudo -H mousepad /usr/share/themes/Greybird/gtk-3.0/gtk-widgets.css
```
and scroll down, ~ line 1914, to```
.scrollbar.slider,
.scrollbar.button,
.scrollbar.slider.vertical,
.scrollbar.button.vertical {
    border-width: 1px;
    border-color: shade(@theme_bg_color, 0.7);
    border-radius: 10px;
    background-image: linear-gradient(to right,
                                      shade(shade(@theme_bg_color, 0.9), 1.2),
                                      shade(shade(@theme_bg_color, 0.9), 1.15)
                                      );

    color: shade(@theme_bg_color, 0.6);
}

```and change that to```
.scrollbar.slider,
.scrollbar.button,
.scrollbar.slider.vertical,
.scrollbar.button.vertical {
    background-color: shade(@theme_bg_color, 0.5);
}
```

---

### Post by Keith_Helms on 2017-01-05
Well, I was in the right place.  Where did you find that writeup, or did you just know it already? :P

---

### Post by vasa1 on 2017-01-05
> **Keith_Helms said:**
> Well, I was in the right place.  Where did you find that writeup, or did you just know it already? :P
I've been looking at how to "fix" scrollbars for quite a few years ;) GNOME keeps moving the goalposts!

Actually, my scrollbars are even simpler and, in a maximized window, the vertical ones extend right to the right edge of the screen (Fitts' Law is mentioned [here]("http://crunchbang.org/forums/viewtopic.php?id=38116")).

---

### Post by vasa1 on 2017-01-05
> **gojira2016 said:**
> I am using Xubuntu 16.04 with
Window manager --> Style --> Numix
Appearance --> Style --> Greybird

I want to change the color of the scrollbars on the windows (because I have difficulties seeing them against the background... would like to change them to red or purple).

Is this possible? If yes, how?If you really want to change the color, then you need to define colors.

Example for gtkrc:```
gtk-color-scheme	= "bg_color:#CECECE\nselected_bg_color:#398ee7\nbase_color:#fcfcfc" # Background, base.
gtk-color-scheme	= "fg_color:#3C3C3C\nselected_fg_color:#ffffff\ntext_color:#212121" # Foreground, text.
gtk-color-scheme	= "tooltip_bg_color:#000000\ntooltip_fg_color:#E1E1E1" # Tooltips.
gtk-color-scheme	= "link_color:#2d71b8" # Hyperlinks
gtk-color-scheme	= "panel_bg:#686868" # Panel bg color
gtk-color-scheme	= "fm_color:#F7F7F7" # Color used in Nautilus and Thunar.
gtk-color-scheme	= "bg_color_dark:#686868\ntext_color_dark:#FFF"
```
You can add your own color like this:```
gtk_color_scheme	= "my_color:maroon"
```for a "named" color, or use the hex code:```
gtk_color_scheme	= "my_color:#800000"
```
You can have as many colors as you like.

Once that's done, you can use *@my_color* instead of any other.

For gtk3 themes such as Greybird (but not for Numix or Arc, etc). You need to define the color in *gtk.css* (or in *gtk-main.css*, depending on the theme). Greybird has:```
/* default color scheme */
@define-color bg_color #cecece;
@define-color fg_color #3c3c3c;
@define-color base_color #fcfcfc;
@define-color text_color #212121;
@define-color selected_bg_color #398ee7;
@define-color selected_fg_color #fff;
@define-color tooltip_bg_color #000;
@define-color tooltip_fg_color #e1e1e1;
```
You can add```
@define-color my_color #800000;
```and then use that like this:```
.scrollbar.slider,
.scrollbar.button,
.scrollbar.slider.vertical,
.scrollbar.button.vertical {
    background-color: @my_color;
}
```

---

