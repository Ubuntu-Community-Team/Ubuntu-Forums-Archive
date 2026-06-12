---
title: "Mount ext3 partition as normal user"
date: 2006-10-21
forum: General Help
---

### Post by fenomenoxp on 2006-10-21
Hi everyone, i'm trying to write on an ext3 partition as a normal user (I don't need to be able to mount it as a normal user, just write on it). I have tried setting "uid=1000" but it seems ext3 doesn't support that option. I have tried chown and chmod the mount point, but all I can do is write a file on the main folder (I mean on "/media/sda4", when the partition is mounted) but I can't make any new directory or delete anything. Is there any way to solve it or should I switch the partition to fat32 (wich actually works fine with another partition I have mounted, giving me full read/write access). I've tried everything I have found on threads and solutions seem to work for other people, but not in my case. I even tried formatting the partition (just in case it was corrupted). By the way, is there anyway to mount it using pmount?
Thanks in advance

---

### Post by tuxrtfm on 2006-10-21
I'm not sure this will work as its been awhile since I've done it, but I think you need to add "users" to the options part of partitions fstab entry.

Good Luck,
TuxRTFM

---

### Post by fenomenoxp on 2006-10-21
Tank you for your reply, but it didn't work :(
May it be a bug??

---

### Post by tuxrtfm on 2006-10-21
I just reread your post, it sounds like the files all have root as the owner.
in the terminal type:
```
sudo nautilus
```

Then navigate to /media and right click on sda4.
Select the permissions tab and change the owner and group to your username
also click "Apply permissions to enclosed files."

---

### Post by fenomenoxp on 2006-10-21
Hi! I finally got it to work! Thank you very much for your help

---

### Post by tuxrtfm on 2006-10-21
No problem, just glad you got it to work.

Tuxrtfm

---

### Post by spectatorion on 2007-07-30
actually, instead of using nautilus, you can just use the chown command.  it does exactly what you want and works thusly:```
sudo chown -R <user>:<group> <filename>
```

the -R is to make it recursive.  substitute your user name (and optionally a group name) and the file name.  of course those brackets are just to indicate substituted text and should not be in the actual command execution.

when running programs as root, it is best to run as specific and basic a command as possible.  nautilus is kind of big and unwieldy and probably does a lot of file system writes, which could potentially overwrite files or pose security risks.  using chown does exactly what you want and nothing more.

frustrating that the uid for mounted linux filesystems cannot be set with the fstab, while dos/windows filesystems can.  go figure...

---

### Post by tuxrtfm on 2007-08-15
Alas I must admit that I did not know how to do it that way.  I appreciate your input, as I always hated running nautilus as root for the very reasons you mentioned.  But, no more, thanks to that little tidbit.

As for fstab / uid not working, I think this is a disro specific issue.  I was able to set it in strait debian, If I remember correctly, that is.


TuxRTFM
P.S. Vash Rules

---

