---
title: "Access denied! [Resolved]"
date: 2007-05-25
forum: General Help
---

### Post by sadako1 on 2007-05-25
Hello fellow rebels!

I've just installed Ubuntu (see sig) and am having problems with my privileges. I only seem to be able to write to my /home directory, so migrating files from Windows is a pain. I've only allocated 40GB of space to the sda1 partition that I've installed Ubuntu in, and hoped to be able to use my 80GB sda3 partition for media and other things like that (sda2 is my swap file).

I can't create folders, I don't have permission to view a lot of things and I certainly can't add files.

I'm not just posting 'cos I'm lazy - I've not been able to find a suitable fix for this issue. I've already been through it trying to get my desktop to display at 1920x1200! That took me the best part of 2 days and made a real mess of xorg.conf a few times :D

I look forward to hearing from y'all in response to my first post ;)

Cheers in advance,

Andrew

---

### Post by dbott67 on 2007-05-25
By default, you're only allowed to write to your home folder.

To make changes to other areas (that require 'root' priveleges) you need to preface any command with 'sudo'.  Be very careful with this... with great power comes great responsibility (Stan Lee, creator of Spiderman).

Maybe you can post a specific example of what you would like to do & we can provide specific advice.

-Dave

---

### Post by vj air on 2007-05-25
hello, i am also a noob with little/no idea :)

im gonna hijack this post as i have a similar problem,im trying to update ubuntu to ubuntustudio.

the guide tells me to type :

**sudo su -c &#8217;echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list&#8217;**

but when i do, i get :

**bash: /ect/apt/sources.list': Permission denied**

any ideas?

thanks.

(ignore the fact that half of that has come up as a link....damm forums...hehe)

Arran.

---

### Post by dbott67 on 2007-05-25
The easiest way is to open the sources.list file in a text editor and add the line to the bottom:

** 1. Backup the current file:**
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
**2. Open the sources.list file in gedit:**
```
gksudo gedit /etc/apt/sources.list
```
**3. Add the following line to the bottom:**
```
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
```
**For example, here's my sources.list file:**
```
[COLOR=Purple]# some comments snipped out for brevity by me #[/COLOR]

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

[COLOR=Purple]# some comments snipped out for brevity by me #[/COLOR]

deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

[COLOR=Purple]# some comments snipped out for brevity by me #[/COLOR]

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
[COLOR=Purple]# type in this line below #[/COLOR]
[COLOR=Red]deb http://archive.ubuntustudio.org/ubuntustudio feisty main
[/COLOR]
```-Dave

---

### Post by sadako1 on 2007-05-25
Hi, all I wanted to do was store files there for now and maybe start installing programs. I have around 16GB left in the primary partition and set it up like that as I'm used to working in Windows where a small drive for OS and a larger drive for progs is desirable!

I've currently got about 15GB of MP3s taking up space in that partition, in /home... and I'd like to be able to move them. I want full access to all of my drives as I would in an M$ based system!

Cheers Dave,

Andrew

---

### Post by shen-an-doah on 2007-05-25
Is your windows partition NTFS? If so, you'll need to enable writing to it by installing "NTFS configuration editor".

---

### Post by vj air on 2007-05-25
thanks Dave, your a gentleman, totaly solved the problem \\:D/:KS\\:D/:KS\\:D/

---

### Post by whistlerspa on 2007-05-25
Or you could open 

System - Administration - Login Window 

and then open the Tab 'Security' and tick 

'Allow local system administrator login'

Once you've don this you can login as root using the same password and do whatever you like aka Windows. 
All the usual warnings about accessing your system like this apply of course but I don't see it as any more dangerous than doing the same on a Windows PC as local admin.

---

### Post by dbott67 on 2007-05-25
@sadako1:

Hi Andrew,

The really nice thing about linux is that you can create 'mount points' which basically means you can add new devices to the system (such as hard drives, or network storage devices) and they just appear as local folders.

