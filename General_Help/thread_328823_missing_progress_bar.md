---
title: "missing progress bar"
date: 2006-12-31
forum: General Help
---

### Post by tuyoutu on 2006-12-31
I just installed, updated and configured Edgy for my hardware on two boxes. The AMD box is normal but the Intel box has a bug.  The orange color is absent from load progression bars.  Invisible progression bars do cover the print while downloading. 

Can someone tell me how to repair this or should I just install again. [http://ubuntuforums.org/images/smilies/eusa_think.gif](http://ubuntuforums.org/images/smilies/eusa_think.gif)

---

### Post by grendel38 on 2007-02-14
did you ever get help with this?  I see there have been no responses to your question.  I had the same problem and found a work around.  (I just found it -- didn't figure it out)

This problem was reported as bug # 67443.

To fix it:

1 - Edit /etc/X11/xorg.conf, and change display DefaultDepth from 24 to 16.
2 - Log out.
3 - ctrl-alt-backspace to restart X

It worked for me.

---

### Post by uber_n00ber on 2007-03-09
This fix worked for me too.

Cross-posted to this thread:
[http://ubuntuforums.org/showthread.php?p=2269536#post2269536](http://ubuntuforums.org/showthread.php?p=2269536#post2269536)

---

