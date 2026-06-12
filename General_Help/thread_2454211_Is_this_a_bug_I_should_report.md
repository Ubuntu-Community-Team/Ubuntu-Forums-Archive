---
title: "Is this a bug I should report?"
date: 2020-11-24
forum: General Help
---

### Post by Goettschwan on 2020-11-24
Hi, I run a 20.04LTS installation on two different SSD drives, where one contains boot and swap, and the other is mounted as home. After a hardware upgrade the system booted and went to the login screen just fine, but went into an eternal wrong password loop. I have seen bug reports for that loop on other versions and Linux flavours. I could login via console login (ctrl alt F3 i think), and found out that home wasn't there - /home was just an empty folder. I realized that this had to have a connection to my hardware upgrade and double checked and found that I had not connected the SATA cable to the second SSD, hence the system booted with an FSTAB pointing to drive for /home which didn't exist. 

After connecting the drive, the system functions just fine. 

My question is, should this be reported as a bug (apparently, you cannot login via graphical interface when home suddenly is gone/empty - don't know if this is reproduceable), and if so, how (it isn't like I can point out a package?)

---

### Post by CelticWarrior on 2020-11-24
Not a bug.

---

### Post by guiverc on 2020-11-25
A *gui* login requires temporary work files to be created & written to; those files are in $HOME or the user directory. If the files cannot be created/modified, the login will fail & the user is logged out (no error message). 

That is expected behavior.

 If a text terminal login is tried, it should succeed (no work files are needed there) for exploration & correction of whatever *out-of-space *error condition exists (other users of the system, if they exist and have space in their $HOME or user directories will still be able to login via *gui*)

---

### Post by Goettschwan on 2020-11-26
OK thank you all for your advice :)

---

### Post by gsahli on 2020-11-26
To avoid that specific issue, here's what I do -
Keep the home directory on the boot drive, but link (ln -s) to the typical home folders (Documents, Downloads, etc) on the second drive.

---

