---
title: "premissions"
date: 2021-09-05
forum: General Help
---

### Post by natbrowne on 2021-09-05
Hi,
I have a new SSD set up on my server but when I ssh into it I cannot write anything due to premissions, without granting premissions for everything and anyone can someone help? My home directory - which I can write to has the following:
```
[FONT=monospace][COLOR=#54ff54]**patrick@daystrom**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ pwd [/COLOR]
/home/patrick 
[COLOR=#54ff54]**patrick@daystrom**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l [/COLOR]
total 4 
drw---S--- 2 patrick sambashare 4096 Jun 19 12:25 [COLOR=#5454ff]**sambashare**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#54ff54]**patrick@daystrom**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

and the directory I cannot write to, but want to be able to:
```
[FONT=monospace][COLOR=#54ff54]**patrick@daystrom**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/mnt/sda**[/COLOR][COLOR=#000000]$ pwd [/COLOR]
/mnt/sda 
[COLOR=#54ff54]**patrick@daystrom**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/mnt/sda**[/COLOR][COLOR=#000000]$ ls -l [/COLOR]
total 16 
drwx------ 2 root root 16384 Sep  4 22:05 [COLOR=#5454ff]**lost+found**[/COLOR]
[COLOR=#000000] [/COLOR]
[/FONT]
```

Im guessing chmod is the solution, but I don't know what to add.

---

### Post by yancek on 2021-09-05
> [FONT=monospace]drwx------ 2 root root 16384 Sep  4 22:05 [COLOR=#5454ff]**lost+found**[/COLOR][/FONT]

The owner/group are both root as shown above so you need to be root (use sudo) to write there or change ownership.  Your output only shows a device; /dev/sda rather than a partition /dev/sda1.  Generally, one would create a partition with a filesystem on it.  What filesystem do you have?   You can get info on chown command by typing in a terminal:  man chown
There are also countless tutorials on using the chown command online.

---

