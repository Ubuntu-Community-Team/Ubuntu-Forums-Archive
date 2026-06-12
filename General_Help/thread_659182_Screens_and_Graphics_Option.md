---
title: "Screens and Graphics Option"
date: 2008-01-05
forum: General Help
---

### Post by GriGGerS on 2008-01-05
Hi All

Yesterday I installed Gusty Gibbon on to my laptop. Dual boot with Vista.
Have just about every thing working fine except the dual monitor malarkey.

Anyway I have been playing around in the Screens and Graphics option getting different results, the problem I now have is that this option has stopped working.

When I click on system/admin/screens and graphics option I get the password box the first time and see the minimized starting screens and graphics..  then nothing.

From them on no mater how many times I try I cannot get the Screens and Graphics window up i get nothing..

Have i broken it... Is there a fix?

Cheers

GriGGerS

---

### Post by FuturePilot on 2008-01-05
Try running it from a terminal and see if there's any errors
```
gksu displayconfig-gtk
```

---

### Post by GriGGerS on 2008-01-05
> **FuturePilot said:**
> Try running it from a terminal and see if there's any errors
```
gksu displayconfig-gtk
```

Hi thanks for your response..

Did as suggested and this was returned

    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 190, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 392, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 411, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range


All seems to be ok...As far as I can tell that is...

Still can't get the Screen and Graphics up via the GUI..

GriGGerS

---

### Post by bobbybobington on 2008-01-19
same problem, any help would be appreciated :)

---

### Post by jenster on 2008-02-26
I, too, am having the same problem.  I actually had the 2-screen layout working, but then switched to the mirrored display, and now I can't access the Screens and Graphics applet.  :(

I got the same string of errors as those the original post-er did.   Have we uncovered a bug?  

This is the second time I have run into this problem.  The last time, I attempted to troubleshoot and fix the problem, and ended up hosing GNOME, so I did a clean re-install.  At that time, I thought I had broken something, but now, it seems I'm not the only person having this problem.  

Any help would be great!  I'm not a complete Linux newbie, but my knowledge is very patchy, and I'm new to Ubuntu.

Danke!

---

