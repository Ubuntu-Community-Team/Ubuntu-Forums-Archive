---
title: "A Matching Cleaning And Backup Tool?"
date: 2020-04-22
forum: General Help
---

### Post by wyattwhiteeagle on 2020-04-22
I'm looking for something that is simple, light-weight, easy to understand and use, that...


* Can clean not only those areas which the built-ins clean, but also those areas which the built-ins doesn't.


* Can backup...
--Files and folders.
--System custom settings.
--Applications and custom settings. (Including Wine, PlayOnLinux and *.exe apps)


* Can create restore points on the main hard drive.
* Doesn't use any cloud.
* Can create a bootable USB flashdrive (seperate from the clean install USB drive.)


While this may require more than one software application, I'm hoping there is just one that matches up.
If there is no such thing, please include the software's that do match.


Any idea's?

---

### Post by HermanAB on 2020-04-23
Hmm, this is perhaps one of those 'Linux isn't Windows' type of requests.  

Linux doesn't dirty its environment - it has a /tmp folder for transient files and a /var/log directory controlled by a process called logrotate to manage it, for log files.

There are several backup utilities and the last thing Linux needs, is another one.  Most of them use a program called rsync underneath.  Rsync is easy to use directly with a home-brew script and most front ends make it more difficult and confusing, instead of better.

Maybe read this: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by wyattwhiteeagle on 2020-04-23
> **HermanAB said:**
> Hmm, this is perhaps one of those 'Linux isn't Windows' type of requests.  

Linux doesn't dirty its environment - it has a /tmp folder for transient files and a /var/log directory controlled by a process called logrotate to manage it, for log files.

There are several backup utilities and the last thing Linux needs, is another one.  Most of them use a program called rsync underneath.  Rsync is easy to use directly with a home-brew script and most front ends make it more difficult and confusing, instead of better.

Maybe read this: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

Thank you. I will have a read :)

I'm not wanting to clutter up with a bunch of Microsoft Apps.
I plan to stay as Ubuntu as possible. 
There is, so far, only one that I use on a daily basis that requires Wine and something like PlayOnLinux.
Those aren't even installed right now.

---

### Post by wyattwhiteeagle on 2020-04-23
> **HermanAB said:**
> Hmm, this is perhaps one of those 'Linux isn't Windows' type of requests.  

Linux doesn't dirty its environment - it has a /tmp folder for transient files and a /var/log directory controlled by a process called logrotate to manage it, for log files.

There are several backup utilities and the last thing Linux needs, is another one.  Most of them use a program called rsync underneath.  Rsync is easy to use directly with a home-brew script and most front ends make it more difficult and confusing, instead of better.

Maybe read this: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

WOW!!!

The post at that link seems pretty AWESOME!!! [IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG] Thank you for sharing.

Mr. Rubel's info makes putting together something so simple look very tasking and very scary. I'm certain the fruits of that labor are very rewarding.

Though it seems tasking and scary, it looks like that script is a very similar example of what I asked for. 
I had no clue what exactly I was looking for.
I honestly believed I would have to compile a bunch of programs and applications just to accomplish a good system backup and restore strategy.

It leads me to some question's though.

In the script, it looks like Muzak is a device and the digits seem to be the protocol address for that device.

Am I able to specify a USB flashdrive attached to my system instead of another device over a network?

Do I use sudo in the terminal to run the script?

Is a bash file script conceptually the same as a batch file in Windows?

The folders and files next to all the "includes" and "excludes", what are the directories of those files and folders?
Are those directories specified in the script just above that part?

---

### Post by oldfred on 2020-04-23
I have multiple scripts.
I have a cleanup script that both updates system & housecleans.
I have an rsync script in every flash drive & label each separately, so I do have to do minor edit for each. Several times a year I sneakernet that data to another system in another state. (I am retired).
I have a cron task to copy data from SSD to HDD. Not really backup as not versioned as link above does with rsync.

Having seen all the posts by TheFu, I am planning on converting my rsync to HDD to rdiff.

[https://rdiff-backup.net/](https://rdiff-backup.net/)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2440020](https://ubuntuforums.org/showthread.php?t=2440020)
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/--delete](http://www.kirya.net/articles/backups-using-rdiff-backup/--delete) 
Sample rdiff file by TheFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
Summary report from rdiff & use variables, example
[https://ubuntuforums.org/showthread.php?t=2422831](https://ubuntuforums.org/showthread.php?t=2422831)
[http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
rdiff-backup for non-media files that need to be versioned.
rsync for media files that don't change. add par2 files for  bitrot 
[https://ubuntuforums.org/showthread.php?t=2432229](https://ubuntuforums.org/showthread.php?t=2432229)

Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

