---
title: "Creating folders and permissions"
date: 2008-04-21
forum: General Help
---

### Post by turned2black on 2008-04-21
I have a game that I want to play, but the Synaptic SM did not create a "mods" folder. I just want to add a folder, but apparently I have to be logged in as "root." How do I give myself this "permission"?

---

### Post by sdennie on 2008-04-21
I think you will want to use "sudo" to create the directory.  If you know the name of the directory then the doing the following in a terminal should allow you to add it:

```

sudo mkdir the_directory_name

```

---

### Post by george9233 on 2008-04-21
Or you can open the file browser with root permission, by type in terminal:```
gksudo nautilus
``` then go to the directory and create "mods", if you want to do it graphically.

---

