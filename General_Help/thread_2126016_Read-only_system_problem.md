---
title: "Read-only system problem"
date: 2013-03-15
forum: General Help
---

### Post by guidod93 on 2013-03-15
[COLOR=#333333][FONT=Ubuntu Beta][COLOR=#000000][FONT=Verdana]i really don't have any idea of how to manage Ubuntu with the console. I am new in all this stuff, and i don't speak English a lot. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]My system crashed, and it doesn't let me do anything. It stays in read-only file system and i can't download or eliminate files. I tried some solutions i read, but i they didn't solve my problem! [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I did this: writing in the console "sudo fsck" (i don't know what that means) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]and the console: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]guido@Damonte:~$ sudo fsck [sudo] password for guido: sudo: no es posible abrir /var/lib/sudo/guido/0: Sistema de archivos de solo lectura fsck de util-linux 2.20.1 e2fsck 1.42.5 (29-Jul-2012) /dev/sda1: clean, 201087/7266304 files, 9690058/29045504 blocks [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I want to add, that the first time i tried this the console asked for my password and then when i put it, it said that it was wrong (it was not). Sistema de archivos de solo lectura means read only file system... [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Then i tried to put this: mount -o remount / [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]guido@Damonte:~$ mount -o remount / mount: sólo el usuario root puede efectuar esta acción [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana](only root user can make this action) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I supposed root user was the main user, this is my pc, i am the only user, then i am the master root user and the creator. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]In the first days this happened, when i had turned on the pc, it said to me that the hard drive crashed, stayed in that page when Ubuntu is loading, asked me if i wanted Ubuntu to solved it. When i did that, it stayed loading again, then restart as normal but whit the same problems. After a few days this stopped and just run like if nothing happened but whit my horrible issues. (i didn't touch configurations or anything). [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]If you could help it would be great, i don't ask in Spanish forums because there are less users than here. Thank you so MUCH![/FONT][/COLOR][/FONT][/COLOR]

---

### Post by kuifje09 on 2013-03-15
Hello, a read  only filesystem is not very handy..

On linux there is no such thing as a main user, there are regular users eventually with root permissions, and a root user.
Root user is rarely used, but in case of trouble or special actions.

When you want to check a filesystem, you need to be root, thats why you indeed did sudo fsck ...
But first you need to know which filesystem is in a readonly mode. howmany partions/disks are you using.

Please show the ouput of the command :   mount   . it will show what is currently mounted and how.

Edit : I had such problem a few years ago, and it came out in the end, my disk was in a bad state, I had to replace it.
But you can alway check ik first.

---

### Post by guidod93 on 2013-03-15
Thanks for answering! 
I did that and it showed me:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/guido/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=guido)


mount: aviso: /etc/mtab no se puede escribir (sistema de archivos de solo lectura).
       Es posible que la información de mount(8) no esté
       actualizada. Para tener una información real sobre los puntos de montaje del sistema
       compruebe el archivo /proc/mounts.
(that means, mount: aviso: /etc/mtab can't write (read-only filesystem, It is posible that the information of mount (8) is not updated. For more real information about the start system facts check the file /proc/mounts).

---

### Post by kuifje09 on 2013-03-15
Ah , thats indeed /dev/sda1   that needs checking.
/etc/*  is on  /  which is /dev/sda1
Probably realy bad.  You cannot check a filesystem which is mounted as with a root ( / ) filesystem.
Best options I would advise, boot from the cd, then check the /dev/sda1 and reboot.

Hopefully it can be repaired.

Run after booted from cd,   fsck -y /dev/sda1

It will repair, at least try to, and does not ask for each error what to do.
Probably a lot, but it is usally too much to do it realy by hand.

Be aware of the fact the disk can be in too badly  state.   but give it a chance.

---

### Post by guidod93 on 2013-03-16
[COLOR=#333333][FONT=Arial]I did that. Then restart. In the Ubuntu loading screen there was a text saying that Ubuntu was checking if my hard drive was ok. Then [/FONT][/COLOR][COLOR=#333333][FONT=Arial]i[/FONT][/COLOR][COLOR=#333333][FONT=Arial] started and the system run normally with no problems. I [/FONT][/COLOR][COLOR=#333333][FONT=Arial]watched[/FONT][/COLOR][COLOR=#333333][FONT=Arial] a movie, then tried to download a torrent, and the problem appeared again! I mean, [/FONT][/COLOR][COLOR=#333333][FONT=Arial]i[/FONT][/COLOR][COLOR=#333333][FONT=Arial] didn't touch anything, and the problem came again.I [/FONT][/COLOR][COLOR=#333333][FONT=Arial]really[/FONT][/COLOR][COLOR=#333333][FONT=Arial] [/FONT][/COLOR][COLOR=#333333][FONT=Arial]appreciate[/FONT][/COLOR][COLOR=#333333][FONT=Arial] your help, this is [/FONT][/COLOR][COLOR=#333333][FONT=Arial]completely[/FONT][/COLOR][COLOR=#333333][FONT=Arial] strange for me. I'm just a bit [/FONT][/COLOR][COLOR=#333333][FONT=Arial]disappointed[/FONT][/COLOR][COLOR=#333333][FONT=Arial] because [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I[/FONT][/COLOR][COLOR=#333333][FONT=Arial] [/FONT][/COLOR][COLOR=#333333][FONT=Arial]though[/FONT][/COLOR][COLOR=#333333][FONT=Arial] Ubuntu was more user-friendly (or the official website said that), but [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I[/FONT][/COLOR][COLOR=#333333][FONT=Arial] installed it one month ago and this is the third time [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I[/FONT][/COLOR][COLOR=#333333][FONT=Arial] have to reinstall it because something happens... I mean, [/FONT][/COLOR][COLOR=#333333][FONT=Arial]i[/FONT][/COLOR][COLOR=#333333][FONT=Arial] am not a monkey.. [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I[/FONT][/COLOR][COLOR=#333333][FONT=Arial] don't know how to program or manage this system, but [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I'm[/FONT][/COLOR][COLOR=#333333][FONT=Arial] not an idiot without any knowledge of [/FONT][/COLOR][COLOR=#333333][FONT=Arial]pc[/FONT][/COLOR][COLOR=#333333][FONT=Arial]. Do you know any other SO [/FONT][/COLOR][COLOR=#333333][FONT=Arial]I[/FONT][/COLOR][COLOR=#333333][FONT=Arial] can use for a low power pc? This one only has [/FONT][/COLOR][COLOR=#333333][FONT=Arial]1g[/FONT][/COLOR][COLOR=#333333][FONT=Arial] of ram, one more user-friendly or without this problems. Thanks a lot for your help.[/FONT][/COLOR]

---

### Post by Mark Phelps on 2013-03-16
If this is happening only AFTER you're downloading torrents -- you have your answer.  Something in the downloading is corrupting your filesystem.

---

### Post by kuifje09 on 2013-03-16
I doubt if the torent is corrupting anything, unless you run as root...
Also it is not related to whatever OS.
When you check the filesystem, offline , again,  does it find errors again?
This might be caused due to a dying disk.

I think of lookin in some of the loggings,  Have a look at the logging in /var/log
Then look in dmesg and syslog , your eye may fall on some error about writing to sda1.

Best to roll the files and run agian what you did and caused the switch to RO.
Maybe someone can give the command to roll the loggings ( to get a clean loggin in dmesg ansd syslog ,  just deleting would work also )

Edit: logrotate -fv /etc/logrotate.d/rsyslog   should do but even I tell to do it forcely, it doesn't

---

