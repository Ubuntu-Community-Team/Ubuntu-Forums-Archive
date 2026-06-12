---
title: "Errors launching displayconfig-gtk"
date: 2008-05-25
forum: General Help
---

### Post by Makaai on 2008-05-25
Hi!The utility displayconfig-gtk (Screen and Graphics) does't start, and launched from terminal it found these errors:

```
luca@daneel:~$ gksu displayconfig-gtk
/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
 will be deprecated in future releases. Please update this theme to get rid of this warning.
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 78, in __init__
    self.xorg_config, self.hasxorg = xorgconfig.readConfig(xorg_config_filename, check_exists=True)
  File "/var/lib/python-support/python2.5/xorgconfig.py", line 771, in readConfig
    raise ParseException,"Unknown line type '%s' on line %i" % (first,line)
xorgconfig.ParseException: Unknown line type 'sendcoreevents' on line 72

```

---

