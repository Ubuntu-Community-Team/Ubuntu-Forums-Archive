---
title: "Two probably dumb newbie questions"
date: 2004-11-09
forum: General Help
---

### Post by Monika on 2004-11-09
Apologies if this should be going into the Installation part of the forum or if somebody already asked somewhere (but I didn't find it)...

I'm a linux beginner (well, used Red Hat 9 and SuSE 9.1 before but while I could see the advantages, I had problems doing all I wanted in them and ended up going back to windows each time...).

Anyway, Ubuntu looks great so far :-) And apart from video editing which I'm unfortunately going to have to do in Windows (incompatible hardware, no linux drivers), I can probably do just about anything else I need to in Ubuntu (and probably better too!) without enourmous complicated efforts to try and install the applications I need (first time using a Debian based distribution and I love it :-) ).

But one thing is that I can't see my windows hard drives/partitions in Ubuntu and while I don't need all of them to appear (in fact, the non-appearance of one hard drive is very convienient since it seems to hang most linuxes during boot and is the reason for me not having tried out Debian or Mandrake yet), there's about 2 that I would like to have access to in Ubuntu (one a nfts one which I know I would only be able to view but that's good enough, and another a fat32 which hopefully I could use to "interchange" data between Windows and Linux, yes?).
I *think* what I did wrong was that during the installation process in the partition table, I left "do not use" and probably should have selected "use and keep existing data" or I think there was an option like that, on the the partitions that I want to have access to in Ubuntu. But I'd prefer to ask since I'm terified about doing anything to my Windows partitions ;-)
Is there any way of doing it now without reinstalling? well, I guess it's not like reinstalling is that difficult :-) And come to think of it I might like to repartition anyway cause I was thinking that maybe I would like a /home partition... But I have to think through that... 

Ah... and while I'm asking stupid questions... I haven't got Polish characters on Ubuntu yet and would like to (even though I'm using English as the system language - I prefer that). Which package should I be installing? (I did choose a Polish key map during installation)

Thanks to anyone who has the patience to reply :-D

---

### Post by ulrich on 2004-11-09
hi,
i really dont know if theres a graphical way to do this but it isnt that much of a hassle.

first you need to know which partitions you want to use.
open a terminal and switch to root 'sudo -s'. you now have root terminal.
assuming the partitions reside on your first hd (otherwise hdb)
```
parted /dev/hda print
```
will show something like
```
7      37197,409  58643,525  logical   fat32 
```
first charakter is the partition number, in this case 7.

then open up 'gedit' as root (just type it in the root terminal) and open the file **/etc/fstab**
this file handles your partitions and mountpoints
add a line like
```
/dev/hda7       /media/winFat   vfat    defaults        0       0
```
now while still root make that directory you just enterd in fstab
```
mkdir /media/winFat
chmod -R 755 /media/winFat
```
this changes the permissions for that folder so that your user can write to this dir.

finally
```
mount -a
```

now there should be a nautilus window with the contents of your fat32-partition.
also the fat32  partition gets mounted every time you start your computer.
for the ntfs-partiton do the same. except that **vfat** is then **ntfs** and there must be another dir to mount it in fstab.

for the charakters.. i dont know :)

hope this helps

---

### Post by Monika on 2004-11-09
Thanks Ulrich :)

It worked with the FAT32 partition no problem. With the ntfs it doesn't seem to want to... I mean it's mounted :) And I can access it from Ubuntu, but only as root. I tried typing in the chmod command that you wrote again (as root) and it spend about 2 minutes on changing permission for all the files (over 25GB of data on that partition), but then when I tried again, again I could only access it as root :( Which I guess is a lot better that not accessing it at all ;) But still...

I've solved the Polish characters thing I think :) It was very simple, just put a keyboard layout applet on one of my toolbars in GNOME and then right-clicked on it and now I can type Polish characters no problem :) Although unfortunately a Polish instant messenger that I installed, still doesn't seem to want to display Polish characters :( oh well... I'm going to be changing the application anyway cause I don't like the GNU Gadu application. Kadu unfortunately isn't in the repository, but I guess I'll try installing it from source, I had it in SuSE and it seemed to work much better for me :)

---

### Post by Opiate on 2004-11-09
Try adding a umask flag to your NTFS fstab line.

