---
title: "How do I get Windows theme and icons to work?"
date: 2017-10-31
forum: General Help
---

### Post by 1jarwolf on 2017-10-31
Alright, I have managed to actually have the windows 10 theme and icons set and they're working, but I am kind of picky. An image in the attachment will show how the title of something; the font of it is kind of...well... unreadable to me.

---

### Post by vasa1 on 2017-10-31
> **1jarwolf said:**
>  ... the font of it is kind of...well... unreadable to me.I think it has to be due to a "shadow" effect. If you can look at the theme contents, you maybe able to edit out the shadow effect. Sorry, but I can't be more specific since the source of the theme isn't mentioned.

---

### Post by 1jarwolf on 2017-10-31
The link as to where I downloaded it from is [https://www.2daygeek.com/install-windows-10-theme-icon-theme-on-ubuntu-fedora-debian-centos-opensuse-mageia-arch-linux-mint/#](https://www.2daygeek.com/install-windows-10-theme-icon-theme-on-ubuntu-fedora-debian-centos-opensuse-mageia-arch-linux-mint/#)

---

### Post by vasa1 on 2017-10-31
Again, there's more than one theme there :)

I'm guessing you need to play around with the relevant *themerc*.

```
# Name: Windows 10 Dark xfwm4 Theme
# Author: Elbullazul <cmedelahumada@gmail.com>
# License: GPL-3.0+

active_text_color=#878787
inactive_text_color=#cfcfcf
button_offset=10
button_spacing=15
show_app_icon=true
full_width_title=true
maximized_offset=10
title_horizontal_offset=3
title_shadow_active=false
title_shadow_inactive=false
title_vertical_offset_active=0
title_vertical_offset_inactive=0
title_shadow_active=false
title_shadow_inactive=false
shadow_delta_height=0
shadow_delta_width=0
shadow_delta_x=0
shadow_delta_y=0
shadow_opacity=30

```I don't use Xubuntu. Maybe someone who does can take this further.

---

### Post by 1jarwolf on 2017-11-01
Oh...How the heck were you able to get to that configuration file? I will have to look around in that theme folder and look for the config file and as you said, just put random numbers in there to see if it fixes the problem. Thanks!!!!!

---

