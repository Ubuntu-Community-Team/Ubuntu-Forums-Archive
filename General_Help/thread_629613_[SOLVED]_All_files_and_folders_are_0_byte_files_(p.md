---
title: "[SOLVED] All files and folders are 0 byte files (permissions problem)"
date: 2007-12-02
forum: General Help
---

### Post by nico@nc on 2007-12-02
Hello,

As I were not able to use ies4linux without sudo, I tryed this : ```
sudo nautilus /opt/ies4linux/
``` then I selected all the folders and files in this folder > Properties > Permissions, I did not modified the owner (root) and the permissions, but I clicked [Apply permissions to included files].

And just after, all the icons on the desktop and anywhere else changed to a red cross in a square, I were not able to start any program (permission not accorded), etc.

I restarted Ubuntu, GDM didn't start, prompt allowed me to login, but when I tried it, I got "impossible to cd to /home/nicolas"!

I used a live cd to see what I could see, and all the files and folders in my home (different partition that the filesystem) and in the filesystem were 0 byte unknwon type files !

But with a ```
gksudo nautilus
``` (still with live cd), everything is ok. I think then it is a permissions problem.

Sorry for my poor English, my mother tongue is French. You can find a message in French (with screenshots) here: [http://forum.ubuntu-fr.org/viewtopic.php?id=171344](http://forum.ubuntu-fr.org/viewtopic.php?id=171344)

Thank in advance for your help !

---

### Post by ruibernardo on 2007-12-02
Can you confirm who is the owner of your home directory from the LiveCD? 

Mount the disk partition by clicking on it in Places > Computer > the_disk_partition and then open a terminal and type:
```
ls -l /media/disk/home/
```It should be something like this (with nicholas instead of user):
```
drwxr-xr-x 10 **user user**    4096 2007-12-03 02:20 **user**
```

---

### Post by nico@nc on 2007-12-03
```
ubuntu@ubuntu:~$ ls -l /media/disk-1/
total 20
drwxr-xr-x  42 1001 1001 4096 2007-11-07 07:16 anne-sophie
drwxr-xr-x  19 1002 1001 4096 2007-07-09 09:55 invite
drwx------   2 root root 4096 2007-05-15 11:32 lost+found
drwxr--r-- 103 1000 1000 4096 2007-12-02 15:24 nicolas
drwxr-xr-x  38 1002 1002 4096 2007-11-30 07:57 sylvie

```

/home is on a separate partition. There is the problem (0 byte files excepted in sudo mode) only for my home (nicolas) (and for the whole file system on the other partition), no problem for other users' files.

---

### Post by nico@nc on 2007-12-03
If it can help you :
```
ubuntu@ubuntu:~$ ls -l /media/disk-2/
total 0
?--------- ? ? ? ?                ? /media/disk-2/bin
?--------- ? ? ? ?                ? /media/disk-2/boot
?--------- ? ? ? ?                ? /media/disk-2/cdrom
?--------- ? ? ? ?                ? /media/disk-2/dev
?--------- ? ? ? ?                ? /media/disk-2/etc
?--------- ? ? ? ?                ? /media/disk-2/home
?--------- ? ? ? ?                ? /media/disk-2/initrd
?--------- ? ? ? ?                ? /media/disk-2/initrd.img
?--------- ? ? ? ?                ? /media/disk-2/initrd.img.old
?--------- ? ? ? ?                ? /media/disk-2/lib
?--------- ? ? ? ?                ? /media/disk-2/lost+found
?--------- ? ? ? ?                ? /media/disk-2/media
?--------- ? ? ? ?                ? /media/disk-2/mnt
?--------- ? ? ? ?                ? /media/disk-2/opt
?--------- ? ? ? ?                ? /media/disk-2/proc
?--------- ? ? ? ?                ? /media/disk-2/root
?--------- ? ? ? ?                ? /media/disk-2/sbin
?--------- ? ? ? ?                ? /media/disk-2/srv
?--------- ? ? ? ?                ? /media/disk-2/sys
?--------- ? ? ? ?                ? /media/disk-2/tmp
?--------- ? ? ? ?                ? /media/disk-2/usr
?--------- ? ? ? ?                ? /media/disk-2/var
?--------- ? ? ? ?                ? /media/disk-2/vmlinuz
?--------- ? ? ? ?                ? /media/disk-2/vmlinuz.old
?--------- ? ? ? ?                ? /media/disk-2/windows
?--------- ? ? ? ?                ? /media/disk-2/windows2
```
```
ubuntu@ubuntu:~$ sudo ls -l /media/disk-2/
total 112
drwxr-xr-x   2 root root  4096 2007-10-18 19:54 bin
drwxr-xr-x   3 root root  4096 2007-10-18 20:21 boot
lrwxrwxrwx   1 root root    11 2007-07-11 21:55 cdrom -> media/cdrom
drwxr-xr-x   5 root root  4096 2007-10-18 20:13 dev
drwxr-xr-x 126 root root 12288 2007-12-02 15:58 etc
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 home
drwxr-xr-x   2 root root  4096 2007-04-15 11:48 initrd
lrwxrwxrwx   1 root root    29 2007-10-18 20:16 initrd.img -> boot/initrd.img-2.6.22-14-386
lrwxrwxrwx   1 root root    33 2007-10-18 20:16 initrd.img.old -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root 12288 2007-11-06 10:09 lib
drwxr-xr-x   2 root root 16384 2007-07-11 21:54 lost+found
drwxr-xr-x   5 root root  4096 2007-12-02 15:24 media
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 mnt
drwxr-xr-x  15 root root  4096 2007-11-30 17:13 opt
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 proc
drwxr-xr-x  32 root root  4096 2007-12-01 16:23 root
drwxr-xr-x   2 root root  4096 2007-11-14 14:00 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 11:48 srv
drwxr-xr-x   2 root root  4096 2007-04-04 10:47 sys
drwxr-xr-t   4 root root  4096 2007-12-02 15:56 tmp
drwxr-xr-x  13 root root  4096 2007-11-17 13:16 usr
drwxr-xr-x  15 root root  4096 2007-04-15 12:01 var
lrwxrwxrwx   1 root root    26 2007-10-18 20:16 vmlinuz -> boot/vmlinuz-2.6.22-14-386
lrwxrwxrwx   1 root root    30 2007-10-18 20:16 vmlinuz.old -> boot/vmlinuz-2.6.22-14-generic
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 windows
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 windows2
```

---

### Post by ruibernardo on 2007-12-03
```
drwxr--r-- 103 1000 1000 4096 2007-12-02 15:24 nicolas
```Your user group doesn't have execution rights on your home directory so he can't cd to the directory (no x). In the recovery mode type:
```
sudo chmod g+x /home/nicholas
```This will give execution rights to your group in that directory. 

Please confirm it works.

---

### Post by nico@nc on 2007-12-03
In recovery mode (and in "normal" mode), I can not do anything. When starting, I get this :
> * [...][RIGHT][OK][/RIGHT]
* Starting kernel log daemon...
start-stop-daemon: Unable to start /sbin/klogd: Permission denied (Permission denied)
[RIGHT][[COLOR="Red"]fail[/COLOR]][/RIGHT]
* [...][RIGHT][OK][/RIGHT]
* Starting Hardware abstraction layer hald [RIGHT]_[/RIGHT]
And nothing more!

With a Ctrl+Alt+F*, I try to login, I get this :
> Unable to cd to '/home/nicolas"
I noticed that there is the same problem for every user, although there is not the problem of 0 byte files when looking their home directory from the live cd.

So I couldn't do what you asked, I tried *sudo chmod g+x /media/disk-1/nicolas* from the LiveCD, but it does not change anything.

I think the problem is also with the filesystem (or files system, in English? > the /), as there is also "0 byte files" there.

Thanks again for your help.


**edit...** now :
```
ubuntu@ubuntu:~$ ls -l /media/disk-1/
total 20
drwxr-xr-x  42 1001 1001 4096 2007-11-07 07:16 anne-sophie
drwxr-xr-x  19 1002 1001 4096 2007-07-09 09:55 invite
drwx------   2 root root 4096 2007-05-15 11:32 lost+found
drwxr-xr-- 103 1000 1000 4096 2007-12-02 15:24 nicolas
drwxr-xr-x  38 1002 1002 4096 2007-11-30 07:57 sylvie
```

---

### Post by ruibernardo on 2007-12-03
it should have been: 

```
sudo chmod go+x /home/nicholas
```sorry. But i will not help about the filesytem.

can you do a "ls -l" of the root partition in the disk?

---

### Post by nico@nc on 2007-12-03
```
ubuntu@ubuntu:~$ ls -l /media/disk-2/root
total 15140
drwxr-xr-x 2 root root     4096 2007-11-14 20:19 Desktop
drwxr-xr-x 3 root root     4096 2007-11-30 17:12 InstallShield
-rw-r--r-- 1 root root 15474688 2007-10-20 23:07 nautilus-debug-log.txt
ubuntu@ubuntu:~$ ls -l /media/disk-2/
total 112
drwxr-xr-x   2 root root  4096 2007-10-18 19:54 bin
drwxr-xr-x   3 root root  4096 2007-10-18 20:21 boot
lrwxrwxrwx   1 root root    11 2007-07-11 21:55 cdrom -> media/cdrom
drwxr-xr-x   5 root root  4096 2007-10-18 20:13 dev
drwxr-xr-x 126 root root 12288 2007-12-03 16:53 etc
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 home
drwxr-xr-x   2 root root  4096 2007-04-15 11:48 initrd
lrwxrwxrwx   1 root root    29 2007-10-18 20:16 initrd.img -> boot/initrd.img-2.6.22-14-386
lrwxrwxrwx   1 root root    33 2007-10-18 20:16 initrd.img.old -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root 12288 2007-11-06 10:09 lib
drwxr-xr-x   2 root root 16384 2007-07-11 21:54 lost+found
drwxr-xr-x   4 root root  4096 2007-12-03 16:48 media
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 mnt
drwxr-xr-x  15 root root  4096 2007-11-30 17:13 opt
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 proc
drwxr-xr-x  32 root root  4096 2007-12-01 16:23 root
drwxr-xr-x   2 root root  4096 2007-11-14 14:00 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 11:48 srv
drwxr-xr-x   2 root root  4096 2007-04-04 10:47 sys
drwxr-xr-t   4 root root  4096 2007-12-03 16:53 tmp
drwxr-xr-x  13 root root  4096 2007-11-17 13:16 usr
drwxr-xr-x  15 root root  4096 2007-04-15 12:01 var
lrwxrwxrwx   1 root root    26 2007-10-18 20:16 vmlinuz -> boot/vmlinuz-2.6.22-14-386
lrwxrwxrwx   1 root root    30 2007-10-18 20:16 vmlinuz.old -> boot/vmlinuz-2.6.22-14-generic
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 windows
drwxr-xr-x   2 root root  4096 2007-07-11 21:55 windows2
```

I'm also trying to get help on the French forum : [http://forum.ubuntu-fr.org/viewtopic.php?id=171344](http://forum.ubuntu-fr.org/viewtopic.php?id=171344)

With a *sudo chmod 755 /media/disk-2* and *sudo chmod 755 /media/disk-1/home/nicolas* I can now access to the files from the liveCD without sudo, and I can go to the login screen, but after I get an error : "your sessions had not longed 10 seconds, ..." and the following error detail :
> (process:5610): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5614): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

---

### Post by ruibernardo on 2007-12-03
Can you verify if the files inside your home directory have read permissions?
```
ls -l /media/disk-1/nicholas
```

---

### Post by nico@nc on 2007-12-03
Seems that yes :
```
ubuntu@ubuntu:~$ ls -l /media/disk-1/nicolas
total 32976
drwxr-xr-x  9 1000 1000     4096 2007-11-25 08:04 Apps
drw-r--r--  4 1000 1000     4096 2007-12-01 19:27 Desktop
drwxr-xr-x  7 1000 1000     4096 2007-12-01 19:34 Documents
-rw-r--r--  1 1000 1000    10904 2007-11-12 18:47 image32.zip
drwxr-xr-x  6 1000 1000     4096 2007-10-28 20:05 Images
drwxr-xr-x 35 1000 1000     4096 2007-08-04 16:26 Musique
-rw-r--r--  1 1000 1000    36864 2007-11-28 08:06 nautilus-debug-log.txt
-rw-r--r--  1 1000 1000   256790 2007-11-14 18:28 out.ogg
-rw-r--r--  1 1000 1000 33370954 2007-11-14 18:37 out.ogg.1
drwx------  2 1000 1000     4096 2007-10-31 13:12 PDF
drwxr-xr-x  2 1000 1000     4096 2007-11-25 10:11 Public
drwxr-xr-x  6 1000 1000     4096 2007-10-29 09:31 Sites
drwxr-xr-x  5 1000 1000     4096 2007-11-04 13:52 Téléchargements
drwxr-xr-x  2 1000 1000     4096 2007-08-09 16:44 Templates
drwxr-xr-x  5 1000 1000     4096 2007-10-31 14:11 Vidéos
ubuntu@ubuntu:~$ 

```

There is maybe a problem with /tmp permissions, I try something suggested on the french forum.

---

### Post by ruibernardo on 2007-12-03
I find a bit strange that the files are not listed with the username as owner, but with the uid. But for now can you verify if the file .Xauthority is not owned by the nicholas user (could be owned by root, not allowing the user to overwrite it).

One more ls, please:
```
ls -la /media/disk-1/nicolas/.Xauth*
```

---

### Post by nico@nc on 2007-12-03
Finally resolved with :
[list][*]*sudo chmod 755 /media/disk-2* (disk-2 is the mount point for the filesystem)
[*]*sudo chmod 755 /media/disk-1/home/nicolas* (my home directory, as I have a separate partition for /home)
[*]*sudo chmod 777 /tmp*[/list]

Thanks a lot for your help epimeteo! :)

---

### Post by ruibernardo on 2007-12-03
Glad you got out of trouble nico@nc :)

---

