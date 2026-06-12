---
title: "gconf-editor doesn't save changes"
date: 2007-04-14
forum: General Help
---

### Post by Deviltongue on 2007-04-14
I've made a couple of changes to the configuration editor but everytime I close it it erases my settings. how do I fix this?

---

### Post by aysiu on 2007-04-14
Can you try typing this command in the terminal and seeing if it makes a difference? ```
sudo chown -R deviltongue:deviltongue /home/deviltongue
``` Substitute in your actual username for *deviltongue*, of course. Then fire up *gconf-editor* and see if your changes stick.

---

