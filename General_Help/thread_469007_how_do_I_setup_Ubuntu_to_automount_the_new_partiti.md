---
title: "how do I setup Ubuntu to automount the new partitions"
date: 2007-06-09
forum: General Help
---

### Post by vadania on 2007-06-09
I have Ubuntu 7.04 Feisty Fawn.

I had 2 hard drives, one with ext3 and one with ntfs partitions.
I had recently reformat the ntfs partitions to ext3 (Goodbye Windows and good riddance!).
Currently I have manually mounted the new partiton with gparted -> right click on partiton name -> mount. 
The system requests me to be root to be able to write files in the new partitions.
The problem is how do I setup Ubuntu to automount (mount at boot time) the new partitions. I also need to write files, create directories on them without being root.

---

### Post by xthund3rh3adx on 2007-06-09
that is odd, since Ubuntu should already automount drives when you startup your system.

to be root, you need to know your roots password. enter this to make one:
sudo passwd root

then enter the password

to be root in terminal, enter 
su

then type the password you just made. You should now be in a root terminal



as for the other drive, try reformatting it via hte ubuntu livecd. Maybe then Ubuntu will reconize it as a new hard drive and automount it itself

---

### Post by vadania on 2007-06-09
Ok, I know I can enable root, but i prefer not to. I belive it is more secure this way.
I can do fine with sudo su, if I really need to become root.

> **xthund3rh3adx said:**
> 

sudo passwd root

then enter the password

to be root in terminal, enter 
su



What I am asking for is a guide /application (GUI prefered, not CLI) to edit /etc/fstab easily. (or whatever is read to automount partitions)
Will reboot again, see if the system mounts the new partitions correctly.

Update: The system automounted the new ext3 partitions with root access.
Can I use the livecd to change my current installation? I do not want to reinstall everything!

---

### Post by vadania on 2007-06-09
I belive I found the problem by reading fstab
 ```
sudo gedit /etc/fstab
```

The problem is that I have installed automatix which changed the mount options to those partitions. Being non standard entries, Ubuntu did not know it has to delete them.

I'll try to comment the troublesome entries in fstab.

---

### Post by martinrandau on 2007-06-09
Generally you want something like

```
/dev/sda4       /media/multimedia       ext3    defaults,user,rw               0 0
```

where sda or hda depends on what kind of hard drive you have and the mount point (/media/multimedia in my case) must exist. 

The option "user" lets the user mount/unmount it and "rw" lets you read/write. The last column "0 0" says that we don't want file checks at boot on this partition but you can of course change this to, "0 1" (not sure here).

Hope this helps!

---

### Post by MattJ100 on 2007-06-09
A little off-topic for the thread, but regarding logging in as root, the easiest way is: sudo -i

Enabling the root account is in general [not a good idea]("https://help.ubuntu.com/community/RootSudo?highlight=%28root%29#head-6cfb89699f99dbeee57c81c64945454d6ded2fac").

---

### Post by vadania on 2007-06-09
> **martinrandau said:**
> Generally you want something like

```
/dev/sda4       /media/multimedia       ext3    defaults,user,rw               0 0
```

where sda or hda depends on what kind of hard drive you have and the mount point (/media/multimedia in my case) must exist. 

The option "user" lets the user mount/unmount it and "rw" lets you read/write. The last column "0 0" says that we don't want file checks at boot on this partition but you can of course change this to, "0 1" (not sure here).

Hope this helps!

It is the answer I expected, but it doesn't help.
I also experience some wierd behaviour with gparted: I unmount partition sdb3, I unmount sdb1 and then, 
sdb3 gets automatically remounted! I unmount sdb3 again, sdb1 gets remounted.

---

### Post by smsmith050 on 2007-06-11
When I first setup Ubuntu it would auto mount my partitions and I could access them. Now after updates Ubuntu does not mount these partitions any more. 
I can edit the fstab and force the partitions to be mounted under my uid gid so I can access them.

Will it break the once-working auto mount if I edit fstab?
Will the auto mount ever work again?

thanks

---

### Post by stchman on 2007-06-11
> **vadania said:**
> I have Ubuntu 7.04 Feisty Fawn.

I had 2 hard drives, one with ext3 and one with ntfs partitions.
I had recently reformat the ntfs partitions to ext3 (Goodbye Windows and good riddance!).
Currently I have manually mounted the new partiton with gparted -> right click on partiton name -> mount. 
The system requests me to be root to be able to write files in the new partitions.
The problem is how do I setup Ubuntu to automount (mount at boot time) the new partitions. I also need to write files, create directories on them without being root.

I have a tutorial on mounting partitions using Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

It works.

---

### Post by smsmith050 on 2007-06-11
Thanks
That seems like a good plan. You get a known mount point name for each partition rather than disk, disk-1 .......

---

### Post by vadania on 2007-06-17
stchman: Even with your guide, I could not mount partitions correctly.
Still waiting for that tool - CLI scripts would do better than /etc/fstab.

---

