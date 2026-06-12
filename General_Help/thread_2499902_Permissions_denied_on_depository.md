---
title: "Permissions denied on depository"
date: 2024-08-14
forum: General Help
---

### Post by kaam2811 on 2024-08-14
Hey there,
          
                                        I am using Xubuntu xfce. I am the only user of the pc and the also the one who setup Xubuntu.
 I am trying to Startup Disk Creator. After installing it without issue, when I try to open it I get the following message:
 An unhandled exception occured:

[Errno 13] Permission denied: /home/myname/Desktop/

 This kind of error is recurring. As an example I tried to go to the  desktop properties to change permissions but this is not allowed  neither. I still get the following message:
 
Error opening directory '/home/myname/Desktop/.
Permission denied

 I tried the chown command to change the owner of a file.
 ```
sudo chown myname /home/myname/Deskto
```p
 As I still have no rights on the directory, I tried:
 ```
$ chown [-R] myname /home/myname/Desktop


``` But I get:
 ```
zsh: no matches found: [-R]

``` Me being the only user, I don't understand why I can't own my own  data. And I don't understand why the chown command doesn't work.So I  tried to have a look who is officially the UID and GID of files and  directories with

 ```
-ls -n

``` And I don't see anything wrong here, there is only my name popping up in the results.
 Does anyone have an idea what the access of some specific files/folders are not allowed?

---

### Post by currentshaft on 2024-08-14
b

---

### Post by kaam2811 on 2024-08-14
Hey! 

Thanks for your quick reply. Then I get:

chown: cannot read directory '/home/amelie-melo/Desktop': Permission denied

---

### Post by currentshaft on 2024-08-14
s1

---

### Post by #&amp;thj^% on 2024-08-14
> **kaam2811 said:**
> Hey! 

Thanks for your quick reply. Then I get:

chown: cannot read directory '/home/amelie-melo/Desktop': Permission denied

Sounds like you used sudo with a GUI, please try this:
```
find . -type d -exec chmod 755 {} \;
```
Then show us these:
```
stat /home/$USER
### And
la -al


```

---

### Post by kaam2811 on 2024-08-15
Hi,

I tried as well with sudo this way:

$ sudo chown -R amelie-melo /home/amelie-melo/Desktop

and this way because I was not sure of the synthax:

sudo $ chown -R amelie-melo /home/amelie-melo/Desktop

In both way, I got as a result: zsh: command not found: $

So I tried without $, but then I get nothing in return and I still can't access the directory.

I  tried as well to access the root access by changing the password, but  same, nothing happens. So now, I am checking who are the users on this  laptop (should be only me) and how to change this

---

### Post by kaam2811 on 2024-08-15
....

---

### Post by kaam2811 on 2024-08-15
When I enter **find . -type d -exec chmod 755 {} \;**
I get a long list of "operation not permitted"


When I enter [B]stat /home/$USER

[/B]  File: /home/myname
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 802h/2050d    Inode: 23199746    Links: 32
Access: (0755/drwxr-xr-x)  Uid: ( 1000/myname)   Gid: ( 1000/myname)
Access: 2024-08-15 14:58:56.042081511 +0200
Modify: 2024-08-15 15:01:19.115315384 +0200
Change: 2024-08-15 15:01:19.115315384 +0200
 Birth: -
When I enter[B] la -al

[/B]total 2.1G
drwxr-xr-x  20 root root 4.0K Apr 26  2020 ./
drwxr-xr-x  20 root root 4.0K Apr 26  2020 ../
lrwxrwxrwx   1 root root    7 Apr 26  2020 bin -> usr/bin/
drwxr-xr-x   4 root root 4.0K Aug 14 08:54 boot/
drwxr-xr-x   2 root root 4.0K Apr 26  2020 cdrom/
drwxr-xr-x  19 root root 5.0K Aug 15 14:12 dev/
drwxr-xr-x 144 root root  12K Aug 15 14:19 etc/
drwxr-xr-x   3 root root 4.0K Apr 26  2020 home/
lrwxrwxrwx   1 root root    7 Apr 26  2020 lib -> usr/lib/
lrwxrwxrwx   1 root root    9 Apr 26  2020 lib32 -> usr/lib32/
lrwxrwxrwx   1 root root    9 Apr 26  2020 lib64 -> usr/lib64/
lrwxrwxrwx   1 root root   10 Apr 26  2020 libx32 -> usr/libx32/
drwx------   2 root root  16K Apr 26  2020 lost+found/
drwxr-xr-x   3 root root 4.0K Apr 28  2020 media/
drwxr-xr-x   2 root root 4.0K Apr 23  2020 mnt/
drwxr-xr-x   7 root root 4.0K Dec  1  2022 opt/
dr-xr-xr-x 328 root root    0 Aug 15 12:23 proc/
drwx------   8 root root 4.0K Aug 13 18:05 root/
drwxr-xr-x  34 root root 1.1K Aug 15 14:55 run/
lrwxrwxrwx   1 root root    8 Apr 26  2020 sbin -> usr/sbin/
drwxr-xr-x  27 root root 4.0K Aug 13 17:03 snap/
drwxr-xr-x   2 root root 4.0K Apr 23  2020 srv/
-rw-------   1 root root 2.0G May  6  2023 swapfile
dr-xr-xr-x  13 root root    0 Aug 15 12:23 sys/
drwxrwxrwt  19 root root 4.0K Aug 15 14:55 tmp/
drwxr-xr-x  14 root root 4.0K Apr 23  2020 usr/
drwxr-xr-x  14 root root 4.0K Apr 23  2020 var/

---

### Post by kaam2811 on 2024-08-16
hey there,

As it seems that root owns everything, all my computer  and all my life (me not being dramatic at all :'D), I would like the  situation to end

Is there a way to know when the change was made  (for sure, I initially had a normal setup)? It would help me analyse my  situation.

And if I reboot everything, would I lose everything?  All data? I mean of course, I can save the data externally that I want  and boot afterwards. But that wouldn't be my favourite option, I would  prefer to fix the computer and keep as much as it is.

---

### Post by ActionParsnip on 2024-08-16
You don't prefix the command with the dollar sign. That just signifies "ran as user"
```

sudo chown -R amelie-melo:amelie-melo /home/amelie-melo/Desktop

```
Will do it for you

---

