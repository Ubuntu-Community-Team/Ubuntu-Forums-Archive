---
title: "Copy files alphabetically"
date: 2007-12-21
forum: General Help
---

### Post by Ranguvar on 2007-12-21
I am using a mobile device that displays files based on creation date, newest file last. There is no way to change this. It is rather annoying for pictures that go in a series (001.png, 002.png, etc.) All file copy utilities I know of, like Windows Explorer and Kubuntu's copying, seem to choose some random order to copy in. Is there any way to change this behavior so it copies alphabetically? Or a separate utility?

Thanks :D

---

### Post by dcstar on 2007-12-21
> **Ranguvar said:**
> I am using a mobile device that displays files based on creation date, newest file last. There is no way to change this. It is rather annoying for pictures that go in a series (001.png, 002.png, etc.) All file copy utilities I know of, like Windows Explorer and Kubuntu's copying, seem to choose some random order to copy in. Is there any way to change this behavior so it copies alphabetically? Or a separate utility?

Thanks :D

You need a script to list each file in alphabetical order and then copy it (probably using the exec() function), you should be able to search out something either in the forums or on the 'net.

---

### Post by pyronaut on 2007-12-21
how about something like ls >> filenames.txt  and then use either rysnc [read filelist from file] or write a small script in python etc

---

### Post by nick_h on 2007-12-22
Filename expansion in bash seems to be alphabetical.

---

### Post by vishzilla on 2007-12-22
In Nautilus, there is "Select Pattern" that selects files according to the argument you give in like for example all files starting with A you enter 'A*', filetype like png you enter '*.png'. I am not sure about Dolphin or whatever you are using!

---

### Post by SOULRiDER on 2007-12-22
I have the same problem with my mp3 player. By using cp it will copy them by name, so no need for anythign fancy, a
```
cp * destination
``` will suffice.

---

### Post by Ranguvar on 2007-12-22
> **SOULRiDER said:**
> I have the same problem with my mp3 player. By using cp it will copy them by name, so no need for anythign fancy, a
```
cp * destination
``` will suffice.
Thanks, it works great :D

An even nicer method would be a function to modify the creation date of all files in a folder so that the first alphabetically has the first creation date. Does there exist such a thing please?

Thanks again ^_^

---

### Post by nick_h on 2007-12-22
You could use the *touch* command to change access and modify times.  The problem is that Unix filesystems do not store create times.

---

### Post by nick_h on 2007-12-22
> **SOULRiDER said:**
> I have the same problem with my mp3 player. By using cp it will copy them by name, so no need for anythign fancy, a
```
cp * destination
``` will suffice.

Yes, both this and my earlier suggestion rely on bash pathname expansion which is alphabetical.  Obviously the simplest solution is the best. :)

---

### Post by Ranguvar on 2007-12-23
> **nick_h said:**
> You could use the *touch* command to change access and modify times.  The problem is that Unix filesystems do not store create times.I'm a little unsure what you mean... my portable device is FAT32?

---

### Post by zarqoon on 2007-12-24
I would presume he meant you should try to use touch "filename on your portable" in the right order and look if that changes anything. But he does not think it will because it will only change the access/modify time stamp and not the create stamp because it would not exist on a unix filesystem.

---

### Post by nick_h on 2007-12-24
Yes.  Most portable devices are probably FAT32.  Within linux all filesystems are accessed via a Virtual File System (VFS) that makes them look like a Unix filesystem.  Even though the FAT drive will support a create date, that will be populated when files are created, it will be difficult to access thorough linux.

The touch command would have been the one to use if create dates were supported.

I don't even know how to see the create time in Ubuntu.

---

### Post by burbankmarc on 2007-12-24
well...if you want to use touch, this worked for me

```
ls | sort -r | touch `xargs`
```

hope that helps

---

