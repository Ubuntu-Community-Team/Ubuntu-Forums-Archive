---
title: "[SOLVED] Just when I thought I was getting it right"
date: 2008-01-06
forum: General Help
---

### Post by barnowl13 on 2008-01-06
I have recently got my Ubuntu on line and had to do loads of update and now my Ubuntu is right up to date but when I went to check to see if there were any more update I got the message blow?

Can anyone help?

"Could not initialize the package information 

A unresolvable problem occurred while initializing the package information. 

Please report this bug against the 'update-manager' package and include the following error message: 

'E: Dynamic MMap ran out of room, E:Error occurred while processing tome (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

When I tried to go into 'update manager' I got the same message as above?:confused:

---

### Post by bapoumba on 2008-01-06
Please try:
```
sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by barnowl13 on 2008-01-06
That seems to have worked thank you for your help!!! I am sure I will be back with some more problems :)

---