-example-

```
/dev/hda1 /home/tyler/windows ntfs umask=0222
0 0
```

This should solve your access problems.

---

### Post by Monika on 2004-11-09
It doesn't seem to have changed a thing :( But thanks!

Come to think of it, I might just copy what I need into Ubuntu through that FAT partition and then I don't really need the ntfs anyway...

One important question though (cause I'm considering reinstalling Ubuntu to make a home partition, it seems like an intelligent thing to do...). So if during the installation I  choose "use and keep existing data" and select a mount point for the FAT partition, then I will have the windows partitions mounted during the installation, yes?

---

### Post by Monika on 2004-11-09
Ah, damn... I didn't try before... The FAT32 partition seems to be read only under Ubuntu :-(

---

### Post by Monika on 2004-11-09
I reinstalled Ubuntu, so as to have a /home partition and I tried setting the FAT32 windows partition during the installation so that Ubuntu would see it. And it does "see" it, but I still cannot write to it from linux :( Tried the chmod command and it didn't help.

I don't really want to end up copying 5GB of files onto CD-roms because I want them in linux... What other options do I have to copy some of my files from windows?

---

### Post by TravisNewman on 2004-11-09
[QUOTE=Monika]I reinstalled Ubuntu, so as to have a /home partition and I tried setting the FAT32 windows partition during the installation so that Ubuntu would see it. And it does "see" it, but I still cannot write to it from linux :( Tried the chmod command and it didn't help.

I don't really want to end up copying 5GB of files onto CD-roms because I want them in linux... What other options do I have to copy some of my files from windows?[/QUOTE]
 Here's my fstab, see what you can do with it. Fat32 only, because I don't have the NTFS drive anymore (made the big switch :)):
```
/dev/hdaX	/mount/point	vfat	rw,user,auto,uid=1000,gid=1000,umask=0000 0 0
```

Obviously change hdaX to whatever partition is yours, and /mount/point to where you want it mounted.
I THINK my NTFS drive had the same options, except vfat would be ntfs, rw would be ro, and umask was 0222

Don't get discouraged. I had the same issues at first.

---

### Post by Monika on 2004-11-10
I tried editing the hda3 (my windows FAT32 partition) line to what you have and then I rebooted to see what would happen and now it doesn't even display the contents of that partition (and still doesn't let me write to it).

Thanks to everyone who has been trying to help with this though! Hope that there are some more ideas...

---

### Post by Monika on 2004-11-10
Wheee, problem solved it seems :) (or at least I hope so ;) )

I found this thread:
[http://ubuntuforums.org/showthread.php?t=3843](http://ubuntuforums.org/showthread.php?t=3843)

And the guidelines there for editing fstab seemed to work :) I mean I've only done the FAT partition as of now cause I haven't decided whether I want the ntfs one to appear in ubuntu or not, but at least for the fat partition the following does work (of course after altering "hda1" and the mount point):

```
/dev/hda1 /media/driveC vfat rw,umask=0,user,codepage=850,exec 0 0
```

Thanks to everyone who tried to help :) I'm still a bit vague about what I've actually been doing ;) But I have learnt something from this, so thank you very much :)

I will come to pester the forum with some other problems very soon ;) (I will also try to post them under better topics next time rather than "newbie questions" - sorry for that :) )

---

### Post by burque on 2004-11-10
Dear Monika,

I haven't tried to read/write ntfs partitions yet myself, but this thread looked encouraging:

[http://www.ubuntuforums.org/showthread.php?t=1886&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=1886&highlight=ntfs)

Several of the posters in the thread reported luck with their ntfs partitions. I hope this helps.

Regards,
burque

---

### Post by Monika on 2004-11-10
Thanks :) I don't think I'll be mounting an ntfs partition in ubuntu on my computer, but I might be installing it eventually on my mum's computer if I manage to tweak everything else the way I want it (I have to be sure everything works well or my mum would kill me ;) but on the other hand she really likes the default look of ubuntu anytime she passes by so she might become a user if she can do anything she needs to on it without any extra hassle ).
The nfts guidelines seem to be the same thing that was on the thread that I found and that worked for me, so reliable enough I think ;)

Anyway thank you everybody :)

---

