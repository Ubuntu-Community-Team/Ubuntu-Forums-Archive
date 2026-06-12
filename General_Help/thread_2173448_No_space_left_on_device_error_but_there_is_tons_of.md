---
title: "No space left on device error but there is tons of space"
date: 2013-09-09
forum: General Help
---

### Post by orrgal on 2013-09-09
[COLOR=#000000][FONT=Arial]I am getting the "No space left on device" error for pretty much anything i try to do. Even using tab to autocomplete a command!
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]but when i do df -h i get:[/FONT][/COLOR]

ubuntu@ip-10-0-2-108:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       99G  6.5G   88G   7% /
udev            3.7G  8.0K  3.7G   1% /dev
tmpfs           1.5G  184K  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G     0  3.7G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/xvdb       414G  199M  393G   1% /mnt
overflow        1.0M  1.0M     0 100% /tmp
[COLOR=#000000][FONT=Arial]
which to me looks like there is tons of space. df -i also looks similar:[/FONT][/COLOR]

ubuntu@ip-10-0-2-108:~$ df -i
Filesystem       Inodes IUsed    IFree IUse% Mounted on
/dev/xvda1      6553600 94227  6459373    2% /
udev             951353   393   950960    1% /dev
tmpfs            953649   274   953375    1% /run
none             953649     3   953646    1% /run/lock
none             953649     1   953648    1% /run/shm
none             953649     1   953648    1% /run/user
/dev/xvdb      27525120    11 27525109    1% /mnt
overflow         953649    12   953637    1% /tmp
[COLOR=#000000][FONT=Arial]
I am on an Amazon EC2 ubuntu 12.04 instance.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Here are some examples of the error popping up:[/FONT][/COLOR]

ubuntu@ip-10-0-2-108:~$ sudo crontab -e
/tmp/crontab.RvYjrR/crontab: No space left on device

ubuntu@ip-10-0-2-108:~$ ls /va (hit tab for autocomplete)

-bash: cannot create temp file for here-document: No space left on device
-bash: cannot create temp file for here-document: No space left on device
[COLOR=#000000][FONT=Arial]
however the server seems to be running and everything seems to be working. what on earth is going on??

[/FONT][/COLOR]

---

### Post by linuxonbute on 2013-09-09
In your list it says /tmp is full.
and it is telling you it cannot create a temp file
So maybe you need to look at that first.

---

### Post by CatKiller on 2013-09-09
Given that there's only 1 MB, that's not going to be difficult to fill up.

---

### Post by orrgal on 2013-09-10
yeah i dont know what /tmp is but its called overflow and is only 1M... what can i do with it and is it really the problem?

---

### Post by linuxonbute on 2013-09-10
Please post the output of this:
```

sudo fdisk -l /dev/sda

```

---

### Post by varunendra on 2013-09-10
Welcome to the forums orrgal ! :)

Please use 'Code' tags to post commands and their outputs. It preserves the formatting making it look tidy and easy to read.

Please follow the "Using Code tags" link in my signature to see how. You can then edit your original post to do that now. :)

---

