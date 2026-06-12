---
title: "Problem with accessing NAS share"
date: 2020-07-21
forum: General Help
---

### Post by peter-morawetz on 2020-07-21
Hi all, first post here, so greetings to the community first :-)


Second, here's my problem. I am using Ubuntu 20.04 and a Synology NAS for storing all my files. I included the NAS shares via the fstab:

```
//ip-address/homes   /home/peter/NAS_Dateien cifs username=my-user,password=my-password,rw,vers=1.0 0 0
//ip-address/photo   /home/peter/NAS_Fotos cifs username=my-user,password=my-password,rw,vers=1.0 0 0
//ip-address/video   /home/peter/NAS_Videos cifs username=my-user,password=my-password,rw,vers=1.0 0 0
//ip-address/music   /home/peter/NAS_Musik cifs username=my-user,password=my-password,rw,vers=1.0 0 0

```

In addition, I added the follwoing to the /etc/rc.local. This is because the NAS is not ready early enough during the boot session, so the NAS-shares would not mount. The rc.local solves this problem:

```
sleep 20


mount -o username=my-user,password=my-password,rw,vers=1.0 //ip-address/homes /home/peter/NAS_Dateien/
mount -o username=my-user,password=my-password,rw,vers=1.0 //ip-address/homes /home/peter/NAS_Fotos/
mount -o username=my-user,password=my-password,rw,vers=1.0 //ip-address/homes /home/peter/NAS_Videos/
mount -o username=my-user,password=my-password,rw,vers=1.0 //ip-address/homes /home/peter/NAS_Musik/

```


This all worked out fine with the previous 18.04 version of Ubuntu. However, with 20.04, I things behave strange:


[LIST]
[*]I can access the NAS shares from the file explorer and libre office
[*]however, I cannot access this shares from other programs like GIMP, Inkscape, Digikam
[/LIST]

What strikes me odd are the rights of the shares:

```
peter@Quax:~$ ls -l
drwxrwxrwx  7 root   root       0 Jul 19 09:46 NAS_Dateien
drwxrwxrwx 38 138862 138862     0 Jul 18 09:57 NAS_Fotos
drwxrwxrwx  6 root   root       0 Feb 26  2017 NAS_Musik
drwxrwxrwx 10 root   root       0 Jul 12 09:38 NAS_Videos

```
How comes this one share has a different owner and group? Where soes this come from? And who the hell is the user with the UID 138862?


ANy help is much appreciated!

Thanks

---

### Post by TheFu on 2020-07-21
a) if the NAS supports NFS, that would be better to use from all Unix-like OS clients.  It provides native support for owners, permissions, and excellent speed.  The mounts are system-to-system, not userid-to-system.   NFS sorta "just works." at this point.

b) Samba defaults have changed for recent Linux releases and Windows10 to drastically improve security.  Unpatched, old, implementations like a typical NAS would have use CIFS defaults that aren't compatible.  The first step is to determine the version of the CIFS protocol supported by the NAS.
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480) has more about that.

But if you switch to NFS, things sorta "just work", assuming you understand normal Unix directory and file permissions.

FWIW, rc.local is deprecated for a few years on all systemd managed Linux systems. That includes Ubuntu.

---

### Post by peter-morawetz on 2020-07-22
Thanks. I already managed to manually mount the share using nfs:

```
peter@Quax:~$ df
192.168.x.xxx:/volume1/homes 956675840 355184000 601389440   38% /home/peter/NAS_Dateien

```

However I cannot access it because of insufficient rights:

```

[COLOR=#000000]peter@Quax:~$ ls -l[/COLOR]
[COLOR=#000000]drwx--x--x 7 root root 4096 Jul 19 09:46 NAS_Dateien[/COLOR]
[COLOR=#000000]drwxrwxrwx 38 138862 138862 0 Jul 18 09:57 NAS_Fotos[/COLOR]
[COLOR=#000000]drwxrwxrwx 6 root root 0 Feb 26 2017 NAS_Musik[/COLOR]
[COLOR=#000000]drwxrwxrwx 10 root root 0 Jul 12 09:38 NAS_Videos[/COLOR]

```


I tried to solve that by adding an entry in the fstab:

```
192.168.x.xxx:/volume1/homes /home/peter/NAS_Dateien nfs rw,users 0 0
```

but to no success so far.

---

### Post by TheFu on 2020-07-22
NFS uses normal Unix permissions. While you may be able to use mount options in the fstab, I've never done in almost 30 yrs. 

Learn Unix permissions. Use those.  There are many tutorials, easily found.  Take 30 minutes to work through the tutorial, then another 45 minutes with a few terminals and different accounts working in some temporary directories playing with chown, chgrp and chmod. Use every possible combination and you'll have a "light bulb" moment of understand.  10 more minutes to "get it" fully and the problem above is easy to solve in the way you'd want.

These permissions are the core of all Unix system security, so this knowledge applies for every popular OS in the world, except one which we don't discuss here. ;)

BTW, the use of 777 permissions as shown above is terrible for security. Seeing that means someone 
[LIST=1]
[*] doesn't understand Unix security
[*] is lazy and doesn't care at all about security on the system
[/LIST]

BTW, I wouldn't mount storage under any single userid's HOME, mainly because it will likely cause problems with backups.  But it is your system.

Now that you've been appropriately chastised, the solution for this one mount has a few steps, assuming you want to ignore my advice:
fstab:
```
192.168.x.xxx:/volume1/homes /home/peter/NAS_Dateien nfs rw  0 2
```

Then run some commands:
```
sudo systemctl daemon-reload  # to get the fstab changes noticed
sudo mount -o remount /home/peter/NAS_Dateien  # to get the mount changed

# and for the owner, group, permissions .... 
sudo chown -R peter /home/peter/NAS_Dateien
chgrp -R peter  /home/peter/NAS_Dateien
find /home/peter/NAS_Dateien -type f -exec chmod -R 660 {} \;
find /home/peter/NAS_Dateien -type d -exec chmod -R 750 {} \;

```
 Those permissions are for data, not programs. It is possible this will break some other stuff. Without knowing the contents, impossible to say, but your 'peter' userid will have access and because you are the owner, you can correct those issues.  Of course, that will require understanding Unix file and directory permissions which I cannot magically impart to your brain.

If the *sudo chown* command above doesn't work - permission denied - then the changes will need to be made "on the NAS."  Typically, NAS-specific hardware allows root to do this. For NFS shares between normal Unix systems, remote root does not have any privileges. It is a security thing.

The order of those commands is important.

---

