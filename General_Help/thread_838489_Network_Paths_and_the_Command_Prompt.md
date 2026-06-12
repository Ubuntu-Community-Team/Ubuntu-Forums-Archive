---
title: "Network Paths and the Command Prompt"
date: 2008-06-23
forum: General Help
---

### Post by Harry Muscle on 2008-06-23
How do you specify network paths at the command prompt?  For example, I mounted the following location using the graphical user interface:

\\Server\Media

How can I do a cd (change directory) to this path and explore what's on it via the command prompt?  I've tried a whole bunch of things but every time I'm told that the directory doesn't exist.

Thanks for any help,
Harry

---

### Post by sdennie on 2008-06-23
Have a look in ~/.gvfs.  They should show up there.

---

### Post by Harry Muscle on 2008-06-23
Thanks.  One more beginner question.  How would I create a symbolic link to this network location?  Should I point the symbolic link to the folders inside the .gvfs folder or is there another way of creating a symbolic link to network locations?

Thanks,
Harry

---

### Post by sdennie on 2008-06-23
You can probably just:

```

ln -s "/home/your_username/.gvfs/place to link" ~/name_for_place

```

---

