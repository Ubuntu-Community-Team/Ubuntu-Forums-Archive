---
title: "make link from ~/yyy to /xxx/yyy"
date: 2015-03-02
forum: General Help
---

### Post by Ski_HolmaNM on 2015-03-02
I am planning to dual boot ubuntu and arch, and I want to sync the main folders, (Desktop, Documents, Music...) so I created a third partition, and mounted it under /data. I wnated to make a symlink so that ~/Desktop would Be listed as ~/Desktop, but is stored under /data/Desktop. I ran ln -s /data/Desktop ~/Desktop, but it created the link as a folder under Desktop, rather than making ~/Desktop the link. I changed the command to ln -s -b /data/Desktop ~/ but it returned that I cannot overwrite the directory. How do I do this?

---

### Post by kerry_s on 2015-03-02
ln -f <- will force

use "ln --help" to see options

---

### Post by Ski_HolmaNM on 2015-03-02
Tried that just now. Same result. this is the output:

```
$ ln -s -f /data/Downloads/ ~/
ln: ‘/home/jj/Downloads’: cannot overwrite directory
```

I used downloads this time.

---

### Post by kerry_s on 2015-03-02
i think it has to do with separate partitions, it doesn't seem to want to go from partition to partition, i always got the broken link, but it handles the same partition just fine.

i think you have to go from the mnt point, ie: /media/you/data/..., where ever you have it mounted. i got bored so didn't test, i just keep 1 partition on a separate drive, all i have to do is click on it in the sidebar to mount it, then i just copy/cut/paste/create what ever i want, i leave it separated so nothing happens to it if something go's wrong with the main system, in the past sometimes mounted drives would get corrupted during blackouts, so it's a safety thing for me.

---

### Post by Ski_HolmaNM on 2015-03-02
I finally figured out that I have to delete them, and than create them as links :\ Bit tedious but whatevs. Thank you for your help. (Side note, ~/Desktop cannot be deleted)

---

