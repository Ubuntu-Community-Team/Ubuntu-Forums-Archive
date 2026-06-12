---
title: "Blog editor client"
date: 2008-01-01
forum: General Help
---

### Post by jordilin on 2008-01-01
Can anyone suggest a good blog editor client, sth like blogtk available for Ubuntu? I don't know how I deleted the blogtk default profile and the app does not load anymore. I installed it again with the same result. The error I get when launching from command line:
> Traceback (most recent call last):
  File "/usr/bin/BloGTK", line 1244, in ?
    blogtk = BloGTK()
  File "/usr/bin/BloGTK", line 138, in __init__
    self.grabConfig()
  File "/usr/bin/BloGTK", line 372, in grabConfig
    self.url = self.conf.get(self.sectionName, 'server')
  File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'Default'

---

### Post by jordilin on 2008-01-01
Well, I just figured out how to solve the issue with Blogtk. It saves the personal conf file in ~/.BloGTK. Removing this dir, I can load the app again. In any case, can someone else suggest more editors?

---

### Post by icheyne on 2008-01-01
I like ScribeFire.

[http://www.scribefire.com/](http://www.scribefire.com/)

It's a Firefox extension, so it also works when I'm on Windows.

---

