---
title: "Apt-get and aptitude not working: missing a dir"
date: 2007-01-26
forum: General Help
---

### Post by raul_ on 2007-01-26
```
raul@osiris:/var/lib/apt/lists$ sudo apt-get update
E: Falta directório de listas /var/lib/apt/lists/partial
```

It seems that folder is missing. There is a FILE with that name though. 

```
E: Não foi possível abrir ficheiro de lock /var/lib/aptitude/lock - open (20 Não é um diretório)

```

"Couldn't open blablabla - open (20 is not a directory)"

What happened here? :-k

```
raul@osiris:/var/lib/apt/lists$ ls
lock  partial

```

---

### Post by taurus on 2007-01-26
```
ls -la /var/lib/apt/lists
```

---

### Post by raul_ on 2007-01-26
```
total 1621850348
drwxr-xr-x     3 root       root             8192 2007-01-26 23:30 .
drwxr-xr-x     4 root       root             4096 2007-01-22 15:03 ..
-rw-r-----     1 root       root                0 2007-01-26 23:32 lock
?rwsr-S--- 49428 1218494782 3244615200 3242277696 1936-07-29 10:03 partial
```

---

### Post by taurus on 2007-01-26
Try this.

```
cd /var/lib/apt/lists
sudo rmdir partial
sudo mkdir partial
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by raul_ on 2007-01-26
partial isn't a directory, it's a file :-k and if i try to remove it , it says that it's not allowed. Should i force it?

---

### Post by taurus on 2007-01-26
Partial is a directory on my Edgy machine and it is empty.  So, remove it and create a new directory for it with the "**sudo mkdir partial**" command.

---

### Post by raul_ on 2007-01-26
```

raul@osiris:/var/lib/apt/lists$ sudo rm -rf partial 
rm: não é possível remover `partial': Operação não permitida

```

"not allowed"

i'm out of ideas here :-k i think it got corrupted somehow

EDIT: i'm sure it got corrupted. Look at all those strange numbers in the ls command output

---

### Post by taurus on 2007-01-26
Yes, your partial directory is corrupted big time.  Here's mine.

```

-rw-r----- 1   root root          0 2007-01-20 14:34 lock
drwxr-xr-x 2 root root     4096 2007-01-20 14:34 partial

```
Try to see if you can remove it with nautilus.

```
gksudo nautilus
```

---

### Post by raul_ on 2007-01-26
Nope...not allowed. Am I screwed? :rolleyes:

EDIT: i'll try a fsck. I'll post the results

---

### Post by taurus on 2007-01-26
Try

```
cd /var/lib/apt
sudo rm -rf lists
sudo mkdir lists
cd lists
sudo touch lock
sudo mkdir partial
```
(I assume you know what each command does so I don't have to explain what I was trying to do here.  :)  )

---

### Post by raul_ on 2007-01-26
It seems that partial is absolutely untouchable! I think the approach here is trying to fix it, since we can't remove it and create a new one. 

fsck did nothing. It just said that "/" is clean

---

### Post by taurus on 2007-01-26
So, removing /var/lib/apt/lists (with the sudo command) didn't work, too!  Maybe you can use the LiveCD to remove /var/lib/apt/lists.  Then, create lock and partial directory under /var/lib/apt/lists again.

---

### Post by raul_ on 2007-01-26
I tried your last post with the Live CD, that I used to do the fsck

---

### Post by taurus on 2007-01-26
Are you dualbooting this machine with XP?  If yes, install fs-driver, [http://www.fs-driver.org](http://www.fs-driver.org), and remove "partial" from XP.  Then, create a directory partial again (either in XP or after booting Ubuntu) and see if that works.

---

### Post by raul_ on 2007-01-26
I have a feeling that it won't work again =) i'm trying a fsck again with the correct flags (-c to start) and see if any blocks are corrupt

---

### Post by raul_ on 2007-01-26
```
Pass 2: Checking directory structure
i_file_acl for inode 563736 (/var/lib/aptitude) is 3240671840, should be zero.
Clear<y>? yes

Inode 563736 (/var/lib/aptitude) has invalid mode (075640).
Clear<y>? yes

i_file_acl for inode 563739 (/var/lib/dhcp3) is 3244922208, should be zero.
Clear<y>? yes

Inode 563739 (/var/lib/dhcp3) has invalid mode (0131040).
Clear<y>? yes

Entry 'periodic' in /**var/lib/apt** (547267) has deleted/unused inode 563715.  Clear<y>? yes

i_file_acl for inode 563714 **(/var/lib/apt/lists/partial)** is 3244573920, should be zero.
Clear<y>? yes

Inode 563714 **(/var/lib/apt/lists/partial)** has invalid mode (0176740).
Clear<y>? yes

```

who would know :cool:

Turns out i had LOTS of inode errors. I guess the board (i don't know how to say it in english...where u turn the power on and off)  just went off. It's winter, we have to find ways to warm us =\

 i'm still in the Live CD, gonna try it in a few minutes

---

### Post by raul_ on 2007-01-26
It didn't work at first, but then i tried to delete "partial" again, and it wasn't there. So i just created a new folder, ran apt-get update and i think it's working again. This one was hard :-k 

A little off-topic, but unlike Windows, when i have this sort of system problem in Ubuntu ( i really can't speak for Linux because i haven't tried other distros) i don't fear for my computer. It's amazing how i can just do these tweaks :) *drool*

---

### Post by az on 2007-01-26
Often when an inode is borked, you can just rename the file and move on...

The inode is still broken, but does not bother you.

---

### Post by raul_ on 2007-01-26
I got a lot of inodes moved to the lost+found. what will happen? Will they stay there forever or eventually some(one?) will claim it?

---

### Post by az on 2007-01-27
> **raul_ said:**
> I got a lot of inodes moved to the lost+found. what will happen? Will they stay there forever or eventually some(one?) will claim it?

I don't think so.  But you should also be worried about hardware problems.

Check for bad blocks.

Assuming you / is mounted on /dev/sda1 run

sudo badblocks -s /dev/sda1

---

### Post by raul_ on 2007-01-27
i suppose i can do that in a mounted filesystem? Actually it's sda6 =)

---

