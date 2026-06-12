---
title: "Create Symlink from /dev/sda1 to home"
date: 2017-02-11
forum: General Help
---

### Post by webmanoffesto on 2017-02-11
On reboot I have 
/home/tom which has fodlers: Desktop, Documents, and Downloads
Those are empty.
How do I browse and get the full /sda1/ path to the folders on /sda1/ which do have my files

Right now, using Files (Nautilus) I can't get to (don't know how to get to) /sda1/.
If I use "sudo mount /dev/sda1 /home"
then /sda1/ mounts as Home and I don't see the full path.

My OS is in sda5
My data/files are in sda1

tom@tom-HP-ProBook-450-G3:~$ lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sr0 11:0 1 1024M 0 rom 
sda 8:0 0 931.5G 0 disk 
&#9500;&#9472;sda2 8:2 0 1K 0 part 
&#9500;&#9472;sda5 8:5 0 18.6G 0 part /
&#9500;&#9472;sda1 8:1 0 862.3G 0 part /
&#9492;&#9472;sda6 8:6 0 50.6G 0 part [SWAP]

In Files (Nautilus) if I go to Other Locations it appears that only sda5 is mounted.

I should be able to use a terminal command such as
```
[FONT=gotham]ln -s /sda1/data/documents /home/username/documents[/FONT]
```[FONT=gotham]
But I want to carefully confirm the details before I run the command.[/FONT]

---

### Post by howefield on 2017-02-11
Duplicate closed.

---

