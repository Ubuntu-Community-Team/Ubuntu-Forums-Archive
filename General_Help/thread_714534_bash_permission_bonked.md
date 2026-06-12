---
title: "bash permission bonked"
date: 2008-03-03
forum: General Help
---

### Post by caughran on 2008-03-03
Something is fouled with bash. There is apparently no permission great enough to run a script. The problem happens with other scripts, not just this one.

```
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ sudo ./flashplayer-installer
[sudo] password for jim:
sudo: unable to execute ./flashplayer-installer: Permission denied
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ ls -l
total 7968
-rwxrwxrwx 1 jim jim   21700 2007-11-20 18:24 flashplayer-installer
-rwxr-xr-x 1 jim jim 8119784 2007-11-20 18:24 libflashplayer.so

```

I discovered that /bin/sh pointed to dash, not to bash, so I changed that and rebooted, to no effect. I also tried reinstalling bash with synaptic.
```
jim@JIMJANET:~/Desktop$ cd /bin
jim@JIMJANET:/bin$ ls -l sh*
lrwxrwxrwx 1 root root 4 2008-03-03 15:51 sh -> bash
lrwxrwxrwx 1 root root 4 2007-05-27 16:15 sh.dash -> dash

```

and even
```
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ sudo -i
[sudo] password for jim:
root@JIMJANET:~# /home/jim/tempstuf/install_flash_player_9_linux/flashplayer-installer
-bash: /home/jim/tempstuf/install_flash_player_9_linux/flashplayer-installer: /bin/sh: bad interpreter: Permission denied

```

---

### Post by mikecrowe on 2008-03-04
Hey Jim,

FYI, I just had this problem (and I assume you've done the research about chmod +x stuff).  I had inadvertently mounted my partition with a noexec parameter.  After correcting in fstab, and a  
> sudo mount -o remount,rw /home 
all is well from me.

---

### Post by caughran on 2008-03-04
Not sure why /home wouldn't have execution privileges. The fstab entry is

```
/dev/sda11 /home ext3 defaults,user 0 2
```

which looks innocuous.

I'm still mystified.

---

### Post by taurus on 2008-03-04
Personally, I would remove the **user** from the entry for /dev/sda11.  

What's the output of this command from a terminal?

```
ls -la ~
```

---

### Post by caughran on 2008-03-04
I've abridged the output below.

```
jim@JIMJANET:~$ ls -la ~
total 3408
drwxr-xr-x 119 jim  jim     12288 2008-03-04 11:20 .
drwxr-xr-x   8 root root     4096 2008-01-27 14:07 ..
-rw-------   1 jim  jim       420 2008-02-16 11:18 2008-02-16-16-18-10.089-VirtualBox-7254.log
drwx------   3 jim  jim      4096 2007-12-14 16:32 .adobe
...
drwxrwxrwx   2 jim  jim      4096 2008-03-03 13:40 Desktop
...
drwxrwxrwx   3 jim  jim      4096 2008-03-03 15:44 tempstuf

```

---

