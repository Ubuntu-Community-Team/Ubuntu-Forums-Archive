---
title: "Just One Question......?"
date: 2008-05-23
forum: General Help
---

### Post by Kaneda187 on 2008-05-23
Im Dual booting Hardy 8.04 and I have all my music files stored on my other OS, so heres the problem when I boot Ubuntu I use Amarok to play music but befor I do so I have to go to Places down to my partition so it appears on the desktop otherwise amarok cant find the files

so heres the question is ther any way make my partition appear automatically?

Or make amarok find the files with out having the icon on the desktop?

Thanks in advance:)

---

### Post by FuturePilot on 2008-05-23
Install the ntfs-config utility. Go under Applications&#8594;System Tools and use the tool to have your NTFS partition mount at startup.

```
sudo apt-get install ntfs-config
```

---

### Post by Kaneda187 on 2008-05-23
Thanks!!! worked PERFECT!!:)

---

### Post by Kaneda187 on 2008-05-23
Another Question now do i have to have it on my desktop all the time or is ther some way i can hide it??

---

### Post by shrimphead on 2008-05-23
open a terminal and run gconf-editor.

then in the config editor go apps -> nautilus -> desktop and uncheck the volumes visible box.

this will stop all mounted volumes appearing on your desktop (USB keys too unfortunately) so you will have to go through the places menu or nautilus windows to get to them.

hope this helps

---

### Post by Kaneda187 on 2008-05-23
Thanks!!:)

---

