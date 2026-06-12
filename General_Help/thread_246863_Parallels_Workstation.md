---
title: "Parallels Workstation"
date: 2006-08-29
forum: General Help
---

### Post by pwrstick on 2006-08-29
Howdy y'all,

In my further attempts to not have to boot into XP I'm giving Parallels a shot (on Dapper 6.06).  So far it's been pretty fun though I'm running into some problems I'm hoping someone else has run into and fixed.

Problem 1 is transparency: the console is transparent.  It's almost like a window being set transparent via compiz/xgl; the parallels window is totally opaque (i.e. the edges with the start/stop buttons) while the content (the actual VM instance console) is transparent.

Problem 2 is full screen.  It keeps telling me that the Primary OS (ubuntu of course) can't handle the resolution the Guest OS is asking for.  Sounds simple enough!  But I changed the Guest OS resolution to be the exact same as Ubuntu's (1280x1024) and no go.  I actually tried all of the resolutions in windows but no go.

So anyway, if you're all curious and haven't tried Parallels I'd give it a shot.  It's an eerie feeling hearing Windows start up noises while in Ubuntu!  And as far as I can tell so far everything works pretty well.

---

### Post by reacocard on 2006-08-29
I take it you're running compiz? Some people experience this problem with some things under compiz. quick fix:
```
export XLIB_SKIP_ARGB_VISUALS=1
parallels
```

---

### Post by pwrstick on 2006-08-29
> **reacocard said:**
> I take it you're running compiz? Some people experience this problem with some things under compiz. quick fix:
```
export XLIB_SKIP_ARGB_VISUALS=1
parallels
```

Well that's fixed!  Thanks!

Now I just have to take care of the full screen mode.

---

### Post by spiff95 on 2008-02-19
I found this thread through a search of the forums, as I was having the same problem. I wasn't sure if reacocard meant to put this in terminal or a file, so I fired off a PM, and received the following. It made it much clearer for me:

> Originally Posted by spiff95
>Greetings,

>I just did a search on parallels window transparency and found the solution you gave to OP. The >code was:

>export XLIB_SKIP_ARGB_VISUALS=1
>parallels

>One question, though. Is that to be type in a terminal or added to a config file? If so, which one?

>I hope you don't mind my asking, I will add the info to the thread I found for this.

>Thanks,

>Spiff

terminal. alternatively it can be run as one command, like this:

Code:

XLIB_SKIP_ARGB_VISUALS=1 parallels

the difference between the two methods being that the first applies the change to any further commands run in the terminal, while the second applies it only to the one command. It is also possible to create a shell script to do this automatically, something like

Code:

#!/bin/sh
XLIB_SKIP_ARGB_VISUALS=1 parallels

save that to /usr/local/bin as start_parallels.sh, run

Code:

sudo chmod +x /usr/local/bin/start_parallels.sh

and then you can run parallels with this tweak by just using

Code:

start_parallels.sh

You can even use the menu editor to change the command it uses to launch parallels to this script so that you don't even have to open a terminal to make it work!

---

