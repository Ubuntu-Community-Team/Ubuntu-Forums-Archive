---
title: "Installing .sh and .run"
date: 2006-11-08
forum: General Help
---

### Post by thecynicality on 2006-11-08
This is probably really easy but im new to linux and i don't know squat yet, anyways I downloaded 2 games, one is a .sh file and one is a .run file, how would i go about installing those?.

---

### Post by voodoonirvana on 2006-11-08
I think for the .sh you would just move it into your home directory and use

```
sudo ./program.sh
```

Of course instead of "program" use what the .sh is called.

---

### Post by kinematic on 2006-11-08
and with the .run file you make it executeable(right click on it,permissions,execute)then left click on it and select execute.

---

### Post by thecynicality on 2006-11-08
I tried both, for the .sh file it give me a command not found.

For the .run i right click on it but theres no permission option, im using kde maybe that makes a difference.

---

### Post by LenzM on 2006-11-08
are you sure you had the './' before the .sh file
```

user@computer:~$ ./prog.sh

```

NOT THIS:
```

user@computer:~$ prog.sh

```

---

### Post by thecynicality on 2006-11-08
Yes im sure im doing it with ./ i also tried it with and without the sudo. I don't know whats going on.

---

### Post by LenzM on 2006-11-08
```

chmod u+x prog.sh

```

---

### Post by thecynicality on 2006-11-08
Thank you that worked, do i always have to do the chmod thing? What exactly does that do?

---

### Post by po0f on 2006-11-08
thecynicality,

chmod **ch**anges the file **mod**e.  "u" stands for "user" ("g" stands for group, and "a" stands for all), the primary owner of the file (you), "+" means add permission for whatever follows, and "x" means execute permission.  It gave you permission to execute the file.

To look at the permissions on a file, execute the following from a terminal:
```
$ ls -l /path/to/file
```
Among the output will be a series of characters.  Something along the lines of:
```
-rwxr-x-r-- 1 user group 10 2006-11-08 12:12 file
```
The permissions on this file are the first set of characters, "-rw-r--r--".  Break it down into four sections of characters in the pattern 1-3-3-3.
[list]
[*]**-**: This will be a "d" if the target is a directory, an "l" if it is a symlink, a "-" if it is a regular file, etc.
[*]**rw-**: The first set of permissions are for the owner/"user" of the file.  This shows that you have "read" and "write" permission on the file.
[*]**r--**: The permissions for "group" are "r--", giving them just "read" permission.
[*]**r--**: Ditto for "all"
[/list]

I'm sure this was more information than what you were looking for, but hopefully you will have learned something from this.  :)

---

### Post by Ay Deverrick on 2006-11-08
I've always done it with

```
$ sh prog.sh
```

It works for me and I usually don't have to use chmod -ax.

---

