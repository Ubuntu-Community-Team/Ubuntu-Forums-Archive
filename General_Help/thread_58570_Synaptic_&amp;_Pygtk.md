---
title: "Synaptic &amp; Pygtk"
date: 2005-08-20
forum: General Help
---

### Post by rwabel on 2005-08-20
When I click on Repositories in Synaptic I get the following error message in the terminal:
 ```
Traceback (most recent call last):
  File "/usr/bin/gnome-software-properties", line 25, in ?
	import pygtk
ImportError: No module named pygtk
``` 

I've to change in the file /usr/bin/gnome-software-properties the first line to:
 ```
#!/usr/bin/env python2.4
``` 

Somehow my python is messed up I guess. How can I fix that or where can I define that the python env is python2.4 by default?

---

