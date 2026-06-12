---
title: "Terminal error: invalid string constant"
date: 2007-12-03
forum: General Help
---

### Post by cschoeps on 2007-12-03
Fairly new to Linux, and trying to figure out an error that I get every time I open something. I posted this elsewhere, but got no responses on it, so I took that one down and reposted here.

 I see this error when I open in terminal:

error: invalid string constant "dark_info_color", expected valid string constant

I've checked the .gtkrc-2.0 file to see if I have any missing quotes, as I saw suggested somewhere else, but my quotes look to all be in order. Any help is greatly appreciated. Thanks!

---

### Post by metalheart on 2007-12-03
Do you mean, that every time you run gnome-terminal you get this error?

---

### Post by cschoeps on 2007-12-03
It appears that this code is output the first time I run a program by typing it into gnome terminal. If I already have that program running, such as a firefox window open, and i open up a terminal and type in "firefox" then I do not get this error. This code does not come up if I just open a terminal.

---

### Post by metalheart on 2007-12-03
I cant find that file you mentioned from my system, but maybe you entered incorrect value for 'dark_info_color' value. Try "#888888" or change Ubuntu theme to something else (to Human for example) and try again.

---

### Post by cschoeps on 2007-12-03
I switched to Human, and still had the problem. I'm using Emerald theme manager, but changing that theme doesn't make a difference either. Also, dark_info_color is already set to #888888

---

### Post by metalheart on 2007-12-03
Can you uncomment this variable with # or something or temporarily delete it?

---

### Post by cschoeps on 2007-12-03
In the gtkrc-2.0 file, the place where the variable is defined is commented. The places that use it are: 


widget_class Menu Item
widget_class Tool Item
widget_class Separator Menu item
widget_class Separator Tool item
widget_class Image Menu item
widget_class Radio Menu item
widget_class Check Menu item 
widget_class Tear off Menu item

should I uncomment all of these?

---

### Post by cschoeps on 2007-12-03
Here is the .gtkrc-2.0 file:

include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "dark_info_color"
widget_class "*ToolItem*" style "dark_info_color"
widget_class "*SeparatorMenuitem* "dark_info_color"
widget_class "*SeparatorToolitem* "dark_info_color"
widget_class "*ImageMenuitem*" style "dark_info_color"
widget_class "*RadioMenuitem*" style "dark_info_color"
widget_class "*CheckMenuitem*" style "dark_info_color"
widget_class "*TearoffMenuitem*" style "dark_info_color"

---

### Post by metalheart on 2007-12-03
widget_class "*SeparatorMenuitem* "dark_info_color"
widget_class "*SeparatorToolitem* "dark_info_color"

maybe those should be

widget_class "*SeparatorMenuitem* style "dark_info_color"
widget_class "*SeparatorToolitem* style "dark_info_color"

---

### Post by cschoeps on 2007-12-03
Tried adding "style" before each of those, but it didn't do anything. end of the file now reads:

widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "dark_info_color"
widget_class "*ToolItem*" style "dark_info_color"
widget_class "*SeparatorMenuitem* style "dark_info_color"
widget_class "*SeparatorToolitem* style "dark_info_color"
widget_class "*ImageMenuitem*" style "dark_info_color"
widget_class "*RadioMenuitem*" style "dark_info_color"
widget_class "*CheckMenuitem*" style "dark_info_color"
widget_class "*TearoffMenuitem*" style "dark_info_color"

---

### Post by metalheart on 2007-12-03
OK. Try to ncomment

#NautilusIconContainer::dark_info_color="#888888"

like this

NautilusIconContainer::dark_info_color="#888888"

I'm really saying now all this just from the top of my head.

---

### Post by cschoeps on 2007-12-03
Hey anything is welcome, I haven't done this stuff long enough myself :)

Now I get this error: 

unexpected character `:', expected character `='

---

### Post by metalheart on 2007-12-03
OK. Now move this line inside the curly braces on top.

---

### Post by cschoeps on 2007-12-03
Hmm...nope, now it's back to the original error message. File now reads:

include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
NautilusIconContainer::dark_info_color= "#888888"
}
class "GtkWidget" style "desktop-icon"


#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200


style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "dark_info_color"
widget_class "*ToolItem*" style "dark_info_color"
widget_class "*SeparatorMenuitem* style "dark_info_color"
widget_class "*SeparatorToolitem* style "dark_info_color"
widget_class "*ImageMenuitem*" style "dark_info_color"
widget_class "*RadioMenuitem*" style "dark_info_color"
widget_class "*CheckMenuitem*" style "dark_info_color"
widget_class "*TearoffMenuitem*" style "dark_info_color"

---

### Post by metalheart on 2007-12-03
I found some other thread with same type of problem.

[http://ubuntuforums.org/archive/index.php/t-397971.html](http://ubuntuforums.org/archive/index.php/t-397971.html)

It seems they have some working .gtkrc-2 file.

The whole issue is getting now to me - this style variable "dark_info_color" is not for some reason defined. Not in this file and anywhere else.

I guess, the "dark_info_color" can be replaced with "my_color", but how does it look?

---

### Post by cschoeps on 2007-12-03
If I replace all of the dark_info_color with my_color, all of the menu toolbar items (File, Edit, View, etc.) turn white instead of black. I think I had to change the first two lines of the gtkrc file to "my_color" (which I'd input as white) because I had black panels on my desktop, and wanted the menu options to turn up white.

Replacing the rest of the entries with codes, like #000000 still yields an error for some reason, even when i'm not using dark_info_color at all

edit: it also looks like the menu bar is using the #888888 color instead of #000000 color, even though the entire file is either my_color or #000000

---

### Post by cschoeps on 2007-12-03
Ahh, I just ended up using the gtkrc rile from that link you sent me, and it ended up fixing everything. I didn't think that my file had been any different, but I must have missed something. Either way, it's fixed! Thanks for all the help!

---

