---
title: "aMSN font rendering?"
date: 2006-10-09
forum: General Help
---

### Post by Old Pink on 2006-10-09
Hi there,

As the screenshots below show, I've pretty much perfected font rendering in Ubuntu, and all looks gorgeous. 

However, in an aMSN chat window, fonts are still disgusting. 

Any ideas?

- Matt

---

### Post by christhemonkey on 2006-10-09
As aMSN uses Tk, which on ubuntu is not compiled with anti-aliasing enabled, so the fonts look vaguely hideous.

(someone correct me if im dis-notioned (wrong))

---

### Post by Old Pink on 2006-10-09
> **christhemonkey said:**
> As aMSN uses Tk, which on ubuntu is not compiled with anti-aliasing enabled, so the fonts look vaguely hideous.

How do I go about enabling anti-aliasing in "Tk" then? :)

---

### Post by christhemonkey on 2006-10-09
Recompile it.

I believe there is a howto somewhere on these forums.

But 

EDIT:
Had a search whilst typing that first bit.
See this howto:
[http://ubuntuforums.org/showthread.php?t=216689](http://ubuntuforums.org/showthread.php?t=216689)

---

### Post by Old Pink on 2006-10-09
> **christhemonkey said:**
> See this howto:
[http://ubuntuforums.org/showthread.php?t=216689](http://ubuntuforums.org/showthread.php?t=216689)

Worked great, thanks. :)

---

### Post by christhemonkey on 2006-10-09
No problemo.




May i recomend to you the search box :p

---

### Post by woekele on 2006-10-09
When using TCL TK 8.5, the fonts look much better :) Also decomming the 'require pixmap' line in gui.tcl should give you a better looking menu.

---

