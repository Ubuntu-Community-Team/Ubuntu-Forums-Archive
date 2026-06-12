---
title: "mount windows partiton"
date: 2005-07-28
forum: General Help
---

### Post by storybookhero on 2005-07-28
I tried to mount my windows partiton and I got this error 
[SIZE=4]**mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab**[/SIZE]
does anyone know a way around this ? I would like to be able to access all of my music files

pllllz help

-Jeff

---

### Post by enang on 2005-07-28
To mount the windows patition, try :

make directory on "/mnt" e.g :" mkdir /mnt/mywindows" press enter
and typed e.g ": mount /dev/hda1 /mnt/mywindows " press enter

for "hda1" is partition hardisk for primary on the first partition
eg :   hda1, hda2, hd3...etc

sorry my english is bad!!!!! :)

---

### Post by MrCheese on 2005-07-28
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs) if it's an NTFS partition 

[http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat) if a FAT partition

---

### Post by angkor on 2005-07-28
[QUOTE=storybookhero]I tried to mount my windows partiton and I got this error 
[SIZE=4]**mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab**[/SIZE]
does anyone know a way around this ? I would like to be able to access all of my music files

pllllz help

-Jeff[/QUOTE]

Didn't you post this question here already:

[http://ubuntuforums.org/showthread.php?t=52421](http://ubuntuforums.org/showthread.php?t=52421)

O and you also started another post about java... :roll:

---

### Post by bored2k on 2005-07-28
[QUOTE=angkor]Didn't you post this question here already:

[http://ubuntuforums.org/showthread.php?t=52421](http://ubuntuforums.org/showthread.php?t=52421)

O and you also started another post about java... :roll:[/QUOTE]
 Thanks for pointing that out.

Storybokhero, do _not_ create dupes.
[size=1]*Strike*[/size]

---

### Post by storybookhero on 2005-07-28
well the previous posts left my problems unresolved so I found the best way to get new replies was to post a new post about the same thing. nobody answers my old posts...besides this is a free site and I believe Its aimed to help people with ubuntu issues....I know your all concerned with double posts and such but the main focus is ubuntu and to help n000bs such as me get the hang of things. so that I can help other people down the line..so I'm going to keep asking the same questions untill my problem is resolved because I Would love to make Ubuntu/ Linux my only O/S because Windows is just completely bug/virus and spyware..I honestly think that microsoft has there hands in it all...but thats just me. so if anyone can help with the java....partitioning issues that I'm having feel free to answer them please..I need all the help I can get here.  \\:D/  sorry for all the double posts I will try to refrain...but sometimes I get frustrated and need help in a hurry...hopefully you guys understand. 

-Jeff

---

### Post by bored2k on 2005-07-28
[QUOTE=storybookhero]well the previous posts left my problems unresolved so I found the best way to get new replies was to post a new post about the same thing. nobody answers my old posts...besides this is a free site and I believe Its aimed to help people with ubuntu issues....I know your all concerned with double posts and such but the main focus is ubuntu and to help n000bs such as me get the hang of things. so that I can help other people down the line..so I'm going to keep asking the same questions untill my problem is resolved because I Would love to make Ubuntu/ Linux my only O/S because Windows is just completely bug/virus and spyware..I honestly think that microsoft has there hands in it all...but thats just me. so if anyone can help with the java....partitioning issues that I'm having feel free to answer them please..I need all the help I can get here.  \\:D/  sorry for all the double posts I will try to refrain...but sometimes I get frustrated and need help in a hurry...hopefully you guys understand. 

-Jeff[/QUOTE]
 I'm sorry but there's simply no excuse for duping. Even if you have a 10month old thread, when you post in it in goes right up in the new post list just as a new thread will. Creating a new thread about old questions simply clutter the forums. You could repost in the old thread and eventually someone will help.

---

### Post by storybookhero on 2005-07-28
thanx man I didnt even think of that....oh well theres always next time right?

---

### Post by storybookhero on 2005-07-28
ok so I tried all of the above and I'm still getting the Root message. I dont know what I'm doing wrong..I would really love to access my music from ubuntu...I might just have to burn it to a dvd and transfer it over if theres no other way

---

### Post by bored2k on 2005-07-28
[QUOTE=storybookhero]ok so I tried all of the above and I'm still getting the Root message. I dont know what I'm doing wrong..I would really love to access my music from ubuntu...I might just have to burn it to a dvd and transfer it over if theres no other way[/QUOTE]
 Ok I haven't helped you on this matter so let's start from scratch shall we ?

Open up a root terminal (apps -  system - root terminal) then type
```
fdisk -l
```
There you will get a list of your partition table. Post us the whole list and tell us wich one do you want mounted.

Also post us your 
```
df -h
```Sorry for being rude btw.

---

### Post by storybookhero on 2005-07-29
heres the request from above 

fdisk -l

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              66G  2.1G   61G   4% /
tmpfs                 500M     0  500M   0% /dev/shm
/dev                   66G  2.1G   61G   4% /.dev
none                  5.0M  2.8M  2.3M  55% /dev

I dont see my windows partiton at all....weird ? is this normal? 
it should be 109G
and 75G 

well anyways I hope this helps with solving my issues

---

### Post by storybookhero on 2005-07-31
posted above and no reply....I might just rip everything into ubuntu 
if nothing else works...

---

### Post by bored2k on 2005-07-31
[QUOTE=storybookhero]posted above and no reply....I might just rip everything into ubuntu 
if nothing else works...[/QUOTE]
 It's **sudo** fdisk -l . You would get something like 
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       21675    10924168+   5  Extended
/dev/hda2   *       21676       67186    22937544    c  W95 FAT32 (LBA)
/dev/hda3           67187       77545     5220936   83  Linux
/dev/hda5               1         670      337302   82  Linux swap / Solaris
/dev/hda6             670       21675    10586803+  83  Linux

```

---

### Post by storybookhero on 2005-07-31
fdisk -l and heres what I got 


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8186    65754013+   7  HPFS/NTFS
/dev/sda2           16874       30515   109579365    f  W95 Ext'd (LBA)
/dev/sda3            8187       16873    69778327+  83  Linux
/dev/sda5           17245       30515   106599276    7  HPFS/NTFS
/dev/sda6           16874       17244     2979994+  82  Linux swap / Solaris

and heres what I got for ....df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              66G  2.4G   60G   4% /
tmpfs                 500M     0  500M   0% /dev/shm
/dev                   66G  2.4G   60G   4% /.dev
none                  5.0M  2.8M  2.3M  56% /dev

hope this helps

---

### Post by bored2k on 2005-07-31
... wich one do you want this time ?

---

### Post by storybookhero on 2005-07-31
I wanted to mount both windows partitions to access the music files

---

### Post by bored2k on 2005-07-31
[QUOTE=storybookhero]I wanted to mount both windows partitions to access the music files[/QUOTE]

[FONT=Times New Roman]I[/FONT]. Mounting /dev/sda1 (Read only)
```

** Local mount folder: /media/fumoffu **
$ sudo mkdir /media/fumoffu
$ sudo gedit /etc/fstab
** Append the following lines **> /dev/sda1       /media/fumoffu  ntfs    nls=utf8,umask=0222 0       0 $ sudo mount -a

``` 

[FONT=Times New Roman]II[/FONT]. Mounting /dev/sda5 (Read only) 
```

** Local mount folder: /media/sousuke **
$ sudo mkdir /media/sousuke
$ sudo gedit /etc/fstab
** Append the following lines **> /dev/sda5       /media/sousuke  ntfs    nls=utf8,umask=0222 0       0 $ sudo mount -a

```

---

### Post by storybookhero on 2005-07-31
thanks man this worked out pretty well. hey where did you learn all the commands for Linux..or Ubuntu? I've been meaning to ask someone

---

### Post by bored2k on 2005-07-31
[QUOTE=storybookhero]thanks man this worked out pretty well. hey where did you learn all the commands for Linux..or Ubuntu? I've been meaning to ask someone[/QUOTE]
 I don't know anyone that knows all the Linux commands.
If you want an overall help for Ubuntu, go to [http://ubuntuguide.org/](http://ubuntuguide.org/) .

The ones I do know you ask ? I could point you to a gazillion links wich would make you sleepy pretty quickly but I'll be honest. I joined this forum on February 20th, 2005. About 85% -or more- of the few things I know I learned them after joining. This is a great easy to read/devour knowledge database.

---

