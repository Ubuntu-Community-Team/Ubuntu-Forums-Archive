---
title: "icons"
date: 2005-06-24
forum: General Help
---

### Post by art on 2005-06-24
Hi forum
The question is the following. There are some apps which do not have an icon when I toggle between apps with Alt-Tab, just a square... I attached a pic of this same square apperaing on the panel (selected) with Emacs. So the question is, where are the pics for Alt-Tab or the panel stored so that I replace one? 
Thanks a lot.

---

### Post by intangible on 2005-06-24
I think the program has to be designed to use an icon.   But anyway, I've found a way to set the icon for you for those prgrams without one:

**sudo apt-get install xwit**

Then make a bash file like this:

```

#!/bin/sh

programname&
xwit -bitmap /path/to/file.xbm -names "Exact Window Title"

```

And there ya go :D.  The Icon will have to be in xbm format to work it appears, and it doesn't seem to override those programs that already have an icon.

Also look at **xwininfo** for some more useful information.

---

### Post by art on 2005-06-27
Well
Thanks for help! I have been playing with xwit these days, but the thing is that when I first run the script it does not iconify it, but if I leave the first emacs window open, and run the script again, the first instance of Emacs gets an icon, gets minimized and the second instance is again without an icon? I put also "-iconify" option, the same result. In the "Exact Window Title" I put Emacs. Any ideas why would this be?
Thanks a lot!

---

### Post by intangible on 2005-06-28
Try using the "Window Id" to make it work more reliably, but you'll have to find a way to get that from the program after it's launched :/  Let me know if you find an easy way to do this.

---

### Post by intangible on 2005-06-28
Try this:
First, make sure we're getting a window id:
**xwininfo -name "Window Name| grep Window id"**

Now let's use that with xwit:
**xwit -bitmap "path/to/file.xbm" -id `xwininfo -name "Window Name"|grep -oE 0x[0-9a-z]{7}`**

I'm sure some regex master out there can make that prettier.

And there ya go, make a bash script to launch the program then run that line and you should be good

---

### Post by art on 2005-06-30
Thank you very much for help!!
The easiest way for me turned out to be the following

#!/bin/sh

emacs21&
xwit -bitmap /path.to.file.xbm  -iconify -select

and I have to click on the window I want to iconify...

---

