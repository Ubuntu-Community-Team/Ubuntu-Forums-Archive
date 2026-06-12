---
title: "Update Manager error on startup"
date: 2007-06-20
forum: General Help
---

### Post by Nevtus on 2007-06-20
When I start ubuntu I get the following error message from the update manager.

> Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

Can anyone help me fix this?

---

### Post by cogadh on 2007-06-20
Do this in a terminal:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_backup
```
That will rename the corrupted status file so apt won't see it anymore. Next run this:
```
sudo apt-get update
```
This will re-create the status file, hopefully without the same problem. Update manager should work fine after that.

---

### Post by Nevtus on 2007-06-20
When I try running update after renaming the corrupt status file it doesn't create a new one and just stops saying that there is no such file.

---

### Post by cogadh on 2007-06-20
Are you still getting the other errors?

---

### Post by Nevtus on 2007-06-20
Nope, when the status file is renamed I get -
> E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

If I rename the file back to 'status' it goes back to the original error.

---

### Post by inoxllor on 2007-06-22
(...) Do this in a terminal:
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_backup
*That will rename the corrupted status file so apt won't see it anymore. *

Next run this:
**sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status**
*To restore an old status file that is ok*

Then
**sudo apt-get update**

That may solve your problem. :D

---

### Post by inoxllor on 2007-06-22
by the way, if you get a stupid error that doesn't allow you to install things via apt-get or via synaptics, use this:
**sudo dselect update **

It worked like a charm for me. :D

---

