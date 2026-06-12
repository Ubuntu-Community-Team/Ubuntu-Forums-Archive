---
title: "sudo ls -l yields question marks"
date: 2007-07-11
forum: General Help
---

### Post by rolfen on 2007-07-11
Check out this bash output:
```

rolf@ubuntu:/media$ ls -l|grep network
drwxr-xr-x 3 rolf rolf 4096 2007-07-11 18:30 network
rolf@ubuntu:/media$ sudo ls -l|grep network
?--------- ? ?    ?       ?                ? network

```
The network directory is where i mounted the windows network through FUSE... (using the fusesmb command).
Anyway... any ideas why this is happening?

If this is a bug, can you direct me to the proper bug report page? thanks

---

### Post by rolfen on 2007-07-12
Bump... :D

---

### Post by dannyboy79 on 2007-07-12
this means that there is nothing mounted to the folder network. it doesn't show anything until you cd to it I thought?

---

### Post by rolfen on 2007-07-12
> **dannyboy79 said:**
> this means that there is nothing mounted to the folder network. it doesn't show anything until you cd to it I thought?
I can CD to it as rolf (normal user) and I can browse the contents of the mounted windows network... but I cannot CD to it as root.
But these question marks are really weird... why would it output question marks like this...

---

### Post by dannyboy79 on 2007-07-12
are you aware how FUSE works? I just explained why you have question marks, nothing is there until you actually cd to the directory or you go to it thru a file manager/browser.

 What are the permissions of the folder? If root can't cd to it that leads me to believe that you have it only executable by the owner not everyone. Make it readable, writable, executable by owner, and readable and executable by everyone else.

---

### Post by rolfen on 2007-07-12
> **dannyboy79 said:**
> What are the permissions of the folder? If root can't cd to it that leads me to believe that you have it only executable by the owner not everyone. Make it readable, writable, executable by owner, and readable and executable by everyone else.
It's not a folder permissions issue, you should be able to read folder permissions even if you dont have any access to the folder. for example:
```

rolf@ubuntu:~$ rmdir test
rolf@ubuntu:~$ mkdir test
rolf@ubuntu:~$ chmod 000 test
rolf@ubuntu:~$ ls -l|grep test
d--------- 2 rolf rolf 4096 2007-07-12 22:07 test
rolf@ubuntu:~$ sudo ls -l|grep test
Password:
d--------- 2 rolf rolf 4096 2007-07-12 22:07 test
rolf@ubuntu:~$ 

```
And by the way, the permissions of the folder are there for everyone to see in my first post: drwxr-xr-x . But you dont seem to have read that before answering.

---

### Post by cuhlik on 2008-02-01
I've got a similar problem.
When I list a directory, everything is normal, but my wife sees these question marks

> 
[FONT="Courier New"]
cuhlik@bigscreen:~$ ls -ld /home/photos/2008/01/19/PRG003/
drwxrw-rw- 2 cuhlik users 4096 2008-01-19 17:09 /home/photos/2008/01/19/PRG003/
cuhlik@bigscreen:~$ ls -l /home/photos/2008/01/19/PRG003/
total 173896
-rwxrw-rw- 1 cuhlik users 88690688 2008-01-19 17:09 MOV001.MOD
-rwxrw-rw- 1 cuhlik users     1280 2008-01-19 17:09 MOV001.MOI
-rwxrw-rw- 1 cuhlik users 89178112 2008-01-19 17:09 MOV002.MOD
-rwxrw-rw- 1 cuhlik users     1289 2008-01-19 17:09 MOV002.MOI
-rwxrw-rw- 1 cuhlik users       48 2008-01-19 17:09 PRG003.PGI
cuhlik@bigscreen:~$ su kathi
Password: 
kathi@bigscreen:/home/cuhlik$ ls -l /home/photos/2008/01/19/PRG003/
total 0
?--------- ? ? ? ?                ? /home/photos/2008/01/19/PRG003/MOV001.MOD
?--------- ? ? ? ?                ? /home/photos/2008/01/19/PRG003/MOV001.MOI
?--------- ? ? ? ?                ? /home/photos/2008/01/19/PRG003/MOV002.MOD
?--------- ? ? ? ?                ? /home/photos/2008/01/19/PRG003/MOV002.MOI
?--------- ? ? ? ?                ? /home/photos/2008/01/19/PRG003/PRG003.PGI
kathi@bigscreen:/home/cuhlik$ grep users /etc/group
users:x:100:cuhlik,root,kathi
kathi@bigscreen:/home/cuhlik$ df | grep home
/dev/sda3            276352884 141443840 120871048  54% /home
kathi@bigscreen:/home/cuhlik$ [/FONT]


Not this is not a network file system, just an ext3 partition on /dev/sda3

Any help interpreting these question marks would be greatly appreciated.

Thanks,

Chris

---

### Post by dannyboy79 on 2008-02-04
> **cuhlik said:**
> I've got a similar problem.
When I list a directory, everything is normal, but my wife sees these question marks




