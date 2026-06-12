---
title: "Play Games On TV"
date: 2017-03-09
forum: General Help
---

### Post by moemoemoe2 on 2017-03-09
Hello All (This is my fist post!),

I would like to be able to use my TV to play games.  As it is, in order to get the games to open full screen on my TV I have to unplug my monitor.  Id like to be able to do it without unplugging my monitor.  Im currently running Ubuntu 16.04

Please advise!

Thanks,

moemoemoe

---

### Post by efflandt on 2017-03-09
So you cannot switch to the TV as your primary display from System Settings > Displays or the X server settings for your graphics driver? What graphics card and driver are you using? If you have both on, make sure that you extend your desktop rather than mirrored, because mirrored may require same resolution on both.

I simply use a 32" 1080p HDTV as a monitor all the time. Even though its video input is 60 Hz, it has 2 ms response and can simulate 120 Hz by interpolation to improve sharpness and smoothness while reducing motion blur.

---

### Post by moemoemoe2 on 2017-03-10
Thanks for the quick reply efflandt.

I have evga gtx 1070 and the driver is X.org X server

If I go to System Settings > Displays there is no "primary display" option.  There is an option to switch which monitor the task bar appears on, but that does not change which screen games launch full screen on.

I tried looking for X server settings for my graphics driver by following this page: [https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto)
but the path suggested by the page: /usr/lib/X11/xorg.conf.d.leads me nowhere.  The X11 folder is empty (I checked for hidden files).

Perhaps I am using the wrong driver... :/

---