So, if your system has multiple hard drives (or partitions or network shares) you just need to mount them to a folder.  We'll do it manually first, but then I'll show you how to add them to your /etc/fstab (this is the file that mounts the filesystem at boot: your root partition, your home partition, etc.).

1. First, identify the device which needs to be mounted (in this case, you mention that sda3 is the partition you want to use).  To view your current partitions, use '**sudo fdisk -l**':
```
dbott@feisty:/$ [COLOR=Red]**sudo fdisk -l**[/COLOR]
Password:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+  83  Linux
/dev/sda2            1913        4462    20482875   83  Linux
/dev/sda3            4463        4865     3237097+  82  Linux swap / Solaris
dbott@feisty:/$

```
2. Having identified the partition to mount, next we need to create a spot (i.e. a folder) to mount it.  If you wanted to dedicate the entire sda3 partition to mp3s, you could create a folder called **mp3s** (or **media** or whatever).  In this example, we'll create a folder in your home directory called 'media' which will contain your MP3s, videos and other multimedia files:
```
[COLOR=Red]**cd ~**[/COLOR]
[COLOR=Red]** mkdir media**[/COLOR]
```
3. Next, we need to mount the partition to the [COLOR=Purple]~/media[/COLOR] folder.  The issue here is what type of file system (NTFS or VFAT) as there are some parameters we need to consider.  The basic format is this:
```
sudo mount [COLOR=Red]/path/to/partition[/COLOR] [COLOR=Purple]/path/to/mountpoin[/COLOR]t vfat or ntfs, umask, etc.
```
For a VFAT partition, the example would be like this:
```
sudo mount /dev/sda3 ~/media/ -t vfat -o iocharset=utf8,umask=000
```
For NTFS, you should download **ntfs-3g**:
```
sudo apt-get install ntfs-3g
```and follow these instructions:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

If all mounts and you are happy, you can add the mount points to your fstab.  All details about fstab can be found here:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

-Dave

---

### Post by sadako1 on 2007-05-25
Ha, ha, thanks for that. Sorry, I had to laugh. It all worked perfectly - I actually created a mount point in my /home/andrew (personal) folder and it was perfect. Unfortunately I still don't have writing priveledges and an extra icon in a folder with a big red cross on it!

So, the mounting worked perfectly... sadly it didn't change whether-or-not I could write to it! what a crazy world this is. I really think we should have done some programming at school! I played with it in my free time at university, but in a week I won't have the sort of time I'm devoting to this and it'll most likely be canned if I can't at least have it working more flexibly!

Oh, extra info, the drive is formatted as ext3. If you could help me to get the permissions sorted I'd be happy.

I attempted to do what whistlerspa suggested (thanks for the input ;)) but I couldn't log in as 'root' - the login screen just kept refreshing and as you can tell, I'm not very confident with the command line yet!

Thanks so far though,

Andrew

---

### Post by aysiu on 2007-05-25
This will help you get write permission to NTFS:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

This will help you get write permission to Ext3:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

This will help you understand permissions better:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by dbott67 on 2007-05-25
Here's a good tutorial on mounting ext3 partitions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

-Dave

---

### Post by dbott67 on 2007-05-25
Holy crap! That aysiu guy is *FAST!!!!* :)


Good thing I linked to his site!

---

### Post by whistlerspa on 2007-05-26
RE refreshing login screen.

 Sorry  - I forgot to include a vital instruction. 

You also need to access Users and Groups ( In System - Administration)

Then goto    root - properties

Set the password by hand (I use the same one as stated before)

Then the tag    User Privileges     and tick the top to statements    (and save )

Again my apologies for the omission.

---

### Post by sadako1 on 2007-05-26
No need to apologise whistler, just helping's enough for me. Right, I'm in as root and I'm moving things around to the places that I want them. Next will be to read the tutorials that have been linked at the top by aysiu and dave - they both posted the same link so it must be good ;)

I'll report on how things have gone. Thanks again everyone, you've been a great help! This forum's excellent, by the way! There are clearly a lot of experienced and helpful people. I expect to have to use it to its fullest extent :D

Andrew

---

### Post by sadako1 on 2007-05-26
Woo-hoo! Command-line-tastic!

