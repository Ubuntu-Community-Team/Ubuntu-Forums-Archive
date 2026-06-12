---
title: "Problem with VNC, showing PRE X screen"
date: 2006-08-16
forum: General Help
---

### Post by jiggilo on 2006-08-16
When i VNC into my ubuntu machine, it displays the PRE-X screen (its like greyed out, and the cursor is a X) and doesnt load anything after that.  I just installed xgl/compiz , which i have a feeling screwed it up, but i disabled it from startup and its still doing this. 

Any thoughts?

---

### Post by crashtest on 2006-08-16
Post the contents of your ~/.vnc/xstartup file.  It is probably not specifying a valid window manager.

---

