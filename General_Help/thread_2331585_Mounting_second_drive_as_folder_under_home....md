---
title: "Mounting second drive as folder under /home..."
date: 2016-07-23
forum: General Help
---

### Post by wolfsong73 on 2016-07-23
Hello everyone.


Posting here in hopes I can get some assistance, or maybe a nod in the correct direction.


I'm moving over to Linux from Windows, and am looking to recreate my Windows setup on Linux.


My current setup on Windows is:
C:\ - 128GB SSD -- Contains OS and any apps/games that I want to take advantage of the SSD's read/write speed.
E:\ - 1TB HDD -- Contains other apps/games, as well as data and other stuff.


Now, of course, because Windows basically "doesn't care" where you install stuff (for the most part), that setup "just works".


My understanding, however, is that things are a bit different in Linux land, and that where software is installed does matter. To my understanding, it has to be under the /home partition, and there can only be one of them. 

The conundrum I'm faced with is:
If I put /home on the SSD, I'm limiting myself to ~100GB for apps/games.
If I put /home on the HDD, I'm wasting all that high-speed space on the SSD.


I'm trying to find a setup where I needn't choose "one or the other", but can "have my cake and eat it, too".


In my searching, I found a post discussing how you can mount a drive as a folder under /home. So, as I understand it, I could basically mount my HDD as /1TBDrive, or something like that, giving me /home/1TBDrive.

Now, my question is, would that effectively be recognized as part of the /home partition as far as Linux is concerned? Could I then use that space (in 1TBDrive) to install apps and games and such, and Linux will recognize and run them without issue?


If so, then my problem is solved, and I know there's a fstab command that has to be edited in to do that (again, per my searches).


However, I might well be barking completely up the wrong tree here. If so, please let me know. Perhaps, point me in the direction of a setup that would accomplish what I'm trying to do. 


I'm sure there's a way, I'm just not quite familiar enough with Linux, yet, to know what it is.


Thanks in advance for your time and help! Much appreciated.


~Mike

---

### Post by Dennis N on 2016-07-23
If you install software from the ubuntu repositories, or software packaged in a .deb file, you have no control over where it is installed - there are standard locations for software applications outside your home directory such as /usr/bin and /usr/sbin. This is controlled by information in its .deb package files.

Software without a .deb file (or other installer) that you might download, such as many games, can be placed in your home folder. I have a games subfolder under home for such items. If you want these accessible to other users, don't put them inside home, but use /opt instead.

---

### Post by oldfred on 2016-07-23
I create a /mnt/data mount point,to a partition on HDD and copy all folders like Documents, Music, Videos etc (and a few others). Then I edit fstab with /mnt/data and partition on HDD. And link all the folders into /home. It then looks like standard install, but actual data is on HDD.

I have multiple installs as I have installed 16.10 (maybe more than once). I keep all system partitions at about 25GB, but have large /mnt/data partition on HDD.
And after manually editing fstab with same entry, manually deleting new empty folders, and linking in the same folders many times, I just copied commands in terminal into a script. But had to learn how to do it manually first, so I knew what I did. MY first copy to script had lots of incorrect commands, typos to edit out, etc. And over time I was able to add a few features to make it better. But it is unique to my configuration.

Basically I do these after creating a large ext4 partition on HDD:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 
    
       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by wolfsong73 on 2016-07-23
Hi, Dennis,

Yes, my main concern is being able to install games and software from discs, or otherwise not from the repositories. I don't worry about things from repositories as I know Linux deals with that.

I think I may have done a poor job explaining my question/situation, as none of the replies so far are really addressing it. 

I've seen a suggestion elsewhere that you can mount a separate/second hard drive as a folder in your /home partition.

Here's what I'm asking about, boiled down:

1. /home is mounted on the 128GB SSD
2. I mount a second 1TB HDD as a *folder* under */home, *naming it 1TBDrive (for the sake of example). 
So, the path to that drive would effectively be /home/1TBDrive.

With that setup, is Linux going to recognize the 1TBDrive as a part of the /home partition, so I can create a Games folder, etc as I would ordinarily?

---

### Post by Dennis N on 2016-07-23
> With that setup, is Linux going to recognize the 1TBDrive as a part of the /home partition, so I can create a Games folder, etc as I would ordinarily?

That would work, yes. You would then have ~/1TBDrive/Games/

---

### Post by Keith_Helms on 2016-07-23
You can mount the second drive anywhere and then set up a home directory as a symbolic link to that mountpoint or a folder within the mountpoint.  For example, I have my second drive mounted to /homedata and within my home directory I have the documents, downloads, and other directories set up as symbolic links to directories under /homedata.  Here's an excerpt from **ls -l** run in my home directory:

```
lrwxrwxrwx 1 keith keith      22 Apr 28 15:35 bin -> /homedata/homedirs/bin
lrwxrwxrwx 1 keith keith      23 Apr 28 15:35 data -> /homedata/homedirs/data
lrwxrwxrwx 1 keith keith      28 Apr 28 15:35 documents -> /homedata/homedirs/documents
lrwxrwxrwx 1 keith keith      27 Apr 28 15:35 dosdrive -> /homedata/homedirs/dosdrive
lrwxrwxrwx 1 keith keith      27 Apr 28 15:35 download -> /homedata/homedirs/download
```

This lets me share these directories between multiple boot partitions running multiple versions of Ubuntu.  If you're wondering, I added that extra directory level of "homedirs" so I can sync those directories between laptop and desktop systems with a single command.

---

### Post by ajgreeny on 2016-07-23
If that 1TB drive is formatted to a Windows filesystem, which I think it will be if you're using files on it in Windows as well as Ubuntu, you could run into problems with any executable files for these games that you want to install as the necessary Linux permissions will not be understood on a NTFS filesystem, and such files may no longer be executable by Ubuntu.

---

### Post by wolfsong73 on 2016-07-23
> **ajgreeny said:**
> If that 1TB drive is formatted to a Windows filesystem, which I think it will be if you're using files on it in Windows as well as Ubuntu, you could run into problems with any executable files for these games that you want to install as the necessary Linux permissions will not be understood on a NTFS filesystem, and such files may no longer be executable by Ubuntu.

Hello,

Nah, I'm not going to be keeping the Windows system. I'm wiping both drives clean and starting from scratch. All my most important data (stuff I can't replace, etc) is on an external USB drive, and/or saved on a dropbox folder. So, I'm going to be working only with Linux once I do the switch over.

---

### Post by wolfsong73 on 2016-07-23
I see. So as long as the link exists within the /home partition it's going to treat its target as part of the /home partition, even if it's on a physically different drive, then? Do I have that right?

---

### Post by oldfred on 2016-07-23
Yes, it just depends on how you mount it or link it what the exact path will be to where the data really is.
You can directly mount partition in /home.
You can mount in /mnt/data and link folders into /home.
Examples of both are above.

---

### Post by wolfsong73 on 2016-07-23
Okay, I think I've got it. I also checked out the post #6 on the other thread linked, and I think those templates are going to be very helpful. 

Thanks again for the help! So long as I'm able to install games and apps to that "1TBDrive" partition/folder, and run them without issue, I think I'm set.

Thanks for all the help, folks!

---

