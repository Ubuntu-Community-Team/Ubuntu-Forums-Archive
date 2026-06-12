---
title: "How do I transfer a file from one Ubuntu partition to another?"
date: 2007-08-17
forum: General Help
---

### Post by kris2pe on 2007-08-17
I seperated my ubuntu partition into parts. The problem is that I can't transfer my files to other ext3 partition in ubuntu.

---

### Post by EndPerform on 2007-08-17
What's the mountpoint of it?  Do me a favor, open a terminal and type:

```
mount
```

also, type:

```
cat /etc/fstab
```

and post the results of both here so we can see them and maybe give you a better answer.

---

### Post by DamjanDimitrioski on 2007-08-17
To mount it> mount /dev/hda3 or change for what ever number is your partition.
To change permission> Open "sudo nautilus /media/hda+number of your partition"
                                      Then Right click ,properties, permissions, change owner to nobody, change group   
                                      to  nogroup other to create and read files.
Then you have it, free to use an partition!

---

### Post by kris2pe on 2007-08-19
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev)




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8ae5e124-53be-4380-9949-bd34e50f281e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=617fd3f9-f928-4b24-9be9-52ca514d9e65 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Ok so how do I do this? Sorry Noob!

---

### Post by kris2pe on 2007-08-20
The same question above:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev)

