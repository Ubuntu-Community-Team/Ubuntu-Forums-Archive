---
title: "Permission problem"
date: 2006-10-31
forum: General Help
---

### Post by SupremePiracy on 2006-10-31
Hey!

I want to copy files from my crashed linux system to my external hdd with a live cd. The problem is that I don't have permission to do so. chmodd does not work.

path to files I want to copy: /target/home/tobbe
external hdd: /media/Volume

--------------------------------------------------------------------------------------------------------------------------

root@ubuntu:/target/home/tobbe# cp /target/home/tobbe/* /media/Volume/
cp: omitting directory `/target/home/tobbe/Desktop'
cp: omitting directory `/target/home/tobbe/Film'
cp: cannot create regular file `/media/Volume/hiscore.dat': Read-only file system
cp: omitting directory `/target/home/tobbe/Incomplete'
cp: omitting directory `/target/home/tobbe/Installationer'
cp: cannot create regular file `/media/Volume/jazz2.log': Read-only file system
cp: cannot create regular file `/media/Volume/Make me a whitch~': Read-only file system
cp: omitting directory `/target/home/tobbe/Mina Dokument'
cp: omitting directory `/target/home/tobbe/Musik'
cp: omitting directory `/target/home/tobbe/Program'
cp: omitting directory `/target/home/tobbe/Spel'
cp: cannot create regular file `/media/Volume/stderr.txt': Read-only file systemcp: cannot create regular file `/media/Volume/stdout.txt': Read-only file systemcp: cannot create regular file `/media/Volume/Teknik läxan~': Read-only file system
cp: cannot stat `/target/home/tobbe/TransGaming_Drive': No such file or directory
cp: cannot create regular file `/media/Volume/uninstalldirs': Read-only file system

---

### Post by MyAnda on 2006-10-31
looks like /media/Volume is mounted read-only

try to umount it and remount it with read write perms
"mount" to see what the device name is for /media/Volume 
"sudo umount /media/Volume"
"sudo mount /dev/xxx /media/Volume" where xxx is the device name

"mount" to see that it show rw for /media/Volume

also you will want to copy recursivly 
so use i tend to use "cp -rap" for something like that

---

### Post by SupremePiracy on 2006-10-31
> **MyAnda said:**
> looks like /media/Volume is mounted read-only

try to umount it and remount it with read write perms
"mount" to see what the device name is for /media/Volume 
"sudo umount /media/Volume"
"sudo mount /dev/xxx /media/Volume" where xxx is the device name

"mount" to see that it show rw for /media/Volume

also you will want to copy recursivly 
so use i tend to use "cp -rap" for something like that

Nope, that didn't work. Still have the same problem.

---

### Post by dannyboy79 on 2006-10-31
what are the permissions and who is the owner of the Volume folder?
ls -l /media/Volume/
i think if you let the system mount it, it get mounted read only but if you umount it, and then remount it with a rw option, it should allow you to write to it. If it's like a sd card, don't forget to make sure that the "lock" button isn't on, that happened to me once. It was pretty funny after I thought about it.

---

### Post by SupremePiracy on 2006-10-31
> **dannyboy79 said:**
> what are the permissions and who is the owner of the Volume folder?
ls -l /media/Volume/
i think if you let the system mount it, it get mounted read only but if you umount it, and then remount it with a rw option, it should allow you to write to it. If it's like a sd card, don't forget to make sure that the "lock" button isn't on, that happened to me once. It was pretty funny after I thought about it.

It's my friends hdd. The permissions is ready only by root. 
And it's an usb external hdd.
I tried: 
sudo rsync -av /target/home/tobbe /media//Volume/

That seemed to work, but it stops copying files after a while. I've tried copying a singel folder and it stops there aswell...

---

### Post by dannyboy79 on 2006-10-31
have you tried to mount it in another folder that you create and chmod? don't put the folder in media either. also, you didn't post what the output of ls -l /media/Volume/ was.

---

### Post by SupremePiracy on 2006-10-31
root@ubuntu:/target/home/tobbe# ls -l /media/Volume/ total 48
dr-x------ 1 root root    0 2006-04-08 08:50 Backup
dr-x------ 1 root root    0 2006-05-31 10:26 Christina
-r-------- 1 root root  880 2002-01-08 11:25 DTemp.att
dr-x------ 1 root root 8192 2006-09-16 13:08 Filmer
dr-x------ 1 root root 8192 2006-10-31 14:06 mina dokument_
dr-x------ 1 root root 4096 2006-10-31 14:05 Mina dokument
dr-x------ 1 root root 8192 2006-10-31 14:05 Min musik
dr-x------ 1 root root    0 2006-07-08 21:27 msdownld.tmp
dr-x------ 1 root root    0 2006-05-20 14:55 Recycled
dr-x------ 1 root root 4096 2006-10-31 14:05 RECYCLER
dr-x------ 1 root root 4096 2006-09-02 11:20 Spel
dr-x------ 1 root root 4096 2006-09-02 11:12 St?da datorn
dr-x------ 1 root root 4096 2006-08-23 09:08 System Volume Information

I tried to copy another folder aswell but... 
sent 279658560 bytes  received 16328 bytes  4863911.10 bytes/sec
total size is 279575088  speedup is 1.00
rsync error: some files could not be transferred (code 23) at main.c(791)

mkdir Tobbe
mkdir: cannot create directory `Tobbe': Read-only file system

---

### Post by MyAnda on 2006-10-31
can you post the output of mount...is there any chance the drive is ntfs (would also give you read-only)
the line "Read-only file system" is the most interesting to me... the only times i have seen that are 
bad disk, ntfs, mounted read-only
have you verified that anything is actually making it to the drive?
do a ls on the volume, unmount/mount and ls again...

---

### Post by David Corrales on 2006-10-31
> **MyAnda said:**
> can you post the output of mount...is there any chance the drive is ntfs (would also give you read-only)
the line "Read-only file system" is the most interesting to me... the only times i have seen that are 
bad disk, ntfs, mounted read-only
have you verified that anything is actually making it to the drive?
do a ls on the volume, unmount/mount and ls again...

I was about about to ask the same thing. Is the drive NTFS? Because if it is, you'll have to use another drive or repartition it.

---

### Post by SupremePiracy on 2006-11-01
yes, it's an NTFS hdd. But since I have no patience I decided to copy my most important files to my 512 mb flash drive and then paste them to my laptop and then copy them back on my fresh edgy install. 

Thanks for the help anyway! :)

---

### Post by dannyboy79 on 2006-11-01
ohmygod, that is so funny, we were all wondering what the hell was going on and the whole time you were trying to write to a filesystem that linux doesn't support out of the box. you would have to install something additional to write to ntfs but there were problems in the begining and people were losing data and despite what people say about it workoing alright now I think to  myself, why would I want to risk it? what benefits does ntfs have over ext3 that would really be worth the risk. Anyway, now you know you can't write to a ntfs drive unless you follow this, [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+to+ntfs](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+to+ntfs)

---

