---
title: "Stalonetray / Toggle Panel Size"
date: 2008-07-07
forum: General Help
---

### Post by anotherdisciple on 2008-07-07
I got rid of (well... just hid really well) my last gnome panel. I am using AWN as a dock and StaloneTray as my system tray. It automatically starts in the bottom left side of your screen.... can I make it start on the bottom right?


Another option I have been throwing around is toggling my last gnome panel's hidden size between 0 and 24. Can I make a script that does this? That way I can just make a link to that script and toggle the panel when I need it. 

Thanks in advance...

---

### Post by moonbeam on 2008-07-07
This command line will start stalonetray in the bottom right.  If the version you are using is a bit old you may have to remove some command line options.

stalonetray -geometry 104x48-4-4 --skip-taskbar --sticky -t --skip-taskbar --window-type dock --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --respect-icon-hints false --max-height 48 --icon-size 24 -i 24

If you have any issues with stalonetray not being recognized as a dock and showing up ast a task/window in taskmanagers etc then you _MAY_ want to try the patched version available at.

[https://launchpad.net/~gilir/+archive](https://launchpad.net/~gilir/+archive)

Note the stalonetray package should be fine (it has a one line patch against ver 0.7.6)...  I believe some of the other packages do bleed.

---

### Post by anotherdisciple on 2008-07-07
cool... could you tell me exactly what part of that command makes it go in the lower right hand side? I already made a config file... so I just wanted to edit it rather than starting over.

---

### Post by ben2talk on 2009-09-27
> **anotherdisciple said:**
> cool... could you tell me exactly what part of that command makes it go in the lower right hand side? I already made a config file... so I just wanted to edit it rather than starting over.

I went for the left side (I have conky on the bottom right) 

transparent true
background grey
icon_gravity NW
window_layer normal
sticky true
window_type dock
vertical
max_width 24
icon_size 24

max width limits to a single column building up. 48 allows 2 rows, 72 gives me a square. No 'max width' lets it spread along the bottom, but then I feel it clashes with docky.

'background grey' works if you don't set 'transparent true'. At this size I don't mind the fake transparent effect. I couldn't get used to it with conky - that's set to black.


Updated 15th December - I find that 

trayer --edge bottom --align right --distance 1 --widthtype request --heighttype request --SetDockType true --expand true --transparent true --alpha 255 works better for me now ;)

Of course, this means I installed trayer - and don't use stalonetray any more. 

Trayer never let me down. I use the above command in my startup programs list - there's no 'config' file.

---

