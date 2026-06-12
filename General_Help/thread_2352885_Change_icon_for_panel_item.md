---
title: "Change icon for panel item"
date: 2017-02-16
forum: General Help
---

### Post by raleigh3 on 2017-02-16
I made a panel item for this script.

  ```
[INDENT][SIZE=5][/SIZE]#!/bin/bash
# 
#    
thunar ~/Scripts[SIZE=5][/SIZE]
[/INDENT]
```  However, I can not change it's icon.

It just keeps the mate-panel-launcher.svg file.

  
Do I have to convert my Downloads.png to a .svg file ?

---

### Post by raleigh3 on 2017-02-16
I found one answer.
  
Convert the png file to a pnm file using convert which is included with ImageMagick.

  Ex. convert Downloads.png Downloads.pnm

Then right click the panel item,properties, and select the .pnm file after clicking on the current icon.

---

