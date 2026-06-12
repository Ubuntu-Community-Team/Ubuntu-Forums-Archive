---
title: "Run script when double clicked"
date: 2016-08-05
forum: General Help
---

### Post by 4kh3RAm on 2016-08-05
Is there way to get a script to run instead of the editor opening when it is double clicked ? (In Thunar)

---

### Post by Keith_Helms on 2016-08-05
Yes.  From the Thunar file list, right-click on the script and select properties.  Select the open with pulldown and click on other application.  Click on use a custom application at the bottom and then type in /bin/bash and select okay.

Note: This will cause ALL your .sh files to behave the same - running them when you double-click on them in Thunar.

HOWEVER: If you ever right-click on a .sh file and select open with something else, like mousepad, then that operation changes the default for .sh files to the new program.  How to change open with for a single file or how to make it a permanent default - I haven't figured those out yet.

---

