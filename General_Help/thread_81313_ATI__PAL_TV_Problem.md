---
title: "ATI / PAL TV Problem"
date: 2005-10-24
forum: General Help
---

### Post by Kadafi on 2005-10-24
I recently decided to put Breezy on my HTPC (Shuttle ST62K) to use MythTV, which seems a whole lot better than MCE or Media Portal in Windows.

Anyway, it SEEMS to boot into X with TV-Out using the ATI drivers which come with Breezy. What I'm getting is close, but not quite right. I can see the right colours, and tooling around with ModeLines I can even see the login box and the mouse pointer (flickering like mad in three different locations on my TV). Everything works perfectly with a regular monitor.

As far as I can tell, all I need to do is set up a monitor configuration for my PAL-B TV in xorg.conf which lists the proper ModeLine for a PAL-B TV.

I've tried countless recognised PAL ModeLines but can't seem to get it clear. Likewise, I've tried using the modeline generator ([http://xtiming.sourceforge.net/](http://xtiming.sourceforge.net/)) and that doesn't help. The closest ModeLine I've tried so far is here:


ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
Using the settings from this page:
[http://www.kingcot.eclipse.co.uk/unichrome/fc3/xorg.conf.txt](http://www.kingcot.eclipse.co.uk/unichrome/fc3/xorg.conf.txt)
(including "nodpms", "noddc", DisplaySize, Viewport etc)
...it's not right though.

Does anyone have solution to this problem - or perhaps a digital TV they could donate? :)


EDIT: Reposting in hardware section...probably more appropriate.

---

