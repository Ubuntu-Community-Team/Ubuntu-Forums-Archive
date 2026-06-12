---
title: "Permission"
date: 2007-09-06
forum: General Help
---

### Post by ronnybob on 2007-09-06
I have a second HHD and when I copied and pasted from a CD that had all my music on it  all the folders have locks on them now and the music inside of the folders turn into documents when I click on them and it won't play. I can not change the permission it won't let me, what now? 

Cannot open 3 - Does Anybody Hear Her.mp3

The filename "3 - Does Anybody Hear Her.mp3" indicates that this file is of type "MP3 audio". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by Amof on 2007-09-06
By any chance is this second HDD partitions with NTFS?

Did you try:

```
sudo chown -R yourname
```

---

### Post by ronnybob on 2007-09-06
the sudo thing didn't work and the format is Fat32

---

