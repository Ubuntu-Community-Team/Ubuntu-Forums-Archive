---
title: "[SOLVED] Can't get &amp;quot;find&amp;quot; to work"
date: 2008-04-02
forum: General Help
---

### Post by MountainX on 2008-04-02
Can anyone explain to me what I am doing wrong when I try to find all files with "scite" in the name? (I'm trying to location the right folder for placing a new scite macro file.)

myuser@MyUbuntu:~$ man find
myuser@MyUbuntu:~$ find -mount -name scite*
find: ./.dbus: Permission denied
myuser@MyUbuntu:~$ sudo find -mount -name scite*
find: ./.gvfs: Permission denied
myuser@MyUbuntu:~$ 

As you can see from above, "man find" wasn't any help. :(

---

### Post by Slushdoot on 2008-04-02
You have to first run updatedb as root to create the index of names.
sudo updatedb

Have you done this yet?

---

### Post by MountainX on 2008-04-02
> **Slushdoot said:**
> You have to first run updatedb as root to create the index of names.
sudo updatedb

Have you done this yet?

Thanks. No, I haven't done updatedb (and I had never heard of that). Can I use grep or something else to search without making an index?

---

### Post by soldats on 2008-04-02
try running find with sudo or as root

---

### Post by MountainX on 2008-04-02
> **soldats said:**
> try running find with sudo or as root

See my original post.

---

### Post by Slushdoot on 2008-04-02
I imagine that you could use some other tool to search in that fashion, though I don't know why that would be better than running updatedb.  On most modern systems it'll take something like 15 seconds to run the first time and it will let you use find and locate.

---

### Post by MountainX on 2008-04-02
> **Slushdoot said:**
> I imagine that you could use some other tool to search in that fashion, though I don't know why that would be better than running updatedb.  On most modern systems it'll take something like 15 seconds to run the first time and it will let you use find and locate.

I didn't want to try it because nothing seems to be working right with my file system. Plus I don't know if it will also index mounted partitions.

---

### Post by cdenley on 2008-04-02
> 
You have to first run updatedb as root to create the index of names.


I don't think so. You must be thinking of locate.

> myuser@MyUbuntu:~$ man find
myuser@MyUbuntu:~$ find -mount -name scite*
find: ./.dbus: Permission denied
myuser@MyUbuntu:~$ sudo find -mount -name scite*
find: ./.gvfs: Permission denied
myuser@MyUbuntu:~$ 

I don't think you can use wildcards in the "name" argument unless you escape it. Try this:
```

find -mount -name scite\*

```
If the user you run find as doesn't have permission to access one of the directories you are searching, it will give you a permissions error. I'm not sure, but I think it will continue to search what it does have access to.
```

ls -ld .dbus
ls -ld .gvfs

```

---

### Post by cdenley on 2008-04-02
> **MountainX said:**
> I didn't want to try it because nothing seems to be working right with my file system. Plus I don't know if it will also index mounted partitions.

updatedb indexes files in a database, and this is done daily on a default ubuntu install. It ignores network filesystems, cd/dvd filesystem, and anything in /media. Indexing makes searching with locate much faster, but the results aren't always current.
```

cat /etc/updatedb.conf

```

---

### Post by MountainX on 2008-04-02
> **cdenley said:**
> 
I don't think you can use wildcards in the "name" argument unless you escape it. Try this:
```

find -mount -name scite\*

```
If the user you run find as doesn't have permission to access one of the directories you are searching, it will give you a permissions error. I'm not sure, but I think it will continue to search what it does have access to.
```

ls -ld .dbus
ls -ld .gvfs

```

Thanks for the tip about escaping the wildcard. However, after trying that I still the exact same error messages as my original post. I tried it again both with and without sudo and the errors were exactly as originally posted.

ls -ld .dbus
drwx------ 3 root root 4096 2008-03-26 14:32 .dbus

but I am running find with sudo. What is going on? :confused:

---

### Post by MountainX on 2008-04-02
> **cdenley said:**
> updatedb indexes files in a database, and this is done daily on a default ubuntu install. It ignores network filesystems, cd/dvd filesystem, and anything in /media. Indexing makes searching with locate much faster, but the results aren't always current.
```

cat /etc/updatedb.conf

```

OK, I tried it:
sudo updatedb
myuser@MyUbuntu:~$ cat /etc/update.conf
cat: /etc/update.conf: No such file or directory

And I tried another application I have installed (BasKet):
sudo find -mount -name basket
find: ./.gvfs: Permission denied

:confused::confused::confused::confused::confused:

---

### Post by cdenley on 2008-04-02
root can't read .gvfs, and your user account can't read .dbus. It is working as expected.
```

cdenley@ubuntu:~$ sudo ls .gvfs
ls: cannot access .gvfs: Permission denied

```
The user can't look for files where it does not have access, so find gives you an error, as it should.

> myuser@MyUbuntu:~$ cat /etc/update.conf
cat: /etc/update.conf: No such file or directory
The file was /etc/update**db**.conf, and I was only pointing out where the rules I was referring to for updatedb are located, in case you were interested.

If you want to search the indexed database, use locate
```

locate */scite*

```

---

### Post by MountainX on 2008-04-02
> **cdenley said:**
> root can't read .gvfs, and your user account can't read .dbus. It is working as expected.
```

cdenley@ubuntu:~$ sudo ls .gvfs
ls: cannot access .gvfs: Permission denied

```
The user can't look for files where it does not have access, so find gives you an error, as it should. The file was /etc/update**db**.conf, and I was only pointing out where the rules I was referring to for updatedb are located, in case you were interested.

Thank you. So now that we know **find** is working as it should, why will it not find scite for me?

I just tried this:
sudo find -mount -name SciTEFAQ.html
find: ./.gvfs: Permission denied

 ls -la /usr/share/scite/SciTEFAQ.html 
-rw-r--r-- 1 root root 13806 2008-01-29 13:49 /usr/share/scite/SciTEFAQ.html

Do you see a problem with any of this?

I did run sudo updatedb earlier. (It took only about 1 second. Is that normal?)

---

### Post by herbster on 2008-04-02
You don't need to ecape with find. I use

```
find -iname "*foo*"
```

all the time.

---

### Post by MountainX on 2008-04-02
> **cdenley said:**
> 
If you want to search the indexed database, use locate
```

locate */scite*

```

locate works. find doesn't work. What am I misunderstanding? Thanks for your patience.

---

### Post by MountainX on 2008-04-02
> **herbster said:**
> You don't need to ecape with find. I use

```
find -iname "*foo*"
```

all the time.

I just tried this (using -iname instead of -name). Same bad result:

sudo find -mount -iname SciTEFAQ.html
find: ./.gvfs: Permission denied

ls -la /usr/share/scite/SciTEFAQ.html 
-rw-r--r-- 1 root root 13806 2008-01-29 13:49 /usr/share/scite/SciTEFAQ.html

EDIT: I also tried this:

sudo find -mount -iname "*SciTEFAQ.html"
find: ./.gvfs: Permission denied

---

### Post by MountainX on 2008-04-02
maybe the problem is that I don't understand the -mount option.

Does it exclude everything mounted via fstab? If so, then there wouldn't be anything to search. And if that is the case, how can -mount be useful at all? Isn't every storage device mounted in some way?

---

### Post by cdenley on 2008-04-02
> You don't need to ecape with find.
Escape or quotes, whatever uses the asterisk in the argument literally.

> 
I just tried this (using -iname instead of -name). Same bad result:

sudo find -mount -iname SciTEFAQ.html
find: ./.gvfs: Permission denied

ls -la /usr/share/scite/SciTEFAQ.html
-rw-r--r-- 1 root root 13806 2008-01-29 13:49 /usr/share/scite/SciTEFAQ.html 

First of all, find searches in the current working directory if you don't specify a path. Since you're running this in your home directory, it is searching in your home directory. If you want to search your entire filesystem, you can use
```

sudo find / -mount -iname scite\*

```
It will still give you an error for directories root does not have permission to access. I believe these directories won't be read by updatedb either, but since locate only reads the index, you don't see a permission error.

---

### Post by MountainX on 2008-04-02
> **cdenley said:**
> 
```

sudo find / -mount -iname scite\*

```
It will still give you an error for directories root does not have permission to access.

Perfect! Thank you! (and no error at all)

```
 sudo find / -mount -iname scite\*
/var/cache/apt/archives/scite_1.75-1ubuntu1_i386.deb
/var/lib/dpkg/info/scite.postinst
/var/lib/dpkg/info/scite.postrm
/var/lib/dpkg/info/scite.md5sums
/var/lib/dpkg/info/scite.list
/usr/bin/scite
/usr/share/applications/scite.desktop
/usr/share/man/man1/scite.1.gz
/usr/share/menu/scite
/usr/share/app-install/desktop/scite.desktop
/usr/share/doc/scite
/usr/share/scite
/usr/share/scite/SciTELexer.html
/usr/share/scite/SciTEExtension.html
/usr/share/scite/SciTERegEx.html
/usr/share/scite/SciTEIco.png
/usr/share/scite/SciTE.properties
/usr/share/scite/SciTEDownload.html
/usr/share/scite/SciTEFAQ.html
/usr/share/scite/SciTEGlobal.properties
/usr/share/scite/SciTEDirector.html
/usr/share/scite/SciTEExtras.html
/usr/share/scite/SciTEImage.html
/usr/share/scite/SciTE.html
/usr/share/scite/SciTELua.html
/usr/share/scite/SciTEDoc.html
/usr/share/scite/SciTEExternalLexer.html
:~$ 
```

---

### Post by herbster on 2008-04-02
You can't run find/locate when you don't have permission for the file/dir, and use

```
find /path/to/look -iname "*foo*"
```

---

### Post by MountainX on 2008-04-02
It seems rare that I get my questions answered 100% completely -- but in this thread that did happen. Thank you all so much for such detailed responses! 
:)

---

