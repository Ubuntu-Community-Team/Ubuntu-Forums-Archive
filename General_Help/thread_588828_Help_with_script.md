---
title: "Help with script"
date: 2007-10-23
forum: General Help
---

### Post by herbster on 2007-10-23
I have a script I'm using to back up multiple folders to partitions on my external hd, using rsync. It works fine, but I'd just like to adjust the way the gnome-terminal handles it. I'd like each rsync operation to open in a new tab in the same gnome-terminal window. What I have works, but what happens is the terminal window opens and I can see a new tab being made but it immediately closes and it sticks to the main window. It can't seem to hold the tab. I am using a profile that has the window set to stay open on completion of the command. Here's part of the script (the rest is the same with more folders being backed up):

```
#!/bin/bash
export DISPLAY=:0 && gnome-terminal --window-with-profile=Stays -e='rsync -avz --progress --delete /media/extra/ubuntu-customizing /media/systembackup/' --tab -e='rsync -avz --progress --delete /media/extra/Docs /media/systembackup/'
```

Thanks

---

