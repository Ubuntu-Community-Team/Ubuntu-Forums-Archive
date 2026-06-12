---
title: "Trouble with devilspie geometry"
date: 2008-05-26
forum: General Help
---

### Post by andrewbrown22 on 2008-05-26
I've finally got my conky configured the way that I like it, but I am now having trouble embedding a terminal on the desktop with devilspie in the location that I want it.
I've gone through [this guide](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop) to configure my terminal config file and all, and I can get it to work, but it is no where near the location that I want it on my desktop. 
I've searched on the issue and cannot find out how to do exactly what I'm asking, and after playing around with it for a while and having no luck, I thought I'd ask.. 
Below is a screenshot of where I'd like to play my embedded terminal on my 1680x1050 res desktop.

---

### Post by Forlong on 2008-05-26
You can configure the placement of the GNOME terminal like this:
```
gnome-terminal --geometry +600+500
```
Just fiddle with the values 'till it fits.

---

### Post by andrewbrown22 on 2008-05-26
I've figured out what my values need to be, and I've set them to that, but it still will not move the terminal itself.
Here is the DesktopConsole.ds:
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+1075+700")
                (geometry "450x450")
        )
)

```

What is the problem? Here is what that .ds file produces.. (changed the wallpaper because with the black font in the terminal you can hardly see it, don't know how to change the font..)

---

### Post by Forlong on 2008-05-26
Like I said, the GNOME terminal has the ability to configure the placement itself. Why don't you just use that?

And the font can be configured in the current profile.

---

### Post by andrewbrown22 on 2008-05-26
Ok, I didn't understand you, sorry.  I'll mess around with it there.  That can be configured to run automatically?

Thanks

---

### Post by andrewbrown22 on 2008-05-26
I've now tried running this command, only to find that it flickers down at the bottom right and moves itself back to the top left..
```

gnome-terminal --window-with-profile=DesktopConsole --geometry +1075+700

```

---

### Post by andrewbrown22 on 2008-05-26
Ok, figured it out.
Anyone else having this issue, follow the steps above, but remove the geometry parts of the DesktopConsole.ds and it should work out for you.
Thanks Forlong.

Edit: I still cannot really get it done the right way. I've added 
```

gnome-terminal --window-with-profile=DesktopConsole --geometry +1075+700

```
as a session as well as devilspie.  After logging out and back in, the terminal is again placed in the top left corner, the geometry value seems to be ignored.

---

### Post by Forlong on 2008-05-26
It is a long time since I used Devil's Pie but don't you have to add it to the startup programs as well?

Then you might as well write a small script to run both:

1. ```
gedit $HOME/start-desktopconsole
```

2. Copy & paste the following in there:

```
#!/bin/bash
devilspie &
sleep 2
gnome-terminal --window-with-profile=DesktopConsole --geometry +1075+700 &
```

3. Save

4. Now make it executable:
```
chmod +x $HOME/start-desktopconsole
```

5. Finally add start-desktopconsole (it's a file in your home directory) to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs*

---

### Post by andrewbrown22 on 2008-05-26
I was starting both devilspie and my terminal upon login.  Both did start, but it didn't place the terminal in the area defined by the geometry value.  I tried your method and it didn't produce anything on the desktop after logging out and back in.
I've kept messing around with the values and still haven't found a solution that works.

---

### Post by Forlong on 2008-05-26
Did you remove the other things you added to your Startup Programs?

And there's no need to log out, just run
```
$HOME/start-desktopconsole
```
in the terminal and look for any error messages.

---

### Post by andrewbrown22 on 2008-05-27
No error messages, and it worked for a while, but after tweaking the geometry a little, it once again moved to the top corner.

---

### Post by jviscosi on 2008-05-30
You can try setting up a debug.ds file (just containing the word **debug) **in your .devilspie directory, then run devilspie from the command line and watch it to see if it reports any interesting messages that might explain why it isn't moving/resizing your terminal as you want it to.

---

### Post by Weevil on 2009-11-16
Kinda late reply but maybe someone has a use for it...

 Instead of setting devilspie geometry like this;
(geometry "+50+50")
(geometry "924x668")
try setting it like this:
 (geometry "924x668+50+50")

This worked for me. Also don't blindly copy the provided tekst but make sure to remove extra spaces and replace them with tabs.

---

