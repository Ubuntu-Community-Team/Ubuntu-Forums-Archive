---
title: "How to fix sudoers when you cant init 1?"
date: 2013-11-14
forum: General Help
---

### Post by alexx.stehman on 2013-11-14
I ssh into a virtual machine as the only user defined on the box (mistake #1). 
I hosed sudoers. (mistake #2)
I can not run init 1 to boot to single user mode.
What can I do, other than build a new server?

TIA

---

### Post by TheFu on 2013-11-14
Mount the storage from outside the VM and fix the broken files.
Physical access means COMPLETE control ... unless the file system is encrypted AND you do not know the key.

---

### Post by alexx.stehman on 2013-11-14
Thank you for the reply.

It is hosted on the cloud so I doubt that is an option.

---

### Post by TheFu on 2013-11-14
Well, if it is hosted, can't you just restore from a backup yesterday? There is probably a "panel" on the provider to do that.

Or just contact support and tell them you toasted the /etc/sudoers and ask for a fix. They'll get to it by Tuesday, I'm sure.

---

### Post by Habitual on 2013-11-14
su - root may work?

JD ?

default sudoers file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

stolen from [https://help.ubuntu.com/community/Sudoers#The_Default_Ubuntu_Sudoers_File](https://help.ubuntu.com/community/Sudoers#The_Default_Ubuntu_Sudoers_File)

---

