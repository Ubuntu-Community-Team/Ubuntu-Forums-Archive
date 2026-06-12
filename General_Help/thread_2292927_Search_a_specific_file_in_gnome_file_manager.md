---
title: "Search a specific file in gnome file manager"
date: 2015-09-01
forum: General Help
---

### Post by fafabone on 2015-09-01
This script is executed by home automation assistant in Linux 14.04, Gnome-desktop
  ```
#!/bin/bash
gnome-open /home/Folder && xdotool search Folder | head -n 1 | tail -n 1 | VAR1=%1 | xdotool windowfocus window=$VAR1 && sleep 1 && xdotool key Down && xdotool key ctrl+f && xdotool type Under
  
```It is useful to search the string Under in the /home/Folder. I would  like to search exclusively for all the video types, using the terminal  and adding a command to the list above. Can you help me? Thanks.

---

### Post by coffeecat on 2015-09-01
Support, not chat.

*Thread moved to **General Help**.*

---

