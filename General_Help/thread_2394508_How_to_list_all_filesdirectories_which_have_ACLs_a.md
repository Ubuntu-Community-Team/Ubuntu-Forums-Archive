---
title: "How to list all files/directories which have ACLs and/or extended attributes?"
date: 2018-06-17
forum: General Help
---

### Post by &amp;KyT$0P# on 2018-06-17
Title says it all.  I know it's possible, because I've done it before, but I've completely forgot how I did it and I don't seem to be able to figure it out again.  Pretty sure I used [FONT=Courier New]find[/FONT], but beyond that I have no idea, and skimming the man page isn't ringing a bell.

Thanks for any suggestions.

---

### Post by #&amp;thj^% on 2018-06-17
You know me (LOL) ;) always trying to be helpful are you speaking of getfacl and setfacl 
```
getfacl /home/me
getfacl: Removing leading '/' from absolute path names
# file: home/me
# owner: me
# group: me
user::rwx
group::---
other::---

```

```
getfacl /etc
getfacl: Removing leading '/' from absolute path names
# file: etc
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

```
[https://wiki.archlinux.org/index.php/Access_Control_Lists](https://wiki.archlinux.org/index.php/Access_Control_Lists)

---

### Post by &amp;KyT$0P# on 2018-06-17
That doesn't ring a bell either, but [FONT=Courier New]getfacl -s[/FONT] looks good for finding ACLs.  So thanks :) [s]Does it do extended attributes too?[/s]

* Ok looks like it's ACL specific.  After trying to read more about extended attributes, and find something that would list them for a given file, I'm confused about what "extended attributes" means.  I'm looking for the type of extended attributes that rsync's [FONT=Courier New]--xattrs[/FONT] command-line option deals with.  Is it related to the data displayed by [FONT=Courier New]lsattr[/FONT], or is it related to the data displayed by [FONT=Courier New]getfattr[/FONT]?  If the latter, which [FONT=Courier New]rsync[/FONT] option handles the data displayed by [FONT=Courier New]lsattr[/FONT]?

---

### Post by &amp;KyT$0P# on 2018-06-21
bump

---

### Post by &amp;KyT$0P# on 2018-06-22
I think I remember now what I did before.  It was probably something like this -
```
sudo find / -exec ls -ld {} \; | grep -P -i '^[a-z-]{10}[^ ]'
```
But some testing and reading indicates that doesn't cover either type of extended attributes.  I must have been confusing it with Mac OS where [FONT=Courier New]ls[/FONT] prints a @ when extended attributes are present.  So my previous method wasn't a solution.

Looks like I have to somehow combine all three of getfacl, getfattr, and lsattr.

---

### Post by #&amp;thj^% on 2018-06-22
> **halogen2 said:**
> I think I remember now what I did before.  It was probably something like this -
```
sudo find / -exec ls -ld {} \; | grep -P -i '^[a-z-]{10}[^ ]'
```
But some testing and reading indicates that doesn't cover either type of extended attributes.  I must have been confusing it with Mac OS where [FONT=Courier New]ls[/FONT] prints a @ when extended attributes are present.  So my previous method wasn't a solution.

Looks like I have to somehow combine all three of getfacl, getfattr, and lsattr.

Wow that's a heavy list to load.:) 
```
sudo find / -exec ls -ld {} \; | grep -P -i '^[a-z-]{10}[^ ]'
```
I wish i could have a definite idea as to what your desired result should look like, but as of now I'm thoroughly confused  :D

---

### Post by &amp;KyT$0P# on 2018-06-22
> **1fallen said:**
> I wish i could have a definite idea as to what your desired result should look like, but as of now I'm thoroughly confused  :D
Ok here's the back story.  Last week I discovered that my [FONT=Courier New]rsync[/FONT] wrapper script that I use for backing up my whole system was not passing [FONT=Courier New]--acls[/FONT] and [FONT=Courier New]--xattrs[/FONT] options to rsync.  I've fixed that now, but I need to assess what this means for my existing backups.  Step 1 is figuring out which files and directories could be affected, if any.  That's what this thread is about.

Does this help clarify what I'm trying to do here?

---

### Post by #&amp;thj^% on 2018-06-22
> **halogen2 said:**
> 
Does this help clarify what I'm trying to do here?
Yes that covers it nicely now. ;) But I will have to defer to someone wiser, I just don't use rsync. :(
I also now have a great interest in this thread>>>for higher education. :)

---

### Post by &amp;KyT$0P# on 2018-07-11
I found an answer somewhere that basically said rsync's [FONT=Courier New]--xattrs[/FONT] option only preserves the extended attributes listed by [FONT=Courier New]getfattr[/FONT], and that the extended attributes listed by [FONT=Courier New]lsattr[/FONT] are too filesystem-specific for tools like rsync to handle.

Anyway I think this might be somewhat moot now since the files and folders with ACLs did have their ACLs backed up when I did my next incremental backup.  Thanks for the replies.

---

