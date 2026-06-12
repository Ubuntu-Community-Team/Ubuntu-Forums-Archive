---
title: "[SOLVED] cannot erase RPM-4.2 file"
date: 2007-08-17
forum: General Help
---

### Post by sdim on 2007-08-17
Hi,everyone.Just joined the club,so good evening to all.
I've been trying to erase a file/program I downloaded while searching for something 2 days ago,but I can't seem to be able to erase it now,so it's stuck on my desktop.
Tha name is "RPM-4.2" and while checking it,I saw that I have no rights over it,it's locked or something.It says I'm not the owner, so I can't do anything to the file.
Any suggestions?
I've tried _sudo rm FILENAME_ but nothing happens.Instead,it says "cannot remove,is a directory".

Anyone?

---

### Post by ThrobbingBrain66 on 2007-08-17
```
sudo rm -r filename
```

---

### Post by sdim on 2007-08-18
"No such file or directory".That's the message after applying _sudo rm -r FILENAME_.
Thanks anyway...

---

### Post by ThrobbingBrain66 on 2007-08-18
You have to be in the same directory as the file to delete it.

For example, if RPM-4.2 is on your Desktop, you should enter
```
cd Desktop
``` and then
```
sudo rm -r RPM-4.2
```

Don't forget the extension either, if it's not a folder.

---

### Post by sdim on 2007-08-18
Many thanks! It worked!

---

