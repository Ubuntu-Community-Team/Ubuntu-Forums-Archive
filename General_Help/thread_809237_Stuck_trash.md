---
title: "Stuck trash"
date: 2008-05-27
forum: General Help
---

### Post by roccivic on 2008-05-27
I have some stuff that is stuck in the trash folder, when I try to delete it I get an error:
```
Error removing file: Permission denied
```

Any way I can delete these using the terminal?

Thanks everyone.

Rouslan

---

### Post by TeoBigusGeekus on 2008-05-27
```
sudo rm -r /home/yourusername/.local/share/Trash/files/*
```

---

### Post by soxs on 2008-05-27
Use search: [http://ubuntuforums.org/showthread.php?t=806978&highlight=trash+files](http://ubuntuforums.org/showthread.php?t=806978&highlight=trash+files)
[http://ubuntuforums.org/showthread.php?t=808366&highlight=trash+files](http://ubuntuforums.org/showthread.php?t=808366&highlight=trash+files)

---

### Post by TeoBigusGeekus on 2008-05-27
If I had a euro every time I've answered this in the past month, I'd be a tycoon...

---

### Post by soxs on 2008-05-27
If I got a cent for every Trash-related I saw, I would be #1 under the 10 richest persons on earth.

---

### Post by roccivic on 2008-05-27
Thanks guys, and yeah, sorry for not searching before posting.

Rouslan

---

### Post by fragos on 2008-05-27
It appears that where trash is stored has changed from /home/user/.Trash to /home/user/.local/share/Trash/files/*. My /home/user/.Trash folder is gone but my desktop icon still thinks there are three files in trash.

Since trash now works properly from the new location I tried removing the trash icon from the applet bar and then adding it again. Everything now functions normaly again.

---

### Post by ercferret18 on 2008-06-06
> **TeoBigusGeekus said:**
> ```
sudo rm -r /home/yourusername/.local/share/Trash/files/*
```

this worked. thanks.

---

