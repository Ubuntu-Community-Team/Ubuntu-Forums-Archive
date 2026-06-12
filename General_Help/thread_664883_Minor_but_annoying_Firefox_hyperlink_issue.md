---
title: "Minor but annoying Firefox hyperlink issue"
date: 2008-01-11
forum: General Help
---

### Post by mb_webguy on 2008-01-11
This is so minor I'm hesitant to bring it up, but it's getting to be rather annoying...

I'm using Firefox 2.0.0.11 on Gutsy.  Fairly often (over 50% of the time) when clicking on a link in Firefox, the browser will not load the page while the cursor is still hovering over the link.  As soon as I move the cursor away from the link, the page loads.   I haven't noticed this problem with buttons or any other page elements, and it's not consistent with all hypertext links.

Any suggestions?

---

### Post by hibajugala on 2008-01-12
I havent had that problem, links open fine for me. hmm

---

### Post by zach12 on 2008-01-12
Try reinstalling Firefox

---

### Post by hibajugala on 2008-01-12
that solves everything ;)

---

### Post by Nesman on 2008-01-12
It might be helpful to start Firefox from a terminal and then browse around a bit.  Most programs will give you error messages on the terminal that you normally wouldn't see.  This might give you something useful, either for us or for Google.

---

### Post by mb_webguy on 2008-01-15
Arrggh!

So I reinstalled, but no change.  I reinstalled again.  Still no change.

Then I uninstalled, installed, and then tried to call Firefox from the command line.  I got a segmentation fault.  Fortunately I have IE installed (what can I say... I design web pages), so I got on the forums and looked that up.  Well, there are apparently only a few dozen things that can cause a seg fault in Firefox, so I tried all of the usual suspects, to no avail.

Finally, I back up my .mozilla folder and do a complete removal and install.  Bingo!  So it had something to do with one of my extensions (which it really shouldn't, since I've been using the same handful of extensions for quite a while, including as I write this, with no problems).  No problem -- I restore all of my preferences and bookmarks, then reinstall each of the plugins, and everything's back to normal.

In fact, while it's still a bit early to call, it seems like my original problem with clicking links seems to be fixed.  It's great if it is, but I wish I knew what caused it in the first place...

---

