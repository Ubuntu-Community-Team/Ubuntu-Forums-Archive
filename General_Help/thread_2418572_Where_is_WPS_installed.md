---
title: "Where is WPS installed?"
date: 2019-05-08
forum: General Help
---

### Post by mcoatman on 2019-05-08
I'm trying to set WPS as the default word processor in Firefox's preferences. In order to do that I need to know where the file is installed. 

*whereis wps-office* returns */snap/bin/wps-office.wps* but when I navigate there I can't find the application file, just folders full of support files.

Any ideas?

---

### Post by Xian on 2019-05-09
/snap/bin/wps-office.wps is the command that launches the WPS word processor. 

For example open a terminal and issue the command:

```
/snap/bin/wps-office.wps &
```

This should then open the application.

---

### Post by sisco311 on 2019-05-09
You have to navigate to the /snap directory located in the root of the file system (/snap) NOT the one located in your home directory (/home/username/snap)

I don't have a standard Ubuntu installation, but you should be able to choose the file by clicking on* Other locations -> Computer -> /snap -> bin -> wps-office.wps* or something similar.

---

