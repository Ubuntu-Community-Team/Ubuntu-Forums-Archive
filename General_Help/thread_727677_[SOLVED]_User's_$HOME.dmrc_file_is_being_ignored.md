---
title: "[SOLVED] User's $HOME/.dmrc file is being ignored"
date: 2008-03-18
forum: General Help
---

### Post by jeffsa12 on 2008-03-18
I have 3 linux distros on this computer. After I altered some network and permission settings in my Linux Mint, I get this warning popup when I log into either Ubuntu of Mint.  This seems to cause no problems, but I'd like to try to get things back to normal. Below is what the message says along with a bad pic of the popup warning.

User's $HOME/.dmrc file is being ignored. This prevents the defautl language and session from being saved. File should be owned by user and have 644 permissions. User $HOME directory must be owned by usere and not writable by other users.

---

### Post by Rocket2DMn on 2008-03-18
Open a terminal and run
```
sudo chown *yourusername* ~/.dmrc
chmod 644 ~/.dmrc
```
Are you sharing your home directory between different distros?
You may also need to run
```
chmod 755 ~
```

---

### Post by jeffsa12 on 2008-03-21
Thanks Rocket2DMn,

I ran the code:

sudo chown jeff ~/.dmrc
chmod 644 ~/.dmrc

I first ran it from Mint, then ran it in Ubuntu. However, still the same problem. I am not sharing any home directories between the three Linux distros.

I copied and pasted both lines of code into my non root terminal, hit enter and was asked for password, hit enter again. When code is given in multiple lines as the first example, does it matter if you enter one line at a time, or should I enter multiple lines at the same time?

I did enter one line at a time after my first attempt did not seem to solve the problem....with the same result of the pop up warning upon log in.

 I have not ran the code:
chmod 755 ~

As I took it that it was to be ran only if I was sharing home directories. Should I run this code in my situation? 

Also I have both Ubuntu and Mint auto mounting upon booting, all the partitions on my HD, which includes the three different home partitions. Could this be related to the problem? I took screen shot of the file browser showing mounted partitions.

---

### Post by Rocket2DMn on 2008-03-21
That's a whole lotta partitions. Please post
```
ls -l /home
```
If you have a separate partition for your Ubuntu home, please say so and post your fstab file:
```
cat /etc/fstab
```
Actually, post it either way, it could give some interesting insight.
What network stuff did you change to cause this?

---

### Post by jeffsa12 on 2008-03-22
Yes, I have a separate partition for Ubuntu home.  It is installed onto hdb8. Ubuntu root is on hdb7

I have 2 hard drives. I have a linux swap partition on each hard drive so that it can run properly if I remove and or swap hard drives from computer to computer or chose to remove one of the hard drives. I have the following OS's and data installed on the partitions as follows.

Since I'm a linux newbie and I know very little about shell commands, I usually resort to research, copy and paste commands for setting things up if using a terminal is required.

 I was attempting to simply share files between my 2 computers on my network running Linux Mint  and was following a guide I found....don't recall where....It was for setting up a file server, samba?  I believe. It was wrong for what I really needed.. After following the guide and using commands posted in the guide, I still could not file share over my network.

After it didn't work for me, I went into natulis, home properties, and messed with the file permissions to try to get things working.....unsuccessfully. 

So I cannot tell you exactly what was changed using the commands posted in the guide and my home file permission changes as I really know very little about what is going on with the code, etc.....

