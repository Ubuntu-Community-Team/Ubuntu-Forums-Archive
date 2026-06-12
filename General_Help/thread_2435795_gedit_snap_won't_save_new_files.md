---
title: "gedit snap won't save new files"
date: 2020-01-26
forum: General Help
---

### Post by ChristopherAdams on 2020-01-26
I've had a problem with the gedit snap (on Xubuntu 19.10): when I selected the "Save as ..." option in the menu, no dialog would appear. Also, nothing would happen if I pressed the "Save" button, or if I tried to close without saving (I would get the option to save the file, but when I selected it, no dialog would appear). This problem persisted even after I updated Ubuntu.

My solution was to remove the snap:

```
~$ sudo snap remove gedit
```

And reinstall gedit as a standard program:

```
~$ sudo apt-get install gedit
```

After this, the "Save as..." dialog appeared as normal.

---