Not this is not a network file system, just an ext3 partition on /dev/sda3

Any help interpreting these question marks would be greatly appreciated.

Thanks,

Chris

is kathi a member of the users group?

---

### Post by aureus on 2008-03-06
Bit of an old post, but I ran into this problem myself today, so I thought I might as well post the solution to cuhlik's problem.

With directories, file permissions (specifically the execute bit) are implemented differently than files.  Since you can't execute a directory, the execute bit controls whether access (such as being able to cd into or ls the contents) is granted or not.

So basically your solution is to run:
chmod ug+x <directory>

---

### Post by mdeen on 2008-05-26
> **aureus said:**
> 
So basically your solution is to run:
chmod ug+x <directory>
Again, old post, but I have the same problem now. chmodding is of no use because the directory is executable:

[FONT="Courier New"][maarten@chef:/home]$ ls -l
total 24
drwxr-xr-x 21 httpd   users  4096 2008-05-21 19:57 htdocs/
drwx------  2 root    root  16384 2008-05-20 23:16 lost+found/
drwxrwxr-x 48 maarten users  4096 2008-05-23 23:38 maarten/
[maarten@chef:/home]$ ls -l htdocs
total 132
-rw-r--r-- 1 httpd users 2205 2007-11-30 09:17 apache_pb22_ani.gif
-rw-r--r-- 1 httpd users 1502 2007-11-30 09:17 apache_pb22.png
-rw-r--r-- 1 httpd users 2160 2004-11-21 06:35 apache_pb2_ani.gif
-rw-r--r-- 1 httpd users 2414 2004-11-21 06:35 apache_pb2.gif
-rw-r--r-- 1 httpd users 1463 2004-11-21 06:35 apache_pb2.png
-rw-r--r-- 1 httpd users 1385 2004-11-21 06:35 apache_pb.png
lrwxrwxrwx 1 httpd users    5 2008-05-21 19:54 EBT -> ./ebt
?--------- ? ?     ?        ?                ? htdocs/absil
?--------- ? ?     ?        ?                ? htdocs/apache_pb22.gif
?--------- ? ?     ?        ?                ? htdocs/apache_pb.gif
?--------- ? ?     ?        ?                ? htdocs/ebt
?--------- ? ?     ?        ?                ? htdocs/favicon.ico[/FONT]

Same problem occurs in /:
[FONT="Courier New"][maarten@chef:/home]$ ls -l /
total 76
drwxr-xr-x   2 root root  4096 2008-05-23 18:43 bin/
drwxr-xr-x   3 root root  4096 2008-05-23 23:37 boot/
lrwxrwxrwx   1 root root    11 2008-05-23 17:04 cdrom -> media/cdrom/
drwxr-xr-x  13 root root 13840 2008-05-26 10:27 dev/
drwxr-xr-x 116 root root 12288 2008-05-26 10:29 etc/
drwxr-xr-x   5 root root  4096 2007-10-08 12:47 home/
?---------   ? ?    ?        ?                ? /initrd
lrwxrwxrwx   1 root root    33 2008-05-23 17:21 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root 12288 2008-05-23 18:43 lib/
drwx------   2 root root 16384 2008-05-23 17:04 lost+found/
drwxr-xr-x   3 root root  4096 2007-10-16 01:17 media/
?---------   ? ?    ?        ?                ? /mnt
?---------   ? ?    ?        ?                ? /opt
dr-xr-xr-x 101 root root     0 2008-05-26 10:24 proc/
drwxr-xr-x   8 root root  4096 2008-05-26 10:05 root/
drwxr-xr-x   2 root root  4096 2008-05-23 18:53 sbin/
?---------   ? ?    ?        ?                ? /srv
drwxr-xr-x  12 root root     0 2008-05-26 10:24 sys/
drwxrwxrwt   4 root root  4096 2008-05-26 10:30 tmp/
drwxr-xr-x  11 root root  4096 2007-10-16 01:19 usr/
drwxr-xr-x  16 root root  4096 2008-05-23 18:18 var/
lrwxrwxrwx   1 root root    30 2008-05-23 17:21 vmlinuz -> boot/vmlinuz-2.6.22-14-generic[/FONT]

more(1) is not affected, but using it leads to:
[FONT="Courier New"][maarten@chef:/home]$ more /etc/passwd
-bash: /bin/more: Input/output error
[maarten@chef:/home]$[/FONT]

This problem turned up after a reboot when I put usbcore.autosuspend=1 in the grub config. Don't know if it is related, but I can't access /boot/grub at the moment:
[FONT="Courier New"]
[maarten@chef:/]$ ls /boot/grub
ls: reading directory /boot/grub: Input/output error
[maarten@chef:/]$[/FONT]

su also does not work.

---

### Post by my_ilium on 2008-06-09
aureus, thanks. Sorry it didn't work out for mdeen though.

---

