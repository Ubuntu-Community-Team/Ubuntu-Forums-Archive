---
title: "User's $HOME/.dmrc file is being ignored, cannot change permissions"
date: 2007-08-21
forum: General Help
---

### Post by Fittersman on 2007-08-21
i cannot change my permissions of my home folder, i want other users to be able to access my files, but not read and write to them anymore.

at login i get this popup that says

```
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```

what can i do to get around this??

---

### Post by merlinus on 2007-08-21
What are the current permissions?

I recently solved this issue, but more info will help.

-merlin

---

### Post by Fittersman on 2007-08-21
current permissions is that other users can read and write, i can (im the owner) read and write, and so can anyone in my group

so, anyone can read and write

---

### Post by merlinus on 2007-08-21
The correct permissions are:

you (owner) - create and delete
group (your group) - access files
others - access files

Otherwise you will continue to get that error message.

Since you are the owner, you should be able to change the permissions using Nautilus.  Right-click on /home/your-folder, left-click Properties, and go to the Permissions tab.

-merlin

---

### Post by Fittersman on 2007-08-21
ive tried that but once i click close and then go back into the permissions area they are reset and do not save

---

### Post by merlinus on 2007-08-21
Have you tried changing the permissions to those above on .dmrc?

You might also try running Nautilus as root and doing it that way:

```

gksudo nautilus

```

-merlin

---

### Post by Fittersman on 2007-08-21
ok, i can save the settings but once i set it to a shared folder they change back....

---

### Post by merlinus on 2007-08-21
What are you meaning by "Once I set it to a shared folder?"

-merlin

---

### Post by Fittersman on 2007-08-22
right click on it then set as shared folder, i want to be able to access my home folder from my laptop running fedora using my wireless router

my setup is as follows

laptop-----(wireless)-----router------(cabled)------desktop

and the router is connected to the internet as well.

---

