---
title: "Back up drive full"
date: 2016-02-27
forum: General Help
---

### Post by MibunoOokami on 2016-02-27
[COLOR=#000000]I wasn't expecting to have to start another “full disk” thread so soon, especially about my back up drive.[/COLOR]
  

  [COLOR=#000000]When I went to back up my wife's PC a few moments ago, I got an error message telling me there is  no room left on my back up drive. This came as a surprise considering said drive is 1TB and both computers in the house have 320GB drives. [/COLOR] 
  

  [COLOR=#000000]Trying to keep this as short as possible, there are 3 strangely named directories on the back up drive containing a total of 207.5GB , the contents of which look suspiciously like double ups. That and I've apparently backed up 292.2GB of data from my PC despite having only used about 175GB.[/COLOR]

  [COLOR=#000000]I ran ```
sudo find / -name '*' -size +1G
``` and disappointingly only found a handful of files larger than 1GB which freed up a total of 29.16GB.[/COLOR]
  

  [COLOR=#000000]Some 18 months ago I used some type of program to fund duplicate files/directories (I can't remember the name) though I found it not very user friendly, I was having to confirm things were a duplicate before deleting them and found it excessively time consuming.[/COLOR]
  [COLOR=#000000]Basically I would like to know if there is an efficient way of confirming files are duplicates and freeing up some space on my back up drive. At the moment I'm using this [thread]("http://ubuntuforums.org/showthread.php?t=1122670") as a guide. Also if it turns out there are many duplicates taking up space, how do I stop this?[/COLOR]

  

  [COLOR=#000000]Thanks in advance for any advice.

P.S To the best of my knowledge /root is not backed up so it's unlikely to be old kernels taking up the space.
[/COLOR]

---

### Post by X-RED_Tech on 2016-02-28
What are you using to do the backup? Or how are you doing it?
Simply copying files is unlikely to have that effect.

---

### Post by MibunoOokami on 2016-02-28
> **X-RED_Tech said:**
> What are you using to do the backup? Or how are you doing it?
Simply copying files is unlikely to have that effect.

I use Rsync, which I understand has the capacity to to duplicate files and directories if you change their location on your machine. That could explain why my back up directory is almost as large as my HDD capacity, but the 3strangely named directories I mentioned, aren't even in my back up directory but do contain backed up stuff.

---

### Post by MibunoOokami on 2016-02-28
Any advice or help would be appreciated, I spent 6 hours last evening combing through 1,500 files which freed up about 10GB but is just too time consuming/inefficient.

---

### Post by X-RED_Tech on 2016-02-29
Agreed, inefficient.
Unfortunately I can't help you, I don't use rsync.

---

### Post by dragonfly41 on 2016-02-29
There is [COLOR=#2f4f4f]**FSlint**[/COLOR] in Ubuntu Software Centre which searches for duplicates.

---

### Post by mikodo on 2016-02-29
I am wondering about _*sparse files *_messing with your backup. Possibly, if you have virtual disks, like virtual-box or other applications that take advantage of sparse files such as Docker and the like, your backup app may be backing up a bunch of zeros or empty space that it doesn't recognize that it is in fact empty. If these programs are in your home like v.box again, and you are backing up your home, the backup app may not see the truly empty space and _repeatedly_ back it up.

Addendum: Take the example of rsync. The option of** rsync -S** **= --sparse       **  (*handle sparse files efficiently*). See: man rsync

See here: [https://administratosphere.wordpress.com/2008/05/23/sparse-files-what-why-and-how/](https://administratosphere.wordpress.com/2008/05/23/sparse-files-what-why-and-how/)

I can't offer any help with this. I was just reading about sparse files and thought of your problem.
  

Good Luck!

---

### Post by sudodus on 2016-02-29
You can ***synchronize*** rather than backup your system. It means that you remove files from the copy, if they were removed from the source.

***Unison*** is a tool for that purpose. Maybe it would work well for you, at least if you are careful and inspect the suggested changes before synchronizing.

I use ***unison-gtk*** for my data partition.

---

### Post by MibunoOokami on 2016-03-01
> **dragonfly41 said:**
> There is [COLOR=#2f4f4f]**FSlint**[/COLOR] in Ubuntu Software Centre which searches for duplicates.

That's the one I couldn't remember the name of, but didn't find user friendly. Having said that, I went to run it now and give it a second chance but every time I tried to launch it nothing happened. I uninstalled via software centre then reinstalled with terminal, went to launch it in Terminal and got this back.

```
~$ sudo apt-get install fslint
[sudo] password for mno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fslint
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 105 kB of archives.
After this operation, 791 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/universe fslint all 2.44-1 [105 kB]
Fetched 105 kB in 1s (86.0 kB/s)
Selecting previously unselected package fslint.
(Reading database ... 229441 files and directories currently installed.)
Preparing to unpack .../archives/fslint_2.44-1_all.deb ...
Unpacking fslint (2.44-1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up fslint (2.44-1) ...
mno@mno:~$ fslint
No command 'fslint' found, did you mean:
 Command 'nslint' from package 'nslint' (universe)
 Command 'ftlint' from package 'freetype2-demos' (universe)
fslint: command not found
```

I added the who install output for reference.

> **mikodo said:**
> I am wondering about _*sparse files *_messing with your backup. Possibly, if you have virtual disks, like virtual-box or other applications that take advantage of sparse files such as Docker and the like, your backup app may be backing up a bunch of zeros or empty space that it doesn't recognize that it is in fact empty. If these programs are in your home like v.box again, and you are backing up your home, the backup app may not see the truly empty space and _repeatedly_ back it up.

Addendum: Take the example of rsync. The option of** rsync -S** **= --sparse       **  (*handle sparse files efficiently*). See: man rsync

I'll look into that as I did give Virtual Box a try out a few years back but not sure I uninstalled it. I just checked my script to see if that was a command I added a while back, I haven't so will add that. Incidentally, I notice rsync should be backing up ~/ which should be root, but is only copying /home, is that normal? The reason I ask is I ran into a small glitch a few days ago where a back up of the root directory really would have come in handy.

> **sudodus said:**
> You can ***synchronize*** rather than backup your system. It means that you remove files from the copy, if they were removed from the source.

***Unison*** is a tool for that purpose. Maybe it would work well for you, at least if you are careful and inspect the suggested changes before synchronizing.

I use ***unison-gtk*** for my data partition.

That sounds interesting and I'll definitely look into it.

---

### Post by sudodus on 2016-03-01
> I notice rsync should be backing up ~/ which should be root, but is only copying /home, is that normal? 

~ is the current home, $HOME, so rsync does what you tell it to do. / (only /) is the file system root.

---

### Post by MibunoOokami on 2016-03-01
I've just learned that some of the backed up stuff is from my browser cache which is very interesting/concerning as that is in my excludes list and when I run rsync cache is definitely skipped, so...

> **mikodo said:**
> I am wondering about _*sparse files *_messing with your backup. 
I can't offer any help with this. I was just reading about sparse files and thought of your problem.
Good Luck!

Actually you may very well have helped more than you think. If I understand what I read on the website you linked, I have some sparsing issues. For example, when I entered the command ```
ls -ls
``` I apparently have something that has 4 blocks but uses 42 or the most ludicrous, 11232 blocks but 11500973. My understanding is that the number on the left hand side represents the number of blocks and the next number before the date is how many blocks are (actually?) being used. Please correct me if I'm mistaken.

---

### Post by MibunoOokami on 2016-03-01
> **sudodus said:**
> ~ is the current home, $HOME, so rsync does what you tell it to do. / (only /) is the file system root.

Thanks for clarifying that for me. I'm just remembering back to when I first started using rsync and I think I was advised only to back up /home, so that makes 100% sense about ~/.

---

### Post by dragonfly41 on 2016-03-01
In fact fslint launches from command **fslint-gui**

FSlint GUI also launches from System Tools > FSlint

---

### Post by oldfred on 2016-03-01
I have used Meld Diff viewer. I think it took a long time to find all files.

I do not back up /, but back up /home and my data partitions. I assume I will just reinstall. I so have some files in /etc that I edit, but copy those into /home manually. Then I do not have to backup /etc. But if a server or running server apps or data base apps then may also be in / and need backing up.

---

### Post by MibunoOokami on 2016-03-01
Just to double check, sparsed files means my "full" 1TB back up drive  could very well have 100 or so GB free but the sparsing makes rsync  think the drive is full?

> **dragonfly41 said:**
> In fact fslint launches from command **fslint-gui**

FSlint GUI also launches from System Tools > FSlint

Thanks, that got it running.


> **oldfred said:**
> I have used Meld Diff viewer. I think it took a long time to find all files.


I'll check that one out too. Thanks oldfred.

---

### Post by mikodo on 2016-03-01
> **MibunoOokami said:**
> Just to double check, sparsed files means my "full" 1TB back up drive  could very well have 100 or so GB free but the sparsing makes rsync  think the drive is full?.
Yes. If you mean that rsync is backing up all the sparce files. Are you blocked from running rsync completely because of the full backup drive? Try the backup with rsync -S on it if you can or, try with another backup drive to, see what you get.

I am only guessing but, I think as the size of the "real & actual" free space in the sparced files changes with data being written to it by an app then, rsync may copy what it sees as newer files too, creating more backup data supposedly being backed up.  But, it doesn't matter about my hypothesis. If it looks like sparce files are the culprit, you'll need to do some more reading somewhere on how to deal with it. I only read that page and linked it to you.

I have a rsync archive backup of my data partition that supposedly holds ~38 GiB of data. It seems to be pretty much in conjunction with what I have on my actual data partition. I too haven't been using the -S option with rsync. If I understand you correctly, I see none of the huge numbers that you see. That may signify much "supposed" data that is written to your backup drive. So, maybe it is a sparce file problem for you. 

The numbers just before the dates I think, only signifies the typical bytes per sector or, so it appears. I am not sure what is up with my lost+found but, it is everywhere where data is written I believe.
```
mikodo@mikodo:~$ cd /media/mikodo/FlashBackup2
mikodo@mikodo:/media/mikodo/FlashBackup2$  ls -ls
total 32
 4 drwxrwxrwx 23 mikodo mikodo  4096 Feb 18 19:17 Documents
16 drwxrwxrwx  2 root   root   16384 Sep 18 17:01 lost+found
 4 drwxrwxrwx 53 mikodo mikodo  4096 Oct 11 01:15 Music
 4 drwxrwxr-x  3 mikodo mikodo  4096 Jan 11 00:09 PDF_Books
 4 drwxrwxrwx  2 mikodo mikodo  4096 Dec 20 16:43 Pictures 
```
Hopefully, some people who know what this is all about will, come in and correct me and give you the definitive answers and the help you need.

Good luck!

---

### Post by dragonfly41 on 2016-03-02
Another article to check ... re: inodes ...

[http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)

---

### Post by MibunoOokami on 2016-03-03
It seems that the cause of my back up drive becoming full is primarily due to sparse files, followed by duplicates. When I import videos to my PC it looks as though they are being saved to more than 1 directory, as per the info below, but I don't know why.
 
```
/home/mno/Pictures/GT-I9000_20140227070727/Video/DCIM/Camera/video-2014-02-26-16-07-45.mp4
/home/mno/i9000/DCIM/Camera/video-2014-02-26-16-07-45.mp4
/home/mno/i9000/Videos/video-2014-02-26-16-07-45.mp4
```

Based on that I'm going to mark this thread as solved. Thank you to everyone who offered some advice.

---

