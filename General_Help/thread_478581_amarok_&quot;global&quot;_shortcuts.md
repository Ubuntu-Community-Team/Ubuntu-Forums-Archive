---
title: "amarok &quot;global&quot; shortcuts"
date: 2007-06-19
forum: General Help
---

### Post by FRuMMaGe on 2007-06-19
How can I use supposedly global shortcuts for amarok when using a fullscreen application such as unreal tournament?  I want to be able to change track while playing.

---

### Post by kuja on 2007-06-19
Well, they should work, so long as nothing else (perhaps a local app) is overriding the global shortcuts, which generally take a backseat by the looks of it. 

Alternatively it might be easier to do it (easy is a relative word here I'm afraid) with one of the x config files, I'm not sure which one it would be, to have i t bind a shortcut to a command. Another solution which might work though perhaps impractical would be to use a remote + lirc to do it.

To change tracks while playing via a script it will look something like this:
```
dcop amarok player next/prev/play/stop/playPause
``` (only one of the next/prev/etc at a time of course)

---

