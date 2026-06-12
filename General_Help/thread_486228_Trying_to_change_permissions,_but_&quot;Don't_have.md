---
title: "Trying to change permissions, but &quot;Don't have permission&quot;"
date: 2007-06-27
forum: General Help
---

### Post by czanchez on 2007-06-27
I partitioned my laptop to have 3 different partitions. 1 for ubuntu, 1 for Vista, and one for files to share between the two. Basicly I want to have one storage space, that will house all my files and they will be in the same spot no matter which OS i'm in.

Though, I can not figure out how to give myself permission to write to the partition.

This is my FStab, and only the root has permission to read and write.
> 
/dev/sda3       /media/Files    vfat    iocharset=utf8,umask=000        0       0


I logged in as root and tried to go in the properties and change the permission that way, but no luck.

I heard of chown and decided to try to use that to change permissions, and supposedly when you use sudo you can do anything, but it tells me I don't have permission.

Here is my console.
> 
domagoj@blackbook-ubuntu:~$ sudo chown domagoj /media/Files
chown: changing ownership of `/media/Files': Operation not permitted
domagoj@blackbook-ubuntu:~$


I'm new to Linux and Ubuntu, but I really like it so far, but this seems like a real pain to get right.

Thanks for the help

---

### Post by merlinus on 2007-06-27
Try this:

```

sudo chown -R username:username /media/Files

```

username is your login id.

-merlin

---

### Post by theDaveTheRave on 2007-07-02
Merlinus.

The other method of doing this is to use a root permissions file manager (Nautilus with Gnome, not sure what with KDE)

type

<sudo nuatilus> and it will ask or your Admin password, then a root control Nautilus window will startup.

if you do like the command line (and practice is allways good for those of who do), as well as having <chown> - change owner, you may try <chmod> on the selected files.

Dave

---

### Post by Analord on 2007-07-03
chown/chmod are not working on fat32 partition.

U should edit your /etc/fstab and find a line for your partition and change it.
or smth similar, stuff that counts is really vfat and user,noauto 0 0

# /dev/sda3
/media/Files     vfat    user,noauto 0 0

---

### Post by theDaveTheRave on 2007-07-05
Hi all.

I have been having games getting read /write permissions to function on the Vista partition.

and I haven't been able to partition the device that hold onto Vista either, in short it has been lots of fun and games.

it seems however that I may have found a solution, not elegant, a bit scary (used diskpart in dos), but hopig to be able to report a fully funcioning shared area for ubuntu and windoze common files that I use.

I'll write a howto later tonight, once I have confirmed that this has worked for me.

Dave

---

