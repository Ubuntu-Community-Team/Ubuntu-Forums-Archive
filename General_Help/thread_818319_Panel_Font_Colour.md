---
title: "Panel Font Colour"
date: 2008-06-04
forum: General Help
---

### Post by HpZ on 2008-06-04
I'm using a kind of darkish wallpaper and a fully transparent top panel. Thus, the font is a tad hard to see. Is there any way to change the font colour to white?

---

### Post by housam on 2008-06-04
system >>preference >>appearance >> themes use a dark one

---

### Post by rbmorse on 2008-06-04
Just in case you didn't find any previous responses to be helpful, the following works for me:

Open the terminal and type:

gedit .gtkrc-2.0

Insert the following into this file

```

style "panel"

{

# fg[NORMAL] = "#ffffff"

# fg[PRELIGHT] = "#000000"

# fg[ACTIVE] = "#ffffff"

# fg[SELECTED] = "#000000"

# fg[INSENSITIVE] = "#8A857C"

# bg[NORMAL] = "#000000"

# bg[PRELIGHT] = "#dfdfdf"

# bg[ACTIVE] = "#D0D0D0"

# bg[SELECTED] = "#D8BB75"

# bg[INSENSITIVE] = "#EFEFEF"

# base[NORMAL] = "#ffffff"

# base[PRELIGHT] = "#EFEFEF"

# base[ACTIVE] = "#D0D0D0"

# base[SELECTED] = "#DAB566"

# base[INSENSITIVE] = "#E8E8E8"

# text[NORMAL] = "#161616"

# text[PRELIGHT] = "#000000"

# text[ACTIVE] = "#000000"

# text[SELECTED] = "#ffffff"

# text[INSENSITIVE] = "#8A857C"

}

widget "*PanelWidget*" style "panel"

widget "*PanelApplet*" style "panel"

class "*Panel*" style "panel"

widget_class "*Mail*" style "panel"

class "*notif*" style "panel"

class "*Notif*" style "panel"

class "*Tray*" style "panel"

class "*tray*" style "panel"

```

Next, uncomment the part that says:

# fg[NORMAL] = &#8220;#ffffff&#8221;

So it looks like:

fg[NORMAL] = &#8220;#ffffff&#8221;

Save this file. It will be saved as .gtkrc-2.0 in your home directory. You do not need to do save as, unless your terminal is opened in another directory besides your home directory.

Note: you will not see this file in normal view. The &#8220;.&#8221; in front of the filename makes the file hidden. You can see all of your hidden files in Nautilus by selecting view -> show hidden files.

To explain, the #ffffff represents the color white. You can change this to whatever color you want. Gcolor2 is a great color chooser for Gnome. Ubuntu users will find this in universe:

sudo apt-get install gcolor2

The change desktop background dialog will also work to select this color notation, if you do not want to install gcolor2.

All we need to change is:

fg[NORMAL] = &#8220;#ffffff&#8221;

to allow our Gnome panel to have a different text color besides black (#000000), which is the default. The rest of the lines in this are out of the scope of this solution. However, they are useful for other things which will not be discussed for this post.

The last step is to refresh the Gnome panel:

killall gnome-panel

---

