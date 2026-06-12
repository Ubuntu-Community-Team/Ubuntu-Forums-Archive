---
title: "[SOLVED] Remove mounted iso file"
date: 2008-01-25
forum: General Help
---

### Post by ajgreeny on 2008-01-25
Can anyone help me remove the folders and files from a mounted aptoncd iso.

I made a folder in my home folder ~/iso and mounted the iso file with ```
sudo  mount -o loop -t iso9660 aptoncd-20080113-CD1.iso /home/andrew/iso
```Now that I want to remove the folder  ```
sudo rm -R /home/andrew/iso
``` I find that it is not possible and the errors keep coming saying it is a read only file system.  I think I need to chmod, but I'm not certain what the command should be and ```
sudo chmod -R 777 /home/andrew/iso
```did not help.  What am I not getting right, or have I got things completely wrong, and I will not be able to remove that folder at all?  I find that hard to believe, as almost anything seems possible in linux, if you know the correct command.

---

### Post by taurus on 2008-01-25
Why don't you try to umount it first and then remove the /home/andrew/iso directory.

```
sudo umount /home/andrew/iso
sudo rmdir /home/andrew/iso
```

---

### Post by sisco311 on 2008-01-25
```
sudo umount ~/iso
```

---

### Post by ajgreeny on 2008-01-25
Thanks guys, I just knew there was a simple thing I was overlooking!  By a roundabout manner I did it after I had booted into Mint on the same machine, and removed it from there, but of course on rebooting it would have unmounted, wouldn't it?
There are times when you feel like a great twit aren't there?  Thanks again.

---

### Post by gvartser on 2008-01-25
Had to do a little test..


What i found out playing arround with it for a bit, wanted to know what happened if i just moved the files. would the inodes be updated.

1) First mount the iso file.
```
sudo mount -o loop /tmp/vista.iso /movies
```

2) Then start a copy of vista to a local directory.
```
cp -R -v /mnt/vista/* /tmp/vista
```

3) While I see the copy (file by file), I rename the iso file to something else:
```
mv /tmp/vista.iso /tmp/vista.iso.MOVED

```

Still seeing the other window with the file copy, it hasn't stoped.
and after a while the file copy completes.. 


/g

---

