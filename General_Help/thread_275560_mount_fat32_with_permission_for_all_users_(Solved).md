---
title: "mount fat32 with permission for all users (Solved)"
date: 2006-10-11
forum: General Help
---

### Post by josh on 2006-10-11
just a quick question. how do i mount a fat32 drive with read, write, execute for all users (owner, group, others)? i dont plan on doing it on /etc/fstab. this is for my removable storage. here is the command i type to mount it

```
sudo mount -t vfat -o rw,uid=josh /dev/sda5 /home/josh/keep
```

that only gives me
```

permisions for /home/josh/keep
owner  r - w - x
group  r -   - x
others r -   - x

```

in /etc/stab it is easy to put the umask=777 option for allusers to have r-w-x permissions but on the command line, how do you do that? the closest i saw was the uid=josh. i just want to mount my storage drive using the command line interface and have it give allusers r-w-x permissions without changing chmod everytime i mount it and without using /etc/fstab. thanks!

---

### Post by CapitalT on 2006-10-11
[SIZE="4"][COLOR="Red"]DANGER: DON'T DO THIS[/COLOR][/SIZE]

You could use chmod on the partition
> sudo chmod 777 /dev/sda5

But that's way too dangerous!
[SIZE="4"]
[COLOR="Red"]DANGER: DON'T DO THIS[/COLOR][/SIZE]

---

### Post by mitch.c on 2006-10-11
> **josh said:**
> just a quick question. how do i mount a fat32 drive with read, write, execute for all users (owner, group, others)? i dont plan on doing it on /etc/fstab. this is for my removable storage. here is the command i type to mount it

```
sudo mount -t vfat -o rw,uid=josh /dev/sda5 /home/josh/keep
```

that only gives me
```

permisions for /home/josh/keep
owner  r - w - x
group  r -   - x
others r -   - x

```

in /etc/stab it is easy to put the umask=777 option for allusers to have r-w-x permissions but on the command line, how do you do that? the closest i saw was the uid=josh. i just want to mount my storage drive using the command line interface and have it give allusers r-w-x permissions without changing chmod everytime i mount it and without using /etc/fstab. thanks!

The umask option works exactly the way your wrote it, so to modify your mount, it would look like this:
```
sudo mount -t vfat -o rw,uid=josh,umask=000 /dev/sda5 /home/josh/keep
```
man mount for more options. Look at the fat section as it is a common part of vfat.

---

### Post by xmastree on 2006-10-11
> **josh said:**
> just a quick question. how do i mount a fat32 drive with read, write, execute for all users (owner, group, others)? 

Try this:

**sudo mount /dev/sda5 /home/josh/keep/ -t vfat -o iocharset=utf8,umask=000**

I got that command from here:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by aysiu on 2006-10-11
You can't *chmod* a FAT32 partition, actually. Josh is on the right track.

Try this: ```
sudo umount /dev/sda5
sudo mount -t vfat /dev/sda5 /home/josh/keep -o iocharset=utf8,umask=000
```

---

### Post by xmastree on 2006-10-11
> **josh said:**
> in /etc/stab it is easy to put the umask=777 option for allusers to have r-w-x permissions but on the command lineActually, umask works the *opposite* way to chmod. So if you want rwxrwxrwx, you make umask=000.

---

### Post by mitch.c on 2006-10-11
> **xmastree said:**
> Actually, umask works the *opposite* way to chmod. So if you want rwxrwxrwx, you make umask=000.
Man, I'm slipping in my old age... I can't believe I didn't catch that in my post. Off to edit! :(

---

### Post by josh on 2006-10-11
thanks guys! that did the trick! good day!

---

