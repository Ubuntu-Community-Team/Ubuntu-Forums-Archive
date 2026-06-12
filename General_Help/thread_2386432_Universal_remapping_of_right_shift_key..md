---
title: "Universal remapping of right shift key."
date: 2018-03-05
forum: General Help
---

### Post by sinykk on 2018-03-05
Hi there, 

My wife has a Lenovo Ideapad 710s, bought as a replacement for her macbook, and whoever designed those series of laptops needs to do some serious rethinking.

Off of google, this is what the bad design decision looks like. 

[https://i.imgur.com/ZqmHQkN.jpg](https://i.imgur.com/ZqmHQkN.jpg)

What I'm asking for help with has been asked in the forums before, but the solutions don't seem to work for me. I'm using Ubuntu Desktop 16.04.

I tried to edited ```
/usr/share/X11/xkb/symbols/pc
``` but that seems to have no effect what so ever.

I also follow [this]("https://askubuntu.com/questions/930829/problems-with-remapping-shift-with-up-keys") mini writeup, by someone who had the same issue as me. The solution says to create an sh file to run at start up with the following commands:

```
xmodmap -e "keycode 62 = Up"        # => Up
xmodmap -e "keycode 111 = Shift_R"  # => Shift
xmodmap -e "add shift = Shift_R"    # Make the new Shift key actually shift
xmodmap -e "remove shift = Up"      # Prevent the old Shift key from shifting
xset r 62                           # repeat Up key
xset -r 111                         # don't repeat new Shift key

```

But I'm running into a problem. This doesn't seem to change the Up key. Instead, it makes my Shift key both Up and Shift. The second issue with this, the changes don't seem to affect Chrome. So I need the changes to be universal, preferably pre-login, so at the login screen as well. 

Last but not least, I intend to also use ```
libinput-gestures
``` as my wife would like to have similar gestures to her old macbook. 

Any guidance would be appreciated. Any reading material that I should look into?

---

### Post by wildmanne39 on 2018-03-06
Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Thanks

---

### Post by sinykk on 2018-03-06
Thanks for making the adjustment.

---

### Post by sinykk on 2018-03-09
I was able to fix the issue thanks to the answer in [this post]("https://askubuntu.com/questions/327389/how-can-i-remap-special-keys-in-xkb?rq=1").


I went to ```
/usr/share/X11/xkb/keycodes/evdev
``` and simply switched the keycodes for the **UP** (keycode 111) and **RTSH** (keycode 62) for my keyboard.


I cleared the xkb cache and rebooted and it's done. Hopefully it will stick.

---

