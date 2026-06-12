---
title: "Only root can create in a mouned windows share"
date: 2007-11-10
forum: General Help
---

### Post by MaverickPS on 2007-11-10
Ok guys, here goes. I am kinda new to linucks , about 2 weeks or so, I am running it on VMware and I love it. But, i have run into this problem:

on my laptop which we will call 'laptop' I have shared a folder called virtushare. In ubuntu if i view the network I can navigate there, and I can see it, right click--properties-- location: "smb://laptop/virtushare"

ok so far so good.

then I make a diretory for where i want to find this stuff:

~/$ mkdir /home/username/winshare

...done...

ok so now I mount then navigate to the folder:

~/$ sudo smbmount //laptop/virtushare /home/username/winshare
~/$ cd /home/username/winshare

then I do a ls -la to see if i see the files, and i do:
~/$ ls -la
drwxr-xr-x 1 root root 4096 2007-11-10 13:30 .
drwxr-xr-x 40 maverick maverick 4096 2007-11-10 12:47 ..
-rwxr-xr-x 1 root root 70 2007-11-10 11:11 hello.txt

so i want to read a file, and i can. now i want to write to the file:

~/$ ifconfig >> hello.txt
~/$ more hello.txt

.. it works fine and outputs the files. just use imagination...


So NOW i want to create files...
~/winshare$ touch foo
touch: cannot touch `foo': Permission denied

and it wont let me do a chmod on the directory, or chown, or anything, but if i do a:

~/winshare$ sudo touch foo

it works fine. ANY IDEAS? this is so frustrating, i dont want to make it so that all of my scripts have to run as root to be able to create files/directories in this shared directory ><

---

### Post by MaverickPS on 2007-11-10
...bump...

---

### Post by fjgaude on 2007-11-11
Can't you simply change the owner of the partition, folder, to something other than root? to your name?

---

