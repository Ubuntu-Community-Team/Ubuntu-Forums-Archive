---
title: "Cannot remove, file exists problem"
date: 2007-05-31
forum: General Help
---

### Post by thatbear on 2007-05-31
Hi,
I am simply trying to rm a directory but I get the following error:

```
tim@tim-desktop:/media/icybear/.Trash-tim$ rm -r DanceofDeath/
rm: cannot remove directory `DanceofDeath/': File exists
```

If anyone has seen this before then an explanation of how to fix it would be very much appreciated.
Thanks.

---

### Post by jimbob on 2007-05-31
Have you tried rm -rf  <file/dir name>?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by thatbear on 2007-05-31
> **jimbob said:**
> Have you tried rm -rf  <file/dir name>?

I have indeed, same error :(

---

### Post by jimbob on 2007-05-31
What does it show when you do an [COLOR="RoyalBlue"]ls -al [/COLOR]on that directory?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by thatbear on 2007-05-31
```
tim@tim-desktop:/media/icybear/.Trash-tim$ ls -al DanceofDeath/
total 4
drwxrwxrwx 1 root tim 4096 2007-05-17 14:44 .
drwxrwxrwx 1 root tim    0 2007-05-31 15:58 ..

```

---

### Post by jimbob on 2007-05-31
What is it that is mounted on /media/icybear ?  Is it some external device?

Try backing up one directory level to .Trash-tim if there is nothing important in there and repeat the rm -rf on it.  You can always recreate that directory.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by eggdeng on 2007-05-31
F ile belongs to root, you need to use ```
sudo rm whatever
```

---

### Post by thatbear on 2007-05-31
> **eggdeng said:**
> F ile belongs to root, you need to use ```
sudo rm whatever
```

Annoyingly, that doesn't work. I just get the same file exists error.

> **jimbob said:**
> What is it that is mounted on /media/icybear ?  Is it some external device?

Try backing up one directory level to .Trash-tim if there is nothing important in there and repeat the rm -rf on it.  You can always recreate that directory.

Attempting to remove the whole .Trash directory also yields the same error.

Icybear is an ide hard drive connected through a pci slot using a raid card. It is ntfs, in case thats of any use.

---

### Post by jimbob on 2007-05-31
Can you delete [COLOR="Red"]any[/COLOR] files on that drive at all? Try copying a file to a new name and deleting the old one and see if that works.  The fact that it is connected as you have it and is an ntfs volume might have something to do with it.

I guess if it was me I would next try to connect the drive via a conventional ide cable and see if the problem persists.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by szaka on 2007-05-31
The problem is answered here: [http://ntfs-3g.org/support.html#emptydir](http://ntfs-3g.org/support.html#emptydir)

---

### Post by thatbear on 2007-05-31
Awesome, it is finally gone.
Thanks to szaka for the solution and to everyone else. Much obliged.

---

