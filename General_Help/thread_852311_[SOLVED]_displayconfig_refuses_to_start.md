---
title: "[SOLVED] displayconfig refuses to start"
date: 2008-07-07
forum: General Help
---

### Post by MaxSommerfeld on 2008-07-07
Hello everyone!

I've tried to enable a TV-monitor at the S-Video output on my laptop. I've used the displayconfig-gtk application.
I cannot recall what exactly I've changed but I think that I indicated that there is now a TV monitor instead of my laptop display (which of course isn't).

Anyway, I now have A 640x480 resolution on my screen and I can't change it. When I try to run displayconfig again this is what I see:
```
gksudo displayconfig-gtk
[]
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 418, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 972, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1184, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1861, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range

```

Thanks in advance for any help you can give me!

---

### Post by MaxSommerfeld on 2008-07-08
I've solved the problem by resetting the xorg.conf file with this line:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

