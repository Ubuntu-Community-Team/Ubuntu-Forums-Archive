---
title: "No such file or dir with script"
date: 2017-12-21
forum: General Help
---

### Post by raleigh3 on 2017-12-21
All my scripts run fine, but I always get this.

```
/home/andy/bin/Date_Time.sh: line 1: &#65279;#!/bin/bash: No such file or directory
```

---

### Post by VMC on 2017-12-21
Do you get that message when yo open a terminal, or only when you run a bash script? Show example of one of your scripts.

---

### Post by litlesam on 2017-12-21
> **VMC said:**
> Show example of one of your scripts.

+1

What I noticed as well is this "/home/andy/[SIZE=4]bin[/SIZE]/" .

There is no /bin/ in the "/home/user/" directory.

---

### Post by raleigh3 on 2017-12-21
I found out it is because of BOM in the files.

[https://unix.stackexchange.com/questions/27054/bin-bash-no-such-file-or-directory](https://unix.stackexchange.com/questions/27054/bin-bash-no-such-file-or-directory)

Don't know how they got in my files as I used Geany and it does not insert BOMs.

Would like a script that can remove them for me as I have a lot of scripts.

This works for individual files.

```
tail -c +4 test.txt > t.txt
```

---

