---
title: "How to set permissions on an ext3 partition"
date: 2008-03-10
forum: General Help
---

### Post by slayer^_^ on 2008-03-10
i've gone crazy with it, but here's the magic command:

in terminal:

```
sudo chown -hR user:group /media/disk
sudo chmod g+rwx /media/disk
```

_**you got to change:**_

**user** to your username
**group** to your groupname, but you may not enter a group at all...
**/media/disk** to the path your ext3 partition is mounted to (if you don't know it, you can discover it by rightclicking  the icon of the partition on the desktop and search for mount point)

this is a sort of standard command i am giving you now... it allows to change the owners of the ext3 partition (first string) and the permissions (second string). Notably the second string (as it is configured here) allows all the users of the group indicated in the first string, to read, write and execute files.

If you want more options for the configuration of owners and permissions for your ext3 partition, just type
 
```
man chown
```

to know more about chown and

```
man chmod
```
to know more about chmod.


let me know if you think it is necessary to add info to this guide or if there are troubles with it!

---

### Post by bodhi.zazen on 2008-03-10
Well, your title is mis-leading as that command does not convert file systems to ext3, it just sets permissions.

You may or may not want to use the -R and/or -h flags.

You do not need a : , you can use a .

chown user.group ....

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by slayer^_^ on 2008-03-11
you are right, i had to re-write the thread because of a line breakup and i didn't pay enough attention to the title that, as you say, can be misinterpreted.

i am unable to change it, please feel free to remove this thread!

p.s. i have to say, however, that i found impossible for ubuntu to format a partition in ext3 and gain privileges (or at least modify them in an easy way, that is impossible without a root access...)

---

### Post by bodhi.zazen on 2008-03-11
Sorry you had trouble, if you have similar questions / problems feel free to ask ans we will try to help.

How about if I title this thread How to set permissions on an ext3 partition ?

I think that would help some people (and be better then deletion).

---

### Post by slayer^_^ on 2008-03-11
that's good, I guess... thanx for the interest!!!

---

