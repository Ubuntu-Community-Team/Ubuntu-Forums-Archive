---
title: "xdotool question"
date: 2013-01-11
forum: General Help
---

### Post by GrouchyGaijin on 2013-01-11
I'm on 12.04.
I have xdotool and xclip installed.

I have a script bound to a hot key that works.

The script is:
```
#!/bin/bash
xclip -in -selection c ~/scripts/xclip-scripts/sig
```

The sig file contains my signature. (I know this is really simple. :D)

So now, I can hit the hot key and then ctrl+v to paste my name in a document, web brownser etc.

I thought it would be cool, if my name was automatically pasted where ever the cursor is when I press the hot key.

That is the problem.  I can't get that part to work.
I tried adding ```
xdotool key ctrl+v
``` and I swear that it worked yesterday in gedit, but nothing else.  Today, it does not work in gedit either.

I tried following the post [here]("http://ubuntuforums.org/archive/index.php/t-1789578.html"), but that doesn't work either.

Any ideas on what I am doing wrong?

I'd really appreciate some advice.

---

### Post by LewisTM on 2013-01-11
I had the same problem recently. Turned out my text file was not properly encoded for xclip and contained extended characters. Saving it with UTF-8 encoding solved it. Perhaps you have exotic Swedish characters in your sig?

Hope this helps!

---

### Post by stinkeye on 2013-01-11
If your pressing a shortcut key to activate a script that contains an xdotool
command you may want to put in a 1 second sleep command before the xdotool command.

---

### Post by GrouchyGaijin on 2013-01-11
> **LewisTM said:**
> I had the same problem recently. Turned out my text file was not properly encoded for xclip and contained extended characters. Saving it with UTF-8 encoding solved it. Perhaps you have exotic Swedish characters in your sig?

Hope this helps!

I wish that were the case.  However, I and my computer are both from the US (Just live in Sweden).  My name doesn't have any of the Swedish letters äöå so the file should be a regular old UTF-8 file.

Go figure, I changed the hot key to F2 from ctrl+alt+n for name and it seems to be working now.

---