Since then, I found a simple ssh file sharing guide at:[http://users.bigpond.net.au/hermanzone/p11.htm#Persistent_SSH_LAN_](http://users.bigpond.net.au/hermanzone/p11.htm#Persistent_SSH_LAN_)

A very simple and detailed guide for myself and what I wanted!! I set that up in Ubuntu on both computers now. Works great.

Below is some info you may find interesting and possibly help me diagnose my problem.

 

hda:
1 ntfs Win XP 1
2 fat32  Recovery 1 (os for WIn recovery)
5 fat32 os share  (windows and linux sharing)
6 Linusx swap
7 reiser fsPC Lin OS root
8 reiser fs PC Lin OS home
9  reiser fs Mint root
10 ext3  Mint home
11  fat32 movie storage for win and linux 

hdb:
1ntfs Win Xp 2
2 fat32  Recovery 2 (os for WIn recovery)
5 fat32 os share2  (windows and linux sharing)
6 Linusx swap
7 ext3 Ubuntu root
8 ext3 Ubuntu home
9 linux movies (k torrent up-down loads from here)
10 reiser fs software (deb packages not in repositories stored here)

The "old" folder showing in natulis is my shared file in my old (other) computer.

jeff@jeff-new-dsktp:~$ ls -l /home
total 20
drwxrwxrwx 68 jeff jeff  4096 2008-03-22 08:30 jeff
drwxrwxrwx  2 root root 16384 2008-01-23 11:06 lost+found
jeff@jeff-new-dsktp:~$ 


jeff@jeff-new-dsktp:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb7
UUID=e35b0b02-29a7-45cb-a5a7-47558adab0d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb8
UUID=56cd59e5-df83-4215-9495-1181314a8a57 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0CBC286ABC28510E /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda10
UUID=696b0a2a-a9ec-4dae-99d0-165cb70c18b2 /media/hda10    ext3    defaults        0       2
# /dev/hda11
UUID=40A8-D7EE  /media/hda11    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1759-73DC  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=9BC4-852A  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=425897de-16c0-4518-b91c-1ac901b28b47 /media/hda7     reiserfs defaults        0       2
# /dev/hda8
UUID=843b84d1-55ee-44bb-a3ca-4b3431f06f37 /media/hda8     reiserfs defaults        0       2
# /dev/hda9
UUID=96ec1acb-8934-4422-a66f-322ae0c60037 /media/hda9     reiserfs defaults        0       2
# /dev/hdb1
UUID=14ACC584ACC5613A /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb10
UUID=c0059448-fb19-87ee-df6f-5de78f890346 /media/hdb10    reiserfs defaults        0       2
# /dev/hdb2
UUID=1759-73DC  /media/hdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=140F-A8DB  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb9
UUID=6e7f7acc-c37d-0a9a-6b8a-d307ccd5ccd3 /media/hdb9     ext3    defaults        0       2
# /dev/hda6
UUID=322170cc-40ff-4886-8c16-ba681570324e none            swap    sw              0       0
# /dev/hdb6
UUID=5d07c577-1b2a-4508-9e2f-42f0f3529f30 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
jeff@jeff-new-dsktp:~$

---

### Post by Rocket2DMn on 2008-03-22
OK, I think the problem is that your /home/jeff folder has permissions "drwxrwxrwx" when it should be "drwxr-xr-x".  That is why you need to run the code
```
chmod 755 ~
```
That is the same as running
```
chmod 755 /home/jeff
```
This all follows from the part of the error message saying "User $HOME directory must be owned by usere and not writable by other users."
Run that command and see what happens.

---

### Post by jeffsa12 on 2008-03-23
Thank you for your help Rocket2DMn.

I thought I might add some info for us, " terminally  illiterate" Linux newbies. This is not the easy or quick way to check or fix this problem.  I tried this after using the terminal to fix it and this will also work.

Open the properties of your home folder using your file browser,  select the permissions tab, under the folder permissions, only the "owner"  should be checked for write permission. 

Near the bottom, the "Text view" should read: drwxr-xr-x

You can watch the  drwxr-xr-x change as you check and uncheck the options above.

Here is a little info I found for chmod
.
Chmod 755 means read and execute access for everyone and also write access for the owner of the file. When you perform chmod 755 filename command you allow everyone to read and execute the file, owner is allowed to write to the file as well.

---

### Post by Rocket2DMn on 2008-03-23
Hehe, thanks for filling in the noobs on the GUI.  As an FYI, the number permissions you see in chmod are from binary, where each rwx permission is 1 bit, so 3 bits for user, 3 for group, 3 for world.  
111 (binary, base 2) = rwx = 7 (decimal, base 10)
101 = r-x = 5
110 = rw- = 6
100 = r-- = 4

So:
755 = rwxr-xr-x
644 = rw-r--r--

If that doesn't make a whole lot of sense to you, it's OK.  There are only 10 types of people in this world - those who understand binary and those who don't.
:lolflag:

Glad your problem is solved :)

---

