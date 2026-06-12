---
title: "split up archive"
date: 2008-05-23
forum: General Help
---

### Post by insert_name_here on 2008-05-23
I'm trying to back up a 29gb file onto a FAT32 external hard drive.  Obviously, FAT32 can't deal with something that big.  (Your mom couldn't either... ;) )

So, I'm trying to split it into 2gb pieces with tar or rar.  I'm having trouble with it.

What kind of command should I use that will split up my file into 2gb pieces?

---

### Post by harlan on 2008-05-23
Maybe split is what you're looking for.
   $man split
for options.

---

### Post by ibuclaw on 2008-05-23
And then use **join** to join them back up again!

man join

Simple stuff really. You are practically answering the questions for us! :D

Regards
Iain

---

### Post by mali2297 on 2008-05-23
With **rar** (available in the repos), you can create a split archive with
```

rar a -v2000M example.rar example

```
where *example* is the file/directory that you want to archive. You can later use **unrar** to extract the archive files.


If you want to use **split** (preinstalled), then it is
```

split -d -b2G example example.

```
To put the pieces back together, use **cat**,
```

cat example.* > example

```

A third option is to use **p7zip** (in the repos),
```

7z a -v2g example.7z example

```

---

### Post by insert_name_here on 2008-05-23
Thanks y'all.  I think I'll stick with the rar version, in case I have to reassemble this file with Windows at any point.

---

