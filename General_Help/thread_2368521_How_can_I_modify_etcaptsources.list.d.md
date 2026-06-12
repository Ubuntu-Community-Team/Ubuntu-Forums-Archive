---
title: "How can I modify /etc/apt/sources.list.d/ ??"
date: 2017-08-11
forum: General Help
---

### Post by elstongunnn on 2017-08-11
I want to remove a line from /etc/apt/sources.list.d/ because I wrote it bad and every time I wrote something it shows me an error. How can I do that? I know how to modificate /etc/apt/sources.list but I don't know how to modificate /etc/apt/sources.list.d/

---

### Post by QIII on 2017-08-11
Can you paste the error?

sources.list.d is a directory, not a text file.

---

### Post by elstongunnn on 2017-08-11
N: Ignoring file 'sp' in directory '/etc/apt/sources.list.d/' as it has no filename extension


because when I do ls -la /etc/apt/sources.list.d/

 the list has a line that says: -rw-r--r-- 1 root root   50 ago 11 19:18 sp

I want to remove that line

---

### Post by oldos2er on 2017-08-11
```
sudo rm /etc/apt/sources.list.d/sp

sudo apt update
```

---

### Post by elstongunnn on 2017-08-11
Thankssssssssssss

---

### Post by vocx on 2017-08-12
> **elstongunnn said:**
> N: Ignoring file 'sp' in directory '/etc/apt/sources.list.d/' as it has no filename extension
because when I do ls -la /etc/apt/sources.list.d/

 the list has a line that says: -rw-r--r-- 1 root root   50 ago 11 19:18 sp

I want to remove that line
The error is telling you that there is a file called "sp" which is inside the "/etc/apt/sources.list.d/" directory. So the solution is to remove the file given with its full path.

You do not edit a file, you simply remove it. The command "ls -la" shows you the contents of a directory, not the contents of the file.
```

/etc/apt/sources.list.d/sp
^          ^         ^ | ^
this part is           | this is the
the directory          | file


a "directory" is another name for "folder"

```


> **oldos2er said:**
> ```
sudo rm /etc/apt/sources.list.d/sp

sudo apt update
```

---

### Post by deadflowr on 2017-08-12
For what it's worth:
The message is inconsequential to the running of apt.
All it is is a notice that apt will ignore the file as it uses the wrong extension or, in the case, no extension.
Not an error.

All the file needs is the proper .list extension
so instead of it reading as
```
/etc/apt/sources.list.d/sp
```
it reads
```
/etc/apt/sources.list.d/sp.list
```
easy to fix by simply moving the file
```
sudo mv /etc/apt/sources.list.d/sp /etc/apt/sources.list.d/sp.list
```

All that though leads to what made you decide to create the file in the first place?
And what is the content of the file?

---

### Post by Habitual on 2017-08-12
shortcut:```
sudo apt sources
```

---

