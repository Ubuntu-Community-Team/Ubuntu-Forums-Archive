---
title: "Frostwire doesnt like Beryl or Compiz"
date: 2007-03-13
forum: General Help
---

### Post by LSparky on 2007-03-13
Everytime time Beryl or Compiz is configured through the Beryl window manager I am not able to open Frostwire normaly, for some reason I must use metacity. When I use beryl or compiz frost wire comes up blank, the window comes up but you cant see anything in side it. Is anyone else haveing this problem?

---

### Post by Ramses de Norre on 2007-03-13
It's a known bug, I think it's due to xgl but I'm not sure.
Most swing applications wont work, it's not only frostwire... There might be workarounds already, search for xgl + swing on the beryl or compiz forums.

---

### Post by zachalekos on 2007-03-13
try this , it worked for me [http://www.ubuntuforums.org/showthread.php?t=321727&highlight=beryl+frostwire](http://www.ubuntuforums.org/showthread.php?t=321727&highlight=beryl+frostwire)

---

### Post by cmost on 2007-03-13
This is the easiest solution:
1.  Open your favorite text editor.  Paste the following:
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

NOTE:  you might need to replace the last line with "/opt/FrostWire/runFrost.sh" (without the quotes) depending on how you installed Frostwire.

2.  Save the file as something, maybe "launch_frostwire"
3.  Right-clcik on the file and select 'properties'; click the 'permissions' tab, then tick 'allow executing file as program'; click 'close'
4.  Create a new launcher for Frostwire with the path being /path/to/launch_frostwire

Enjoy!

---

