---
title: "Back up directory question"
date: 2018-06-27
forum: General Help
---

### Post by zuto2 on 2018-06-27
Hi,

I used the following command for and long time to back up. (works for me)

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

I want to exclude my desktop. Would it be the following? ```
--exclude=/desktop
```

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/desktop --exclude=/mnt --exclude=/sys /
```

For more information.
Source: [https://ubuntuforums.org/showthread.php?t=35087](https://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Xian on 2018-06-27
> **zuto2 said:**
> 
I want to exclude my desktop. Would it be the following? ```
--exclude=/desktop
```


I've not used this particular method, but wouldn't it be the full path:

```
--exclude=/home/<username>/Desktop
```

---

### Post by zuto2 on 2018-06-28
That is where I am confused. The following file is in the home directory and I do not need to specify the directory.

```
--exclude=/backup.tgz
```

---

### Post by Xian on 2018-06-28
Can you post the output of these commands:

$ ls / 

and 

$ ls /home

and

$ ls /home/<username>

---

### Post by zuto2 on 2018-06-28
okay,

I test it. The following works.

```
--exclude=/home/Z[FONT=Ubuntu Mono][COLOR=#000000]uto[/COLOR][/FONT]/Desktop
```

Now this leads to another problem. Why is the [COLOR=#000000][FONT=&amp]backup.tgz not the same way? It seems to be archived in the terminal at a slow speed, but it does not exist when restoring the back up.[/FONT][/COLOR]

```
--exclude=/backup.tgz
```

Should not it be the following?

```
--exclude=/home/Z[FONT=Ubuntu Mono][COLOR=#000000]uto[/COLOR][/FONT]/backup.tgz
```

---

### Post by zuto2 on 2018-06-28
Ah, the following command was used in the post: ```
cd /
```
[https://ubuntuforums.org/showthread.php?t=35087](https://ubuntuforums.org/showthread.php?t=35087)

Now I understand why they used:
```
--exclude=/backup.tgz
```

Although, why would one want the back up to go in the File System? Deleting it there is dangerous.
```
sudo rm -r -f <directory>
```

I had success restoring everything without: ```
cd /
``` (backup.tgz just ends up in the home folder)

```
sudo su

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/home/cortana/backup.tgz --exclude=/home/cortana/Desktop --exclude=/mnt --exclude=/sys /
```

Oh well, thank you everyone that tried to assist. I managed to figure it out with you all with trial and error. Thanks @Xian.

---

