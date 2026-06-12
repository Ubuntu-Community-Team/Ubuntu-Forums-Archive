---
title: "Emacs fonts aren't right"
date: 2006-10-23
forum: General Help
---

### Post by jimmyk on 2006-10-23
Hi All,

Since I upgraded from Breezy to Dapper, the fonts in emacs seem to have disappeared (see attached link for screenshot).  I've tried reinstalling emacs using Synaptic, and removing and installing without any success.  Any ideas?

Thanks

James

[IMG]http://www.ma.hw.ac.uk/~james/emacs.png[/IMG]

---

### Post by mbeierl on 2006-10-23
I've specified my own font family info in my ~/.emacs file like so:

 '(default ((t (:stipple nil :background "black" :foreground "white" :inverse-video nil :box nil :strike-through nil :overline nil :underline nil :slant normal :weight normal :height 96 :width normal :family "misc-fixed"))))

When I was monkeying with my DPI settings, sometimes I'd get a display like the one you attached.  Not sure if that info can help you analyze the problem any further...

---

### Post by Typhoon on 2006-10-23
The emacs font mess is caused by a glitch in the xorg.conf file. The font path should be "/usr/share/fonts/X11/...". That fixed the problem for me.

Cheers,
Typhoon

---

### Post by jimmyk on 2006-10-24
Thanks,

I found another thread that mentioned that, but it didn't solve my problem because the fonts are not in at the "/usr/share/fonts/X11/" path either. :confused:

Any ideas?

James

---

