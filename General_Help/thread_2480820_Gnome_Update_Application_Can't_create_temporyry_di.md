---
title: "Gnome Update Application: Can't create temporyry directory"
date: 2022-11-11
forum: General Help
---

### Post by ocram44 on 2022-11-11
Hi,

The Gnome Software app shows Applications that should be updated. The update does not work, the error message: Unable to update xxx: Can't create temporary directory.
Gnome 42, Ubuntu 22.04, Application to update from Flatpak.

Thank you for your help.

---

### Post by Joseph_Fleet on 2022-11-11
Hi ocram44,

If it's a Flatpak application you're having trouble updating. Open a new Terminal window. Enter the command: [FONT=courier new]*sudo flatpak repair.*
[/FONT][FONT=courier new][/FONT]Let us know if the issue persists.[FONT=courier new]
[/FONT]

---

### Post by ocram44 on 2022-11-13
Thank you for your reply. Unfortunately this didn't help. Still the same error message

---

### Post by deadflowr on 2022-11-13
Into to the nitty gritty open a terminal and run
```
flatpak update
```
and post the results.
Depending on what's hanging it up, it might be possible to get a workaround going or something.

A quick search reveals this seems to be a more common problem than I would have ever known,
and not something I have encountered myself.

---

### Post by Joseph_Fleet on 2022-11-13
It's also worth checking the permissions for the */tmp* directory.
```

ls -ld /tmp

```

---

### Post by ocram44 on 2022-11-17
> **deadflowr said:**
> Into to the nitty gritty open a terminal and run
```
flatpak update
```
and post the results.
Depending on what's hanging it up, it might be possible to get a workaround going or something.

A quick search reveals this seems to be a more common problem than I would have ever known,
and not something I have encountered myself.

This worked! All the hanging updates went through. In this case from the terminal it works but not from the Gnome Software Application. Maybe it has to do with user rights of the /tmp directory as Joseph_Fleet suggested. I have drwxrwxrwt 23 root root 4096.

---

### Post by ocram44 on 2022-11-18
> **Joseph_Fleet said:**
> It's also worth checking the permissions for the */tmp* directory.
```

ls -ld /tmp

```

The permissions of /var/tmp have to be checked:
sudo chmod 1777 /var/tmp/

---

