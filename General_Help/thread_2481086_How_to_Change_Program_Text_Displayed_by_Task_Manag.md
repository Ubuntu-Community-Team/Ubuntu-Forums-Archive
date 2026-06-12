---
title: "How to Change Program Text Displayed by Task Manager (Panel)"
date: 2022-11-18
forum: General Help
---

### Post by vilhelmo79 on 2022-11-18
Is there a way in which the text displayed for each program by the Task Manager (Panel) can be changed?
For instance, featherpad displays the path of the file in addition to the filename.  
See: attachment
I would like to be able to display only the filename and not the path in the Task Manager (Panel).
Can this be done?

Sincerely,

Vilhelmo.

Edit:  Just to be clear, Task Manager is the default taskbar app used by Lubuntu Panels.  It displays running applications.

---

### Post by TheFu on 2022-11-18
I've never seen or used Task Manager.

But 'glances', it is not possible.  It pulls the information based  on the process table.

'top' seems to remove the leading paths, most of the time, but not always. I don't know what the differentiator is, perhaps how the program was started?  

```
$ glances
```
vs
```
$ /usr/bin/glances
```

If you use .desktop files to start processes (i.e. menus), then the Exec= line inside would be my guess for how the program is launched.
For example, inside the firefox.desktop file, there's a line:
```
Exec=firefox %u
```

Anyway, some places to check for you.

---

