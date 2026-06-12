---
title: "KControl monitor/display section"
date: 2007-06-22
forum: General Help
---

### Post by pickarooney on 2007-06-22
This part of kcontrol won't open for me. Running kcontrol from the command line the output when I click on this section is 
```

Pythonize constructor -- pid = 18676
Python interpreter initialized!



Pythonize constructor -- pid = 18676
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 72, in __init__
    self.xorg_config = xorgconfig.readConfig(xorg_config_filename)
  File "/var/lib/python-support/python2.5/xorgconfig.py", line 657, in readConfig
    raise ParseException,"Unknown line type '%s' on line %i" % (first,line)
xorgconfig.ParseException: Unknown line type '1025' on line 92
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 72, in __init__
    self.xorg_config = xorgconfig.readConfig(xorg_config_filename)
  File "/var/lib/python-support/python2.5/xorgconfig.py", line 657, in readConfig
    raise ParseException,"Unknown line type '%s' on line %i" % (first,line)
xorgconfig.ParseException: Unknown line type '1025' on line 92
error: *** runFunction failure
;

```

I just want to prevent my monitor switching off after 10 minutes idle time. Any ideas?

---

### Post by pickarooney on 2007-06-22
For info, I tried the solution in [this thread](http://ubuntuforums.org/showthread.php?t=347154&highlight=kcontrol+monitor) to no avail.

---

