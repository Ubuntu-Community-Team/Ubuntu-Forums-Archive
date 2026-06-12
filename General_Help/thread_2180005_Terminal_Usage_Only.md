---
title: "Terminal Usage Only"
date: 2013-10-10
forum: General Help
---

### Post by blake4 on 2013-10-10
I'm using Ubuntu 13.04, but OpenBox -- a Terminal-only system. 

          I'm using OpenBox, so it's all terminal-based. Here are my questions. How do I open the following using Terminal only?
  [INDENT]   
[LIST]
[*]TeamViewer
[*]Photoshop (CS2)
[*]Home Folder
[*]Software Center
[/LIST]
 [/INDENT]

---

### Post by vasa1 on 2013-10-10
I've seen [http://askubuntu.com/questions/356495/terminal-commands-a-guide](http://askubuntu.com/questions/356495/terminal-commands-a-guide). Will you provide feedback to comments there as well? Or have you abandoned that question?

---

### Post by mastablasta on 2013-10-11
Openbox is not a terminal only system. it's a windows manager (so a desktop)

otherwise: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

also if they are windows software (i.e. Photoshop) you can start from terminal with: wine *whatever*.exe

---

### Post by stinkeye on 2013-10-11
Command to list applications and exec line....
```
sed -nrs '/^(Name|Exec)=/p;${g;p}' /usr/share/applications/*.desktop
```

---

