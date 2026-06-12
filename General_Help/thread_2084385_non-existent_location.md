---
title: "non-existent location"
date: 2012-11-15
forum: General Help
---

### Post by miro71 on 2012-11-15
```
miroelo82@ubuntu:~$ cd /wine/dosdevices/c:/Program Files
bash: cd: /wine/dosdevices/c:/Program: No such file or directory
miroelo82@ubuntu:~$ cd .wine
miroelo82@ubuntu:~/.wine$ cd ..
miroelo82@ubuntu:~$ cd /.wine/dosdevices/c:/Program Files
bash: cd: /.wine/dosdevices/c:/Program: No such file or directory
miroelo82@ubuntu:~$ cd /.wine/dosdevices/c:/Program Files
bash: cd: /.wine/dosdevices/c:/Program: No such file or directory
miroelo82@ubuntu:~$ cd .wine
miroelo82@ubuntu:~/.wine$ cd dosdevices
miroelo82@ubuntu:~/.wine/dosdevices$ cd c:
miroelo82@ubuntu:~/.wine/dosdevices/c:$ cd Program Files
bash: cd: Program: No such file or directory
miroelo82@ubuntu:~/.wine/dosdevices/c:$ ls
Program Files  Program Files (x86)  users  windows
```
?

---

### Post by pkadeel on 2012-11-15
when there is a space in the file or folder name then use either one of the following two methods
```

cd /path/to/folder/with\ space

```
```

cd '/path/to/folder/with space'

```

---

### Post by oldfred on 2012-11-15
Capitals are also important.

fred@fred-Precise:~$ cd .wine
[EMAIL="fred@fred-Precise:~/.wine"]fred@fred-Precise:~/.wine[/EMAIL]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
[EMAIL="fred@fred-Precise:~/.wine"]fred@fred-Precise:~/.wine[/EMAIL]$ cd drive_c
[EMAIL="fred@fred-Precise:~/.wine"]fred@fred-Precise:~/.wine[/EMAIL]/drive_c$ ls
Program Files  Program Files (x86)  users  windows
[EMAIL="fred@fred-Precise:~/.wine"]fred@fred-Precise:~/.wine[/EMAIL]/drive_c$
[email]fred@fred-Precise:~/.wine[/email]/drive_c$ cd "Program Files"
[email]fred@fred-Precise:~/.wine[/email]/drive_c/Program Files$

---

