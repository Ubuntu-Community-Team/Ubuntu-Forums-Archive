---
title: "generic &quot;having trouble with fstab&quot; thread"
date: 2007-01-23
forum: General Help
---

### Post by Choad on 2007-01-23
ok, i had my hard disk partitioned as such

/dev/sda1 - ext3 - root
/dev/sda2 - ntfs - windows
/dev/sda3 - ext3 - storage
/dev/sda5 - swap (extended partition)

now i decided that both my linux and windows partitions were too small, and i couldnt resize them with gparted because it wont move an ext3 OR an NTFS partition. so i backed up all my music, videos and pictures on to a series of dvd's and cleaned the slate apart from sda1, which i left. the partition layout now is EXACTLY the same. /etc/fstab has been left.

to begin with, it wouldnt mount the storage partition. that was easy to figure out: it was using that hash thing instead of its logical drive location, so i swapped out the hash for "/dev/sda3" and it worked

ill attach a screenshot of my /etc/fstab so that it keeps the formatting nice 
[[IMG]http://img155.imageshack.us/img155/2919/screenshot19ff.th.png[/IMG]](http://img155.imageshack.us/my.php?image=screenshot19ff.png)

i have no write permissions on /media/storage

i have searched to forums, and tried various methods of giving myself write permissions but to no avail

fsck says its clean

heres my mtab

```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=richard 0 0
/dev/sda3 /media/storage ext3 rw 0 0

```

thanks in advance :)

---

### Post by taurus on 2007-01-23
```
sudo chown -R **richard**:**richard** /media/storage
sudo chmod -R 755 /media/storage
```
(where **richard** is your login name.)

---

### Post by Choad on 2007-01-23
> **taurus said:**
> ```
sudo chown -R **richard**:**richard** /media/storage
sudo chmod -R 755 /media/storage
```
(where **richard** is your login name.)
i am a little creeped out that you know my real name... but ill give it a go none the less.

---

### Post by Choad on 2007-01-23
> **Choad said:**
> i am a little creeped out that you know my real name... but ill give it a go none the less.
lol it worked

but doesnt that mean that only i can use it? not that its a problem; only i use this laptop, but technically its a bit of a hack isnt it?

---

### Post by taurus on 2007-01-23
Look at the screenshot that you have included!  It says right there, **[COLOR="Blue"]richard@richard-laptop: ~[/COLOR]**...

---

### Post by Choad on 2007-01-23
lol :rolleyes: thanks

---

### Post by taurus on 2007-01-23
> **Choad said:**
>  but technically its a bit of a hack isnt it?

What do you mean by a hack?  You want to write to it and I showed you how to change the onwership of /media/storage so you could write to it.  If that's not what you want, then we can change it back to root.  Then, you need to use sudo if you want to write to /media/storage.

---

### Post by Choad on 2007-01-23
> **taurus said:**
> What do you mean by a hack?  You want to write to it and I showed you how to change the onwership of /media/storage so you could write to it.  If that's not what you want, then we can change it back to root.  Then, you need to use sudo if you want to write to /media/storage.

i mean that ideally anyone should be able to read/write this partition, not just me :)

---

### Post by taurus on 2007-01-23
Right now, you are the only one who can read/write/execute (besides root) to /media/storage.  Everybody can only read/execute.  And if you don't want others to read/execute /mdia/storage, change the permission to 700.

---

### Post by Choad on 2007-01-23
> **taurus said:**
> Right now, you are the only one who can read/write/execute (besides root) to /media/storage.  **Everybody can only read/execute. ** And if you don't want others to read/execute /mdia/storage, change the permission to 700.

ja, i want everyone to be able to write as well

---

### Post by taurus on 2007-01-23
```
sudo chmod -R 777 /media/storage
ls -la /media
```

---

### Post by po0f on 2007-01-23
An even better solution would be to make sure that all the users you want to have write access be in the same group ('users' sounds good  ;)).  You probably do not want global write access to these partitions.
```
[FONT="Courier New"]$ sudo chown richard:users /media/storage
$ chmod 775 -R /media/storage[/FONT]
```

To see if you're in the 'users' group:
```
[FONT="Courier New"]$ groups | grep users[/FONT]
```

To add yourself if you're not (takes effect after a logout/re-login):
```
[FONT="Courier New"]$ sudo gpasswd -a <username> users[/FONT]
```

---

### Post by Choad on 2007-01-23
that sounds perfect!

im in windows atm tho, so wont be able to try for a bit. thanks to both of ya anyhow, im sure it will work :)

---

### Post by SRQ on 2007-01-27
This was helpful for me, but is there not a way to change the owner of the partition automatic when it is mounted (thus when fstab is loaded) ?

I think that with the method you provided, you have to chmod every time you boot.

---

### Post by Lil_Eagle on 2007-01-27
If you want anyone (all users) to be able to write to /media/storage, you can accomplish that by changing fstab.  modify the line:
```
/dev/sda3   /media/storage   ext3   defaults   0   2
```
to:
```
/dev/sda3   /media/storage   ext3   defaults,umask=007  0  2
```

That will give read, write and execute access to all files on that partition.

Change it to umask=006 if you only want read/write.

---

### Post by SRQ on 2007-01-28
Ok, I knew that. I think it was mentioned by someone in this thread already.
I found out how to change owner automatic in fstab with this code:
```
/dev/hda9       /home/srq/documents  vfat   iocharset=utf8,umask=007,users,gid=100,uid=1000        0   0
```

---

### Post by Lil_Eagle on 2007-01-29
Funny, I didn't notice it in this thread.  I'm glad you have it working like you want.

---

### Post by Grifter81 on 2007-10-27
Hey guys. I'm having a small issue. I want to mount a network drive from my windows xp machine. However, whenever I try to save the fstab file, it tells me that I don't have the rites. Can somebody point me in the right direction?

---

### Post by taurus on 2007-10-27
> **Grifter81 said:**
> Hey guys. I'm having a small issue. I want to mount a network drive from my windows xp machine. However, whenever I try to save the fstab file, it tells me that I don't have the rites. Can somebody point me in the right direction?

If you want to write to /etc/fstab, you need to run it with sudo/gksudo.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by Grifter81 on 2007-10-27
Thanks mate! You're a star!

---

### Post by popat007 on 2007-11-02
Thanks @taurus and all

you help me out to on swap in fstab,

---

