---
title: "Ubuntu freezes on boot up whilst checking filesystem"
date: 2007-02-11
forum: General Help
---

### Post by Maxwell7 on 2007-02-11
Hi 

I run Ubuntu Edgy on my Dell Inspiron 8500 laptop. Everything has worked fine for me, for months until this afternoon. (after some updates)

Ubuntu freezes on startup. Just about when the bar is halfway. I think it's when Ubuntu checks the 2nd partition of my harddrive. It is formatted as follows : 

hda1 : / linux partition (ext3?)
hda2 : Windows XP :      (NTFS)
hda3 : Shared partition: (FAT)

it appears somewhat like this: 
(not exact)

```

Checking root filesystem : 
fsck *something* 	[ok]
Checking filesystem *something* : 
fsck /media/dev/hda2 	

```

there it hangs. 

I can get a root shell by <ctrl><alt><delete> and can then kill that process. After that I can just startup gdm and Gnome like usual. Altough now my Windows and shared partition are not visible. 

What can i do about this? I'm working on my master thesis now, and it's due soon so every quick answer is greatly appreciated. :-)

Thank you very much in advance, everyone at Ubuntu Forums
Maxwell

---

### Post by dexter on 2007-02-11
You should also be able to skip it by pressing ctrl+c (works here). It's also possible to disable disk checking at startup, i found this on google:
> 
This command sets how often you want to run the checks.
sudo tune2fs -c 50 /dev/hdx@
The blue number is how often you want the checks run.
The red x is the drive letter (a for first drive, b for second, etc...)
The green @ sign is for the partition number.
Replace these values with ones appropriate to your system.
I am not sure what the upper limit is but if you set this to 0 it will turn them off.


---

### Post by Maxwell7 on 2007-02-12
Thanks, I will try that. 

Just for the record, we are talking here about the file system check that happens at every boot up. Not the one that happens every 30 times, right ?

---

### Post by Maxwell7 on 2007-02-12
I'm feeling more for reinstalling Ubuntu actually ... It worked fine before, it has to work fine now too. 

Would that solve the problem ?

---

### Post by gizmoarena on 2007-02-12
i have the same problem ... i want to stop checking all filesystems everytime ubuntu boots
... i used this method, and it didnt work :| 
> gizmo@desktop:~$ sudo tune2fs -c 50 /dev/sda7
[COLOR="Red"]tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/sda7
Couldn't find valid filesystem superblock.
[/COLOR]

what does these messages mean?

---

### Post by dcstar on 2007-02-12
> **gizmoarena said:**
> i have the same problem ... i want to stop checking all filesystems everytime ubuntu boots
... i used this method, and it didnt work :| 


what does these messages mean?

They mean you have a **broken** filesystem that needs fixing - that is why is tells you at every boot.

---

### Post by Maxwell7 on 2007-02-13
Is it wise to disable all filechecking ? 

What is the actual purpose of the filechecking at boot-up ?

---

### Post by Maxwell7 on 2007-02-13
I think I know where it goes wrong this time. 

> 
fsck.vfat /dev/hda3


This command takes forever to execute. I have no idea why. When I popped in Knoppix to make backups of my disks, nothing seemed to be wrong with the disk.

---

### Post by Maxwell7 on 2007-02-13
Ok, so now I know what went wrong and I've been able to fix it without seeking my resort in disabling the filesystem checks. 

This weekend I tried copying one of my dvd's to my laptop, so i can watch it without the disc. I used the -dumpstream function of Mplayer. Ok, so far so good. That seemed to work, as i was able to watch the movie. 

But after shutting down, something must have gone wrong because i now noticed that during a Knoppix terminal filecheck, it said that the file was *0 Bytes, 0 sectors*   .... stuff like that. 

And that is where my **fsck** kept hanging. After removing that 'empty' file, everything went perfectly again. 

Go Ubuntu !!!!!  :KS  :KS

and thanks everyone for your kind help !

---

### Post by Hellaxe on 2007-02-14
Well I'm having the same problem here.
This is hapennig in a FAT partition were i keep the video files and some more stuff.
But how do I know what file is making this hang??

Thanks

---

### Post by dcstar on 2007-02-14
> **Hellaxe said:**
> Well I'm having the same problem here.
This is hapennig in a FAT partition were i keep the video files and some more stuff.
But how do I know what file is making this hang??

Thanks

If you have a (relatively) unimportant filesystem, then you can turn off the checking by editing your /etc/fstab file.

At the far R.H.S. of each line their is either a "1", "2" or "0".

"1" means check at mounting as this is the root FS (only one entry should ever have a "1"), "2" means check (but I'm not the root FS) and "0" means don't bother checking.

If the Fat partition in question has a "2", then change it to "0".

You can later "umount" the partition and:
```
sudo fsck -y /dev/partition-name-whatever-it-is
``` to scan and automatically fix anything it finds.

---

### Post by Maxwell7 on 2007-02-15
What I did was, 

1. boot in recovery mode
2. when you see the filecheck is hanging, press <Control> + <C> , or if that doesn't work (it didn't in my case) <Control><Alt><Delete>, you should then get a command prompt - i.e. a root-terminal. 
3. In my case I had to kill that particular process to prevent overheating of my laptop. 
```
ps -ux
kill xxxx(proces_id)
``` will give you all the root processes running. then identify the hanging process and kill it 
4. resume normal startup by <Control><D>, or by starting up gdm
5. Once started up, open up a terminal and do a manual filecheck on that partition. It should then give you some more output, and show you which file it is busy on. Obviously the file that takes forever is the one causing your problems


edit : 
Whoops, too late ;-)

---

### Post by Maxwell7 on 2007-02-15
> **dcstar said:**
> 
You can later "umount" the partition and:
```
sudo fsck -y /dev/partition-name-whatever-it-is
``` to scan and automatically fix anything it finds.

Please be advised that it is apparently **crucial** that your filesystem is not mounted !! Otherwise it could cause major damage ... 

(I didn't know this at first)

---

### Post by Hellaxe on 2007-02-15
Thank you guys:
But i could understand that was one file that was corrupt and was causing the hanging when it reached the sda2 partition. Now it's ok.
But it's stupid that one file corrupt make a terrible headake.

---

### Post by Ken_Lewis81 on 2007-05-14
> **gizmoarena said:**
> i have the same problem ... i want to stop checking all filesystems everytime ubuntu boots
... i used this method, and it didnt work :| 
> gizmo@desktop:~$ sudo tune2fs -c 50 /dev/sda7
[COLOR="Red"]tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/sda7
Couldn't find valid filesystem superblock.[/COLOR]

what does these messages mean?

tune2fs is **not compatible** with vfat partitions!  The patterns that data is laid out in for an ext2-formated disk is not the same as the FAT format.  That's why tune2fs has issues, not because your disk is (necessarily) broken.  

Take care.
Ken.

---

