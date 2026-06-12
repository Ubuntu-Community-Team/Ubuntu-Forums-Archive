---
title: "Clock Size"
date: 2018-01-31
forum: General Help
---

### Post by mountainman70 on 2018-01-31
I have just installed Ubuntu 17.10 on a spare Hard Drive to see the difference between it and 16.04. 
Also I have 18.04 on another spare HD to check it.
I have always run this script to increase the clock size so my old eyes can see it better. 
I have used it on several Ubuntu upgrades including 16.04.

Here is the script:

Create a file named .gtkrc-2.0 in the Home folder & copy paste the following lines into it:

style "my-panel-clock"
{
fg[NORMAL] = "272727'
font_name = "DS-Digital Bold 18"
}
widget "*.clock-applet-button.*" style "my-panel-clock"

Do ALT+F2 & run:

 pkill mate-panel


It will not work in 17.10. Is there a work around to fix this?

---

### Post by TheFu on 2018-01-31
This is wrong:
> That's an X11 resource solution.  17.10 doesn't use X11 anymore by default.  It uses Wayland.  You can choose to use X11 by selecting a different DE/WM prior to logging in.  Click on the "gear" on the login page to choose xorg/X11.  I don't have 17.10, so I've never seen it, but I've heard it works.

It is clearly NOT an X11 resource.  I mixed up this question with another that seemed similar, but wasn't.

Sorry.

---

### Post by mountainman70 on 2018-01-31
> **TheFu said:**
> That's an X11 resource solution.  17.10 doesn't use X11 anymore by default.  It uses Wayland.  You can choose to use X11 by selecting a different DE/WM prior to logging in.  Click on the "gear" on the login page to choose xorg/X11.  I don't have 17.10, so I've never seen it, but I've heard it works.

Thanks for replying TheFu. 
I tried that but no luck. Since I run Mate Desktop it won't work. I guess I will have to wait for someone to come up with a work around or a new script.

---

### Post by vasa1 on 2018-02-01
> **mountainman70 said:**
> Thanks for replying TheFu. 
I tried that but no luck. Since I run Mate Desktop it won't work. I guess I will have to wait for someone to come up with a work around or a new script.

I don't use Mate, but I think it's moved completely to gtk3. So editing .gtkrc-2.0 shouldn't be relevant or effective.

[http://www.omgubuntu.co.uk/2017/03/mate-1-18-desktop-released-now-gtk3](http://www.omgubuntu.co.uk/2017/03/mate-1-18-desktop-released-now-gtk3)

---

### Post by strixtux on 2018-02-01
Use "Settings" "Menu bar", the height of the menu bar can be adjusted- Increase it to a convenient size, hit "return" and enjoy.

---

