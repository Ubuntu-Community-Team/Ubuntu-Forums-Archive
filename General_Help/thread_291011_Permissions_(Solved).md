---
title: "Permissions (Solved)"
date: 2006-11-01
forum: General Help
---

### Post by frente69 on 2006-11-01
Howdy,
I would like to figure out how to do permissions from the GUI.

How do I change the owner, manage groups and set read write permissions on files?

I use KDE on 6.10

---

### Post by matthewstory on 2006-11-01
i believe it's right click, properties, in nautilus.  There should be an owners box, and then under it 3 rows of checkboxes with 3 colums each, Read Write and Execute for owner/group/and everyone else.  This is what you're looking for i think.  Though you can only change permissions for stuff that you own, otherwise you'll have to launch nautilus as root from the CLI with sudo, at which point it would be faster to change the permissions in the CLI.

---

### Post by frente69 on 2006-11-01
Ok,
What if i want two people to have access to a file but not another?

---

### Post by gerowen on 2006-11-01
You could create a new group specifically for that file, and then add those users to it.  Go to System, Administration, Users and Groups.  Click "Manage Groups" then "Add Group".  You can create a new group and select users you want to be a member of that group.  Now go to the permissions of the file in question and change its "group" to the new group you created and you can manage the permissions that way.  To change the file's permissions for the new group via command line do:
```

sudo chmod g+rwx pathtofilehere

```
Hope this helps, :-)

---

### Post by frente69 on 2006-11-02
thanks for that

Cheers,
Frente

---

