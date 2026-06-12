---
title: "home turned into executable"
date: 2013-09-26
forum: General Help
---

### Post by mut3d87 on 2013-09-26
hey all i have had a major system screw up and i dont know how to fix it.

I was running xubuntu13.10 and had a problem on the 25th boot where it wants to check your filesystem it wouldnt do it so i skipped. On the next reboot i  was w armly welcomed to the grub rescue page. Since then i have tried a couple things to get me back into the system

1. booted up my live usb of xubuntu 12.04 tried boot-repair. rebooted nothing
2. did the grub resuce method 

set root=(hd0,1) etc etc 

with this it got me all the way into a xubunut@xubuntu terminal, not what i wanted but hey i as further to getting my system back. Tried all sorts of things here 
1.reinstalling grub to apt-get update && apt-get upgrade didnt work
2 grub-install didnt work
3 this one didnt bring up xubuntu@xubuntu bu initfrms box instead so tried mount and chroot to get into system big fail

so now as i was thinking ok i give up. The i went to the live usb again and was about to dump my home directory to and external hdd so i can pick what i wanted from it and hopefully save my songs, photos , conky config(took one hella time doing) only to find out that it was an executable and not folder ?? see picture. I was wondering what the hell happened to it and will i be able to get it back to a folder. 

edit here:-


Puling up ls -l i get this for home

-rw-rw-rw-   1 root root 17024 Feb  7  2013 home

Does this have anything to do with it as i am seeing that most directorys have a d where the first dash . So how do i go about getting that back?







[IMG]http://i174.photobucket.com/albums/w85/muted_apoc/Screenshot-09262013-015039PM.png[/IMG]

---

### Post by mut3d87 on 2013-09-27
im trying to change my folder which has turned into an executable following a e2fsck back to a folder and need to know how to do this.

After using ls -l i get the following 

-rw-rw-rw-   1 root root 17024 

Now from what i read i need to restore the d before the -rw-rw-rw-  

my question is what chmod command can i do to make this happen?

---

### Post by varunendra on 2013-09-27
> **mut3d87 said:**
> Puling up ls -l i get this for home

-rw-rw-rw-   1 root root 17024 Feb  7  2013 home

Have you tried enabling "Show Hidden files" (or whatever similar option you have) to see it is not converted (or moved) to some hidden folder? Least possible thing, I know, but just to make sure.

