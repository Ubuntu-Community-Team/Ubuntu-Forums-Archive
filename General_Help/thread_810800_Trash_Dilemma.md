---
title: "Trash Dilemma"
date: 2008-05-28
forum: General Help
---

### Post by jbaerbock on 2008-05-28
Ok so the simplest (maybe) problem occured today. I tried to trash a file that I had in my /home/downloads folder (user created by me). It went to trash quietly but now it will not empty from trash or restore to folder it came from. Anything I try to do with it is says permission denied. Now I was planning on moving it back then under gksu nautilus deleting it for good but since I cant even move it now my plan failed. Is there a way to open my user trash in sudo mode or something? Please help I dont like my trash full lol.

---

### Post by nick_h on 2008-05-28
You could try copying or deleting the file from the command line.

[http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

Be careful when using the *rm* command.

---

### Post by drs305 on 2008-05-28
Open nautilus with root privileges:
```
gksudo nautilus /home/**username**/.local/share/Trash/files
```

This should take you directly to the normal user trash bin. You mentioned sudo nautilus but it sounded like you didn't actually try it.

You could similarly run the same command replacing 'gksudo nautilus' with 'sudo rm -R' but be careful anytime you use sudo and rm!

---

### Post by jbaerbock on 2008-05-28
I did try it but did not know where the user trash bin was located. By clicking on trash while in root nautilus it took me to the root trash lol no help there. Now that you told me where the user trash is it should be a breeze to clean up, thanks a lot.

---

### Post by jbaerbock on 2008-05-29
So that worked like a charm, good to know where that's at for future reference :P

---

