---
title: "Can't change directory permissions even as root"
date: 2014-12-25
forum: General Help
---

### Post by totito on 2014-12-25
Hello fellas!!!!

So i have this little problem... even as root i cant seem to mange to change directories permissions

Let me show you:

First ls -l

 ```

drwx------ 1 toto toto      0 dic 16 21:39 VirtualBox_VMs
drwx------ 1 toto toto      0 jul 24 23:38 Windows 7 Lite x86 Español
root@kubuntu:/media/toto/DATOS# 


```

Then try to change permissions:

```

drwx------ 1 toto toto      0 dic 16 21:39 VirtualBox_VMs
drwx------ 1 toto toto      0 jul 24 23:38 Windows 7 Lite x86 Español
root@kubuntu:/media/toto/DATOS# chmod 707 VirtualBox_VMs/
root@kubuntu:/media/toto/DATOS# 

```

Then.... all remains the same:

```

drwx------ 1 toto toto      0 dic 16 21:39 VirtualBox_VMs
drwx------ 1 toto toto      0 jul 24 23:38 Windows 7 Lite x86 Español
root@kubuntu:/media/toto/DATOS# 

```

I first tried as regular user (which is user of the #User privilege specification inside sudoers, below root user) but nothing happened. The I tried as root like you saw before.


I cant even change permissions of the Hard Drive :(

```

root@kubuntu:/media/toto# ls -l
total 64
drwx------ 1 toto toto 65536 dic 22 17:52 DATOS
root@kubuntu:/media/toto# chmod 777 DATOS/
root@kubuntu:/media/toto# ls -l
total 64
drwx------ 1 toto toto 65536 dic 22 17:52 DATOS
root@kubuntu:/media/toto# 



```

I hope you guys could give me a hand... 


Thanks in advanced!!!!

---

### Post by Bashing-om on 2014-12-25
totito; Hello;

You have not said the file system in use.
You can not impose unix file permissions on a Windows file system. These Windows' Permissions are set in the mount.

see:
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251) <-HOWTO: Mount NTFS partitions with specific ownership/permissions

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by totito on 2014-12-26
Thx for your replay but both files I'm trying to change permissions are directories which are inside a NTFS partition ( DATOS/ )

```

drwx------ 1 toto toto      0 dic 16 21:39 VirtualBox_VMs
drwx------ 1 toto toto      0 jul 24 23:38 Windows 7 Lite x86 Español

```

It's ok if I cant change partition permissions (though it's weird) but Why cant I change directories inside permissions?

---

### Post by Bashing-om on 2014-12-26
totito; Welp;

> **totito said:**
> Thx for your replay but both files I'm trying to change permissions are directories in which are inside a NTFS partition ( DATOS/ )

```

drwx------ 1 toto toto      0 dic 16 21:39 VirtualBox_VMs
drwx------ 1 toto toto      0 jul 24 23:38 Windows 7 Lite x86 Español

```

It's ok if I cant change partition permissions (though it's weird) but Why cant I change directories inside permissions?

It is because the parent directory has jurisdiction ;
see:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)

Part of what makes *nix
[INDENT][INDENT][INDENT]so secure
[/INDENT][/INDENT][/INDENT]

---

### Post by Morbius1 on 2014-12-26
>                      Thx for your replay but both files I'm trying to change permissions  are directories which are inside a NTFS partition ( DATOS/ )
Because NTFS partition have no Linux permissions to change.

When Linux mounts an ntfs partition it creates a "view" of the partition that gives it the appearance that it has Linux permissions when in fact it does not. As a consequence of this "view" the permissions assigned at mount time ( or boot time if you mount it through fstab ) permeate throughout the partition and are immutable.

---

### Post by totito on 2014-12-26
Thx both of you guys I finally changed the file system options of the NTFS drive :D

```

toto@kubuntu:~$ sudo cat /etc/fstab
[sudo] password for toto: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=5ab4d17a-2399-4a0d-afe8-5796202e8072 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=cd74e560-9865-46b4-a185-7b941d76329b /boot           ext2    defaults        0       2
# /home was on /dev/sdb4 during installation
UUID=a51e8217-6aee-445b-acda-fc0c4b1a0f96 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=2b92cd84-7937-4ff3-a158-71d56367dc05 none            swap    sw              0       0
# /DATOS was on /media/toto/ during installation
UUID=AA2C0E122C0DDA69 /media/DATOS ntfs-3g defaults,auto,uid=1000,gid=1000,umask=007 0    0 
toto@kubuntu:~$ 

```

Now to let other user from "others" read and execute /DATOS partition I created a group called "movies". Do I need to add "movies" (gid n° 1002) next to the gid n° 1000 (belongs to user toto)?

The thing is that I have a special directory called MOVIES inside /DATOS i want everyone can access but only to that directory... not the rest of the other
Should I set it like this?

```

[FONT=Verdana]UUID=AA2C0E122C0DDA69 /media/DATOS ntfs-3g defaults,auto,uid=1000,gid=1000,**[SIZE=3]1002[/SIZE]**,umask=007 0    0 [/FONT]

```


Thx in advanced again!!!!


EDIT:


Ok I created another user called CINTIA and added her to "movies" group, then I set fstab just like this:

```

[FONT=Verdana]UUID=AA2C0E122C0DDA69 /media/DATOS ntfs-3g defaults,auto,uid=1000,gid=**[SIZE=3]1002[/SIZE]**,umask=007 0    0 [/FONT]

```

But she can access to all directories inside /DATOS not just to movies directory... And when I tried to change the rest of directories using chmod nothing happened at all just like the first time..

Any suggestions? 

:D

---

### Post by Morbius1 on 2014-12-26
You can't do what you want in NTFS for the reasons already given.

If you only want one specific subfolder to be accessible the only safe way is to set the mount like this so only you have read / write access:
> [FONT=Verdana]UUID=AA2C0E122C0DDA69 /media/DATOS ntfs-3g defaults,auto,uid=1000,gid=1000,umask=007 0    0 [/FONT]
Then use bindfs to remount the subdirectory with different permissions. To do so temporarily :
```
sudo bindfs -o perms=0777 /media/DATAOS/MOVIES /media/MOVIES
```
You would have to create the /media/MOVIES directory and also install bindfs:
```
sudo apt-get install bindfs
```
THe only issue however is that bindfs and ntfs-3g are using the same technology to do this so you are in affect creating a "view" of a "view" and I can't help but think there will be a performance issue. Wouldn't be a problem if it was just data but since these are media files it may be too much.

Try the bindfs technique and if it's acceptable have it done at boot time by placing the line without sudo above the "exit 0" line in /etc/rc.local like this:
```
bindfs -o perms=0777 /media/DATAOS/MOVIES /media/MOVIES
```
If it were me the best solution would be to place the files in an ext4 partition.

---

### Post by totito on 2014-12-26
Ok Morbius1 I'll be checking out the bindfs program later on!!!!

Thank you all guys for your help now I know a bit more about linux :D 

I just let the 1002 group in gid option and all users inside that group can access with r,w,x permissions. 

Problem solved!!!!

---

