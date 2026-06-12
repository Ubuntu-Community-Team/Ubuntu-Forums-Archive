---
title: "Directory permissions - Need urgent help. how do i reverse a chmod command"
date: 2008-02-13
forum: General Help
---

### Post by duewaynec on 2008-02-13
hi,
i just ran the following command
 # sudo chmod 764 /media/sda8/downloads/linux/ubuntu

now all the files and folders cannot be accessed. how do i undo this last command?
any ideas?

---

### Post by duewaynec on 2008-02-13
another thing, type, date modified, owner, permissions are all unknown.

---

### Post by Trail on 2008-02-13
764 means:

owner: read, write, execute
group: read, write
others: read

If this "/media/sda8/downloads/linux/ubuntu" is a directory, to access it you need execute permissions as well.

To give permission for everyone to access the directory, do:

# sudo chmod a+x /media/sda8/downloads/linux/ubuntu

Where a+x means: a=all users, +=grant permission, x=execute.

To give permission for everyone to write to the directory, do:

# sudo chmod a+w /media/sda8/downloads/linux/ubuntu

If you need something more specific, read the manual of the chmod command by:

#man chmod

---

### Post by Christmas on 2008-02-13
Run
```
sudo chmod 755 /media/sda8/downloads/linux/ubuntu
```
To see owner, permissions etc type:
```
ls -lh /media/sda8/downloads/linux
ls -lh /media/sda8/downloads/linux/ubuntu
```
The first one will show the permissions of all files in the 'linux' directory, including ubuntu, the second one will show for all files inside 'ubuntu' directory.

---

### Post by duewaynec on 2008-02-13
thanks. that did the trick. for a moment i thought it was lost.

thanks again

---

