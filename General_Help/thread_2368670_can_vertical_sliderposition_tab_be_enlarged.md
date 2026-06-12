---
title: "can vertical slider/position tab be enlarged?"
date: 2017-08-13
forum: General Help
---

### Post by seekertom on 2017-08-13
Im using 17.04 on a desktop pc. Is there any way to make the vertical position tab/bar bigger? I'd like to blame it on my mouse, but actually it's my shakey hand that's the problem. Hard for me to get the lil arrow just right to scroll properly.
thanks for your help and understanding!
st  :confused:

I  haven't made any progress yet, but did notice one thing... i've been referring to my use of firefox, and that's where the vertical scroll bar is so small.

Then I opened Ubuntu Software, clicked on all, and the window that opens to show my stuff does have a usable size bar, certainly many times the thickness of firefox.

I also remember, probably from my ver 14 on my first linux laptop, that not only was the bar wider, but it also showed another device just to the right of the window, which allowed vertical scrolling from that one point.
All this means that the current problem may be a firefox issue, not ubuntu, but I still wonder why the hover-enabled scroll box went away...
just a thought while i shuffle along in my inconsequential way...
st

---

### Post by oldfred on 2017-08-13
I think I just did this in 17.10, but I use fallback or gnome-classic & whatever defaults that has. 
If you change theme, it may be a different .css.

[https://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04](https://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04)

       scroll bar
echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars 
[http://ubuntuforums.org/showthread.php?t=1965929](http://ubuntuforums.org/showthread.php?t=1965929)

You need to look in your theme's folder for files called gtkrc (in the gtk-2.0 folder) and gtk-widgets.css (in the gtk-3.0 folder). Open these files with a text editor. You may need to use gksudo gedit instead of just gedit if your theme is in /usr/share/themes and not in ~/.themes. Then, search for overlay scrollbars or overlay-scrollbar or something similar and play with the colors specified in those sections. You can even specify your own color in hex code.
gtkrc file
style "scroll"
{

 GtkScrollbar::slider-width = 25
GtkToolbar::icon-size = 48 
 }
class "*" style "scroll"

---

