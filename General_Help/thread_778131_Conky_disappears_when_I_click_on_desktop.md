---
title: "Conky disappears when I click on desktop"
date: 2008-05-01
forum: General Help
---

### Post by laffinet on 2008-05-01
Hi !

I've recently installed conky and configured it so it appears on the desktop and not in a separate window. 

The problem is that the moment I'm clicking anywhere on the desktop conky disappears.

I've tried various settings, but so far have not been able to solve this. At the moment I'm running with the following settings:

own_window yes
own_window_transparent yes
own_window_type desktop

Any idea how I can get conky on my desktop, no separate window, without showing up on the panel, without disappering when I click on the desktop ? Thanks for any help.

BTW: I'm running 8.04 with compiz.

---

### Post by xaqm238 on 2008-10-13
Did you ever get anyhting on this?  Having same issue...

---

### Post by lswest on 2008-10-13
My conky file sets the window_type to override, I believe that solved the problem for me.

Also, make sure conky is delayed to start, otherwise it will be rendered with shadows.

If you need, I'll post my conkyrc file here.

---

### Post by laffinet on 2008-10-13
I'm not quite sure what fixed it for me in the end. Here's what I've got at the start of my .conkyrc
```

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
```

And I'm starting conky with a decent delay using this script:
```

#!/bin/bash
sleep 20 && conky;
```

Hope this helps !

---

### Post by HyperHacker on 2008-10-13
I use these settings to work around it:
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by Michal77 on 2008-10-13
Hi,
I had the same problem when I've been using .conkyrc scypt from this HTD:
[http://www.simplehelp.net/2008/05/20/how-to-display-your-system-info-on-your-linux-desktop/]("http://www.simplehelp.net/2008/05/20/how-to-display-your-system-info-on-your-linux-desktop/")
When I've changed to some I got from Forum [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") the problem is gone.

My advise: find one the most similar to what you want and adjust to your need.

---

### Post by xaqm238 on 2008-10-14
the override is what fixed it...Thanks for all the posts!

---

### Post by Eemeez on 2008-10-24
> **laffinet said:**
> I'm not quite sure what fixed it for me in the end. Here's what I've got at the start of my .conkyrc
```

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
```

And I'm starting conky with a decent delay using this script:
```

#!/bin/bash
sleep 20 && conky;
```

Hope this helps !

This was the solution to get it work for me. Important part is the delayed start. As it was new to me, how to get it work, I will write it down just in case.

Copy the code into text editor. Save the file with some name (for example conkystart), save the file in some location (example: /home/username/)
Browse to the file, right click on file and propeties, then permissions tab and check the box "allow executing file as program".

After that go to System-Perferences-Sessions. Add a new session and in the command line, put the file location (/home/username/conkeystart).

Next time the system starts, it will execute the script and start conkey with the 20 seconds delay.

---

### Post by jpyanowski on 2008-12-14
> **lswest said:**
> My conky file sets the window_type to override, I believe that solved the problem for me.

Also, make sure conky is delayed to start, otherwise it will be rendered with shadows.

If you need, I'll post my conkyrc file here.

I want to thank you for this suggestion. I stopped my conky from disappearing and also removed the border around it. Thanks again.):P

---

### Post by enzyme on 2009-03-26
> **xaqm238 said:**
> the override is what fixed it...Thanks for all the posts!

I can also confirm that the override fixes the problem. Thanks to everyone who helped fix this!

---

### Post by ervanux on 2009-04-25
> **HyperHacker said:**
> I use these settings to work around it:
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```


thanks this :)

---

### Post by msmx5s on 2010-10-29
> own_window_type override

This worked for me! Thanks!

---

### Post by metallus on 2011-10-21
> **HyperHacker said:**
> I use these settings to work around it:
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

This is what worked for me (especially the  own_window_type normal part)
Thanks!

---