I tried to find similar cases with possibly some fix and only this one came up in my search that is similar to your case : [http://superuser.com/questions/401474/somehow-a-directory-got-converted-to-a-file-how-do-i-change-it-back](http://superuser.com/questions/401474/somehow-a-directory-got-converted-to-a-file-how-do-i-change-it-back)

Based on the results and some personal understanding, I think your only hope is some data recovery software, and testdisk is on top of my list of recommendations.

Doing another fsck on the partition may help, but it may also make the recovery more difficult by making changes to the file-system. So I would prefer to scan with testdisk first.

Try booting into live session, get connected to internet and install testdisk with -
```
sudo apt-get update
sudo apt-get install testdisk
```

Then run it with-
```
sudo testdisk
```
and follow the instructions here to see if it can find your lost home/data : [www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

As a precaution, the first thing I would do is to stop using the partition. For using recovery tools like above, I would use a live media and would only use the partition in read-only mode.

---

### Post by Impavidus on 2013-09-27
chmod cannot change a file into a directory. The only thing I can imagine to have happened is that somehow the directory was replaced by a file with the same name. Try file recovery software. See your other thread: [http://ubuntuforums.org/showthread.php?t=2176873&p=12800440#post12800440](http://ubuntuforums.org/showthread.php?t=2176873&p=12800440#post12800440)

Maybe someone very clever with the internals of the file system knows how to fix this manually by manipulating some flags belonging to that file, but I'm not that person.

---

### Post by mut3d87 on 2013-09-27
> **Impavidus said:**
> chmod cannot change a file into a directory. The only thing I can imagine to have happened is that somehow the directory was replaced by a file with the same name. Try file recovery software. See your other thread: [http://ubuntuforums.org/showthread.php?t=2176873&p=12800440#post12800440](http://ubuntuforums.org/showthread.php?t=2176873&p=12800440#post12800440)

Maybe someone very clever with the internals of the file system knows how to fix this manually by manipulating some flags belonging to that file, but I'm not that person.


Thanks i have just tried the other thread and had no luck, no hidden/dleted files were found.

Manipulating the filesystem seems the only way forward. Now if we could just get the attention of someone really clever to help.

---

### Post by mut3d87 on 2013-09-27
hi thanks for the response unfortunately testdisk has no hidden or deleted folders only shows that one file. 

I cant even get to files located in that directory which is the part im most annoyed about thanks for helping.

---

### Post by varunendra on 2013-09-27
Did you try "Deeper Search" ? What is the size of the partition on which your Home was/is? And what was the approximate size of the directory?

If the files 'ever' existed on that partition, then unless they have been overwritten, testdisk should be able to show them to you, even if they are corrupted and irrecoverable.

Does the current "Available space" on the partition justify the disappeared data? (if a 10 GB folder is gone, is 10 GB added to "available space"?) If not, then maybe the data has been just moved somewhere.

The last resort in my opinion would be running [PhotoRec]("www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"), which is a part of test disk. It can recover whatever is physically leftover on the partition, but won't recover filenames and directory structure. And most of the 'recovered' data would be corrupt and unusable.

---

### Post by mut3d87 on 2013-09-27
> **varunendra said:**
> Did you try "Deeper Search" ? What is the size of the partition on which your Home was/is? And what was the approximate size of the directory?

If the files 'ever' existed on that partition, then unless they have been overwritten, testdisk should be able to show them to you, even if they are corrupted and irrecoverable.

Does the current "Available space" on the partition justify the disappeared data? (if a 10 GB folder is gone, is 10 GB added to "available space"?) If not, then maybe the data has been just moved somewhere.

The last resort in my opinion would be running [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"), which is a part of test disk. It can recover whatever is physically leftover on the partition, but won't recover filenames and directory structure. And most of the 'recovered' data would be corrupt and unusable.

No i didnt try a deeper search as the partitions were found autmatically and there was no need to "go deeper" when i selected the drive it took me to the / folder and listed everything you would expect including the the /home directory which still only had -rwx-rwx-rwx- still no d at beginning  and no hidden/deleted folder in there.

The available size is definetely as if the files inside that home directory are still there 280/461GiB 181Gib free looking at Gparted which seems the correct amount. Only i have no way to getting in to it all to verify this. 

Would it be possible to make a folder and somehow trick it to believe it was the original home folder and list everything in that folder?Kind of like merging the 2. That or get the file to become directory gain which from what i gather is near on impossible.

---

### Post by matt_symes on 2013-09-27
Threads merged.

Please don't create multiple threads asking the same question.

---

### Post by matt_symes on 2013-09-27
Is there anything in the lost+found on the same partition as your home directory ?

---

### Post by varunendra on 2013-09-27
> **mut3d87 said:**
> Would it be possible to make a folder and somehow trick it to believe it was the original home folder and list everything in that folder?

Please don't even try that, at least not until all other attempts fail. Like I said before, when data is gone, the most important thing to do is to avoid 'writing' on the partition to avoid possible overwriting.

Please perform the deeper search option and check the directory listing again after it finishes. You immediately got directory listing because your partition is not corrupt or lost. So it just listed what a normal OS would list. A deeper search *may* reveal some lost data. If not, PhotoRec would be last resort.

And this part of your post looks quite significant to me -
> The available size is definetely as if the files inside that home directory are still there 280/461GiB 181Gib free looking at Gparted which seems the correct amount.
Does the OS (live one) also show the same stats about it? Does the output of "df -h" match the statement of Gparted? If yes, then try running "Disk Usage Analyzer" to see where this space is used up.

To run it as root on Ubuntu -
```
gksu baobab
```
Run it on the whole partition and see if it leads you to your lost data. In fact you should try this BEFORE testdisk, maybe it can save you a lot of time that testdisk may take in "Deeper search".

---

### Post by mut3d87 on 2013-09-27
> **matt_symes said:**
> Is there anything in the lost+found on the same partition as your home directory ?


Sorry for the 2 Diff threads. Yes theres loads of stuff in there.

[IMG]http://i174.photobucket.com/albums/w85/muted_apoc/losstFOUND.png[/IMG]

---

### Post by matt_symes on 2013-09-28
Hi

I would suggest the file in the lost+found folder are the files that were in your home directory.

Try to open then and see what they contain.

You can use the file command to see what type they are.

```
file <file_name>
``` 

Here's an example...

```
matthew-S206:/media/matthew/0110E4397709853F % file 'science/Pioneer Science_ Discovering Deep Space _ BBC Documentary'
science/Pioneer Science_ Discovering Deep Space _ BBC Documentary: ISO Media, **MPEG v4 system**, version 2
matthew-S206:/media/matthew/0110E4397709853F %


```

Try this with some of the files iin lost+found to see their type and then try to open them using the correct application for their type.

Kind regards

---