========================================================
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=8ae5e124-53be-4380-9949-bd34e50f281e / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=617fd3f9-f928-4b24-9be9-52ca514d9e65 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by bodhi.zazen on 2007-08-20
_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by kris2pe on 2007-08-21
chmod: cannot access `/mount/point': No such file or directory

I tried doing this but I ran into probs!

---

### Post by bodhi.zazen on 2007-08-21
LOL

which partition are you trying to access ?

you need to change "/mount/point" to the actual mount point.

for example, take a partition, hda1

sudo mkdir /media/data

# /media/data is the mount point

sudo mount /dev/hda1 /media/data

chown root.users /media/data

chmod 770 /media/data

---

### Post by kris2pe on 2007-08-21
OK very very confusing! I will try! 
I don't know what hda no it is sorry! 
Tell me why do I have to do this just to access this?
Is there any easy way to do this I mean really?

---

### Post by bodhi.zazen on 2007-08-21
What partition are your trying to mount ?

Basic partition information : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

can you post the output of the following commands :

```
sudo fdisk -l
mount
cat /etc/fstab
```

---

### Post by kris2pe on 2007-08-22
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8076    64870438+  83  Linux
/dev/sda2           29693       30401     5695042+   5  Extended
/dev/sda3            8077       29692   173630520   83  Linux
/dev/sda5           29693       30401     5695011   82  Linux swap / Solaris

I'm looking for the 106 gigs!
I just wanna transfer some files!

---

### Post by kris2pe on 2007-08-25
How do I do it? 
Please simplify it!
I want to copy specific files & folders to my second ubuntu partition!
NOt the entire hd!

---

### Post by Auax on 2007-08-25
If the disk is mounted, go to your "Media" directory, and choose the partition you wish to copy the file from, then browse untill you find it, right click on it, select "cut" if you want to move it, or "copy" if you wish to make a duplicate of it... then browse to the directory you wish to transfer it to, right click on empty space, and select "Paste 1 File".

---

### Post by kris2pe on 2007-08-25
I don't know if that's true! 
Coz I tried doing the copy & paste thing! 
It does not work! 
I got it mounted for sure!
mount /dev/sda3 /home/user/back folder

---

### Post by osos on 2007-08-25
hello.

with mount /dev/sda3 /home/user/back folder you mount your /dev/sda3 to /home/user/back, if your directory is back folder use backslash in front of back.
Is your partition mounted as read-only? Do you have permission to write to that disk?

---

### Post by kris2pe on 2007-08-25
Good question! I don't know! Coz in windows I just put a partition & it works on THE FLY! 
Yeah I'm noob! 
back folder was just a name not the exact one that I used! 
Um yeah so if you could help me that would be great!

---

### Post by tpg on 2007-08-25
Firstly, how did you create this partition, and is it an ext3 (i.e. linux) partition? As you are asking the question, I am guessing it doesn't show up in the file browser if you just open it (without doing any fiddling around).

Right. Let's say you've got the folder "back" in your home directory. Then you run the command
```
sudo mount /dev/sda3 /home/<user>/back
```
where <user> is your user name. I am assuming that /dev/sda3 is correct, and the partition is mounted. Now, if you run
```
ls /home/<user>/back
```
do you see the files you expect to on that partition?

---

### Post by DarkDancer on 2007-08-25
When you try to move a file what is the ***_exact_*** error message you get?

---

### Post by kris2pe on 2007-08-26
> **tpg said:**
> Firstly, how did you create this partition, and is it an ext3 (i.e. linux) partition? As you are asking the question, I am guessing it doesn't show up in the file browser if you just open it (without doing any fiddling around).[/CODE]
Using gparted live cd! I let it resize & split my ubuntu partition into 2 parts. I left on its on. I personally don't know whether there option to fill it out. Becoz it took so long to get it done that I had to sleep. When I woke my computer was shut down by my brother by pulling all the plugs & ****!
> **tpg said:**
> 
```
ls /home/<user>/back
```
do you see the files you expect to on that partition?
Folder=lost+found
Yes! This is what was in the partition!

---

### Post by kris2pe on 2007-08-26
> **DarkDancer said:**
> When you try to move a file what is the ***_exact_*** error message you get?

There's no error what so ever. I just can't copy files in the same type of partition. I can mount it but can't do anything w/ it!

---

### Post by tpg on 2007-08-26
OK, now, with the partition mounted, run
```
touch /home/<user>/back/randomfile.txt
```
If this fails, then there is a permission problem. Run
```
sudo chmod -R +rw /home/<user>/back
```
(which gives you read & write permission to the directory) and everything should work.

---

### Post by kris2pe on 2007-08-26
> **tpg said:**
> OK, now, with the partition mounted, run
```
touch /home/<user>/back/randomfile.txt
```
If this fails, then there is a permission problem. Run
```
sudo chmod -R +rw /home/<user>/back
```
(which gives you read & write permission to the directory) and everything should work.

For some reason that too didn't work!
This is what I did!
kris2pe@kris2pe:~$ touch /home/kris2pe/Desktop/Backup/randomfile.txt
touch: cannot touch `/home/kris2pe/Desktop/Backup/randomfile.txt': Permission denied
kris2pe@kris2pe:~$ sudo chmod -R +rw /home/kris2pe/Desktop/Backup
kris2pe@kris2pe:~$ sudo chmod -R +rw /home/kris2pe/Desktop/Backup
kris2pe@kris2pe:~$ touch /home/kris2pe/Desktop/Backup/randomfile.txt
touch: cannot touch `/home/kris2pe/Desktop/Backup/randomfile.txt': Permission denied

So these are the exact command line being placed. Tried copying files & all that!
No I don't want to back up files on cds or dvd I have 19gigs in total back up! 
I don't have backup external hd! 
DO I need to do this in gparted again?

---

### Post by kris2pe on 2007-08-26
Can this be solve?
I tried reformating! It didn't work!

---

### Post by tmahmood on 2007-08-26
reformatting what?

try this, 

Mount the partition the way tpg provided you

Then Alt+F2 to open the run dialog box, in the run Dialog box enter 

```
gksudo nautilus
```

After authentication Nautilus Window will open, Now copy your files to that partition using it.

---

### Post by kris2pe on 2007-08-26
I tried that for quite awhile. It doesn't work either. I just deleted the partition & will proceed to back up my data through my portable music player.
IS there good program that can compress videos or mp3 & etc into one archive file? I need to migrate huge amounts of files in my system right now!

---

### Post by tmahmood on 2007-08-26
You can right click on a file/directory and select "Create Archive..."

or you can just use the following terminal command to compress all the files in a single tar

tar -cf <file_name.tar> <source>

---

### Post by jim_p on 2007-08-26
> **kris2pe said:**
> Coz in windows I just put a partition & it works on THE FLY!

Just a thought that popped in my head...
The drive is formatted in ntfs,isn't it?
If so, you must install the ntfs-3g package that will allow you to copy and paste on ntfs drives.

```
sudo apt-get install ntfs-3g
```

---

### Post by kris2pe on 2007-08-27
> **jim_p said:**
> Just a thought that popped in my head...
The drive is formatted in ntfs,isn't it?
If so, you must install the ntfs-3g package that will allow you to copy and paste on ntfs drives.

```
sudo apt-get install ntfs-3g
```

NO! ITS NOT! Too late the problem has eliminated by not trying to solve but. Leaving it! So I went to archive my files the TRADITIONAL WAY! Using a DVD DOUBLE LAYER & a DVD Burner! GUESS what? 
That worst! THE SYSTEM CRASHES! WELL DON"T LET ME PULL OUT PROOF On that one! 
I'm using a GNOME BAKER & FIREFOX & IT ******* CRASHED LIKE I CAN"T EVEN KILL THE PROGRAM! 
OOOH!

---

### Post by bodhi.zazen on 2007-08-27
kris2pe :

I am sorry you are so frustrated ...

in order to have access to your partition you need to :

1. Set a mount point or place on the directory tree where you will mount the device

2. Mount the partition.

3. Put an entry in fstab.

4. set the proper ownership and permissions.

OK ? So ...


==================


1. Mount point :

The standard mount point is in /media 

You can mount it in /home/<user> if you like, bu t we need to use a consistent place.

The mount point you chose is **/home/<user>/back** so I will work with that.

2. You can mount with 

sudo mount /dev/sda3 /home/<user>/back


3. fstab

Open fstab with the following command :```
gksu gedit /etc/fstab
```

```
/dev/sda3 /home/<user>/back ext3 user 0 2
```

Re-mount the partition with :

```
sudo umount /home/<user>/back
mount /home/<user>/back
```


4. Ownership/permissions

```
sudo chown <user>.<user> /home/<user>/back 
chmod 770 /home/<user>/back 
```

You should now have rw access to the partition at /home/<user>/back 

```
nautillus /home/<user>/back 
```

**_Note_: You need to use your log in name in place of <user> in all the above commands/fstab entries.**

---

### Post by maybeway36 on 2007-08-27
You could use a Knoppix disk too.

---

### Post by kris2pe on 2007-08-28
> **bodhi.zazen said:**
> 
I am sorry you are so frustrated ...
I'm sorry that I even tried Ubuntu!  Whether its Ubuntu's fault or my fault's! It will end up becoming mine! So far this is the pinnacle of the Ubuntu experience! 
You know what bodhi ppl should know about this experience honestly! That going into Ubuntu means you going all through his perils. 

> **bodhi.zazen said:**
> 
3. fstab

Open fstab with the following command :```
gksu gedit /etc/fstab
```

```
/dev/sda3 /home/<user>/back ext3 user 0 2
```

I don't get this one! Do you put both of those in the command line? 
Or do I have to place it inside gedit?

---

### Post by bodhi.zazen on 2007-08-28
The first one you put in the command line. That will open fstab, a system file for editing.

The second needs to either be modified or edited in fstab. Post the contents of fstab if you do not understand what to add/change and we will help ...

---

