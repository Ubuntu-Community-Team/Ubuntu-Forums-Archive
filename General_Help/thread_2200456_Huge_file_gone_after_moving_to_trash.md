---
title: "Huge file gone after moving to trash"
date: 2014-01-19
forum: General Help
---

### Post by pieter3 on 2014-01-19
Hello everyone,

I wanted to create a swap file, so I ran the command  ```
dd if=/dev/zero of=/swap bs=1024 count=20480000
``` and I realized I had entered one 0 too much. So I cut off power from my laptop, which had stopped to respond completely and restarted it. I tried to remove the file by moving it to the trash, but when I tried to open the trash I got an error saying that the operation could not be completed. Now the file is gone, but the disk space (~13GB) is still occupied. I eventually got the trash opened, but the swap file was gone.
```
sudo rm /swap
``` didn't help me either.
Any ideas on how to remove the file?

Thanks in advance,
Pieter

(I'm using Lubuntu 13.10).

---

### Post by jeanjd63 on 2014-01-19
Hello

Can you try :

**[COLOR=#000000]sudo du -sh /root/.local/share/Trash/*[/COLOR]**

---

### Post by pieter3 on 2014-01-19
That folder doesn't exist.

Edit: I already emptied the trash, by the way, but the disk space was still occupied.

---

### Post by jeanjd63 on 2014-01-19
You are sure ?
**sudo  ls  -l  /root/.local/share/Trash/files/**

---

### Post by pieter3 on 2014-01-19
No, the folder does exist, but for some reason, du can't handle the asterisk. Without it works, and using the ls command I can see the file. Can I just remove it with rm?

Edit: removed it! Thank you very much!

---

