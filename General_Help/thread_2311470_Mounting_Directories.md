---
title: "Mounting Directories"
date: 2016-01-27
forum: General Help
---

### Post by ChrispyChris on 2016-01-27
I tried looking for help in Virtualization, but have received no answers in days. I hope I don't get in trouble for looking elsewhere, but I'm really struggling with this. I'm working on binding or mounting folders. I'm not even sure if I'm understanding this all correctly. I know I can mount /dev/sdc1 to a place after I format it, so that I may use it as a "downloads" folder, for example. At least I think that's correct thinking? I'm also wondering if I can take /home/Test1 and bind it to /home/Test2. Both folders are created and Test1 contains testing1.txt, testing2.txt, testing3.txt. I was under the assumption that if I type "mount --bind /home/Test1 /home/Test2" it would basically copy those text files into Test2, and then if a new file was created in either directory, it would mirror that in the other. Am I completely wrong for thinking this, or what is my problem?

Here is a couple tries of me doing what I'm talking about. Please someone help me grasp this concept, I've been trying for a few evenings now, and it's really frustrating haha. Thanks!

```

root@Subsonic:/home# mount --bind /home/Test /home/Testing -rw
mount: block device /home/Test is write-protected but explicit `-w' flag given
root@Subsonic:/home# mount --bind /home/Test /home/Testing
mount: block device /home/Test is write-protected, mounting read-only
mount: cannot mount block device /home/Test read-only
root@Subsonic:/home#

```

This is to show that I have full permission, I've even does this with the folders as 777.
```

root@Subsonic:/home# ls -l
total 8
drwxr-xr-x+ 2 root root 4096 Jan 27 14:28 Test
drwxr-xr-x+ 2 root root 4096 Jan 27 14:30 Testing

```

---

### Post by steeldriver on 2016-01-27
The '+' at the end of the ls permissions field suggest that the directories have extended attributes set on them - what is the output of

```

lsattr /home/Test

```

for example? Also, is /home/Test a regular directory, or is it itself a mountpoint?

---

### Post by ChrispyChris on 2016-01-27
```

root@Subsonic:/home# lsattr Test
-------------e-- Test/File1.txt
-------------e-- Test/File2.txt
-------------e-- Test/File3.txt
root@Subsonic:/home#

```

/home/Test is a regular directory. In my CT I just created it using mkdir in the /home folder. I never knew about extended attributes. Are these causing the problem?

---

### Post by steeldriver on 2016-01-27
Oops sorry that should have been

```

lsattr **-d** /home/Test

```

(we want to see the directory's attributes, not those of its contents)

---

### Post by ChrispyChris on 2016-01-27
Oh, well it looks kind of the same.

```

root@Subsonic:/home# lsattr -d /home/Test
-------------e-- /home/Test

```

---

### Post by bab1 on 2016-01-27
> **ChrispyChris said:**
> Oh, well it looks kind of the same.

```

root@Subsonic:/home# lsattr -d /home/Test
-------------e-- /home/Test

```
I think @steeldirver misspoke.  The + indicates the use of Linux ACL's (Access Control List).  To see if there are any ACL's you can use this command```
getfacl /home/test/
```

Post the output of that command

---

### Post by ChrispyChris on 2016-01-27
```

root@Subsonic:/home# getfacl /home/Test
getfacl: Removing leading '/' from absolute path names
# file: home/Test
# owner: root
# group: root
user::rwx
group::r-x
other::r-x
default:user::rwx
default:group::r-x
default:other::r-x

```

---

### Post by bab1 on 2016-01-27
> **ChrispyChris said:**
> ```

root@Subsonic:/home# getfacl /home/Test
getfacl: Removing leading '/' from absolute path names
# file: home/Test
# owner: root
# group: root
user::rwx
group::r-x
other::r-x
default:user::rwx
default:group::r-x
default:other::r-x

```
This shows that at least this directory (/home/Test) has standard permissions set for:: owner:group:others.

---

