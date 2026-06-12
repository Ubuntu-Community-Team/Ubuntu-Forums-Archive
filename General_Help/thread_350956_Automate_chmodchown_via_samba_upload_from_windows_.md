---
title: "Automate chmod/chown via samba upload from windows boxes"
date: 2007-02-01
forum: General Help
---

### Post by ghee22 on 2007-02-01
I have samba setup on my ubuntu box.  I have it so people don't have to login to share and write files.  However, whenever people upload files, the files created are owned by "nobody" in the ubuntu box's correct group.  I would like the files to be under the permissions 770 so that my personal account on ubuntu can move them.

is there a way to automate the process rather than having to physically go on the ubuntu box and chmoding/chowning them after each upload?

---

### Post by lamego on 2007-02-01
Look at your samba config options, you can setup the default files permissions with umask.

---

### Post by ghee22 on 2007-02-01
> **lamego said:**
> Look at your samba config options, you can setup the default files permissions with umask.

i have no idea how to do "umask" i've tried it and set it for 0777 and 1777.  it doesn't seem to work for me..

thanks for the tip but i have no clue how to implement it

---

