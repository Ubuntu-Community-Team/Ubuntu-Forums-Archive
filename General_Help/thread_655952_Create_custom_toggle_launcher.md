---
title: "Create custom toggle launcher"
date: 2008-01-02
forum: General Help
---

### Post by penguinfan on 2008-01-02
Heppie New Year community,

How do i  create a toggle launcher that will:
a - mount a remote nfs file system
b - open mountpoint

THEN  if the file system mounted successfully;
a - the launcher icon should change
b - the launcher name should change

Consequently if i click the launcher again, the reverse should happen. (eg. unmount filesystem and change launcher's properties to default)

Any help would be appreciated

PS you thought this was going to be just another 'create custom launcher' post hey :)

---

### Post by penguinfan on 2008-01-02
OK, what i have so far is this

I created a new file in /bin

sudo vi /bin/mnt_toggle_launcher

#!/bin/bash
	gksudo mount ip.address:/remote/folder/to/be/mounted /local/mount/point
	gksudo nautilus /local/mount/point

sudo chmod +x /bin/mnt_toggle_launcher

This works great. Obviously what i need is a 'if' statement that checks if the filesystem was mounted successfully, then change the launcher icon and name and then on the next click should unmount and do the reverse.

thanx

---

### Post by penguinfan on 2008-01-02
OK,
This is as far as i got.
pls check it out. Obviously the credit goes to the linux community.

This works for mounting / unmounting the relevant file-systems, BUT i still need to find out how to check if the file-system is already mounted before running the script AND a way to catch errors.

---

