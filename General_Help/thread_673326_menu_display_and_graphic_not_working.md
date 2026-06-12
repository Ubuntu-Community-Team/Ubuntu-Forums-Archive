---
title: "menu display and graphic not working"
date: 2008-01-20
forum: General Help
---

### Post by e_defranco on 2008-01-20
Hi, 

I have an xubuntu 7.10 with nvidia GeForce 4 MX 4000.

I have installed the nvidia driver with Envy (very good software), all working fine, but now I cannot set the 3d functionality of the card with the menu applications -> setup -> display and graphic (I hope that the translation from my italian version to english will be correct, in my sistema is: applicazioni -> impostazioni -> schermi e grafica).

When click on the menu nothing occour and if  I start from a terminal the application displayconfig-gtk this is the error:

Xlib:  extension "XFree86-VidModeExtension" missing on display "10.0.50.103:1.0".
[]
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
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

I don't know if it is related but I use a kernel 2.6.22.15-custom and when I go to the menu System -> manage driver with restrictions,  the system tell me: is needed install linux-restricted-modules-2.6.15-custom if you want that the program working.

There are some people that can help me on this topic ?

Thank in adavance,
emilio

---

### Post by e_defranco on 2008-02-07
kernel mismatch

solution: re install the kernel and update the system

---