I tried to mount the drive from the command line, but was told to go away. I then decided to unmount the drive and followed the tutorial you guys gave me and BAM! Full access! Thanks very much. One satisfied customer!

Andrew

---

### Post by doccpu on 2007-05-27
I have had all kinds of trouble with linux letting me write files either thru mkdir, saving a file thru an editor or thru samba.

If fred is in login group fred and of group users why cant he make a dir or file in a dir that has user as a group priviledge? How do groups really acess files?
I am getting real angry at the problems of a user not being able to acces or create a file or dir. If he owns it he can, if he is in a dir of a group he is in he cant . What IS the precedence of what groups can use or create a file or dir?


I made a dir. owned by root and group of mine. worked fine.
I changed a higher dir to be owned by root and group i am a part of. I cant create anything in the higher dir or now in the dir that is supposed to be mine. What's with that?

---

### Post by dbott67 on 2007-05-27
It depends on what the default group of the user creating the file is in.

For example, my user account's (dbott) default primary group is also dbott.  If I provide rwx permissions at the "group level", the other user's must be a member of the group dbott.  Every file or folder I create has a user / group ownership of dbott (as illustrated below), except for a few which may have a group owner of root:
```
dbott@feisty:~$ ls -all
total 333964
drwxr-xr-x 100 [COLOR=Blue]dbott[/COLOR] [COLOR=Red]dbott[/COLOR]     8192 2007-05-27 22:58 .
drwxr-xr-x   8 root  root      4096 2007-04-23 20:11 ..
-rw-r--r--   1 root  root         0 2007-04-22 15:37 1
-rw-r--r--   1 dbott dbott   203320 2006-11-16 15:18 1_NAT_2_Routers.png
drwxr-xr-x   2 dbott dbott     4096 2006-12-24 21:11 2006-12-24--21.10.39
-rw-r-----   1 dbott dbott   205562 2006-12-03 15:33 2006_JK_Lindsay.jpeg
drwx------   8 dbott dbott     4096 2007-04-15 13:13 .amsn
drwx------   2 dbott dbott     4096 2007-04-15 13:13 amsn_received
drwx------   2 dbott dbott     4096 2007-03-31 11:28 .aptitude
drwxr-xr-x   2 dbott dbott     4096 2007-04-21 18:04 archive
drwxr-xr-x   1 [COLOR=Blue]dbott[/COLOR] [COLOR=Red]root[/COLOR]      4096 2007-05-27 22:45 archive1
-rw-r--r--   1 dbott dbott    45988 2007-01-08 10:16 att9575.wav
-rw-r--r--   1 dbott dbott   253363 2007-05-14 12:10 attachment.php
-rw-r--r--   1 dbott dbott    71728 2007-01-08 10:16 attD65C.wav
-rwxr-xr-x   1 dbott dbott  1185962 2006-11-10 23:29 auth.log.0
drwxr-xr-x   2 dbott root      4096 2007-04-22 15:51 .automatix
drwxr-xr-x   2 dbott dbott     4096 2007-03-24 19:16 .avidemux
-rw-------   1 dbott dbott     8083 2007-05-27 22:43 .bash_history
-rw-r--r--   1 dbott dbott      220 2006-11-10 21:07 .bash_logout
-rw-r--r--   1 dbott dbott      414 2006-11-10 21:07 .bash_profile
-rw-r--r--   1 dbott dbott     2227 2006-11-10 21:07 .bashrc

```I could create a new group called "sales" and add all of the appropriate users to that new group.  Then, I would have to "chgrp" or "chown" the folder so that the groups "sales" can rwx in the directory.

Here are 3 good tutorials that go over user & group permissions:

- [basic user & group permissions with chmod/chown/chmod]("http://www.freeos.com/articles/4440/")
- [more advanced group permissions]("http://news.softpedia.com/news/Managing-User-Accounts-on-Linux-36645.shtml")
- [a good multi-user, multi-group explanation]("http://lowfatlinux.com/linux-file-permissions.html")

-Dave

---

