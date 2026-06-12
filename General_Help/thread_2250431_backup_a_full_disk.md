---
title: "backup a full disk"
date: 2014-10-28
forum: General Help
---

### Post by rbmoler on 2014-10-28
I have used Dir Sync Pro as my go to backup for all the folders and files on my ntfs *data *disk for the past several years before I switched to Ubuntu.  That separate *data* disk contains my Thunderbird and Firefox profiles along with just about every single file that I've generated in LibreOffice,all my pictures and videos, videos and files downloaded from the internet, and most everything except the operating system, and program files.  (I became a little paranoid from experience with windows NT, XP and 7.)  Everything from that disk is backed up to a ntfs USB disk.  I have Dir Sync Pro set up to synchronize the *data *disk and the USB disk periodically.  It has saved my bacon a few times.  Since I'm dual booted I can do what I need by booting up in Win7 once a week and do the backup, but I'd like to get out of using it.  Also, Ubuntu baulks at running Dir Sync pro.  It's not an acceptable program if I try to run the jar file.  (Didn't try it in a terminal, but I expect it would be blocked there too.)

I cannot find a comparable program to do this (to me) essential task.  All of the Ubuntu programs that I've investigated appear to work only on folders.  Unity seems to require that a folder be specified.  Is there a program comparable to Dir Sync Pro for Ubuntu?

---

### Post by bab1 on 2014-10-28
> **rbmoler said:**
> ... Ubuntu baulks at running Dir Sync pro.  It's not an acceptable program if I try to run the jar file.  (Didn't try it in a terminal, but I expect it would be blocked there too.)

Is OpenJDK Java installed?
> 
I cannot find a comparable program to do this (to me) essential task.  All of the Ubuntu programs that I've investigated appear to work only on folders.  Unity seems to require that a folder be specified.  Is there a program comparable to Dir Sync Pro for Ubuntu?

Why try and find something else when DirSync itself says their app runs on Linux.  See below > [COLOR="#0000FF"]DirSync Pro is programmed completely in platform independent Java™ so it can be run under nearly every modern operating system including Windows™, Linux™ and Macintosh™. [/COLOR]

If it runs on Java is should run on OpenJDK Java which is available in the Ubuntu repos.

---

### Post by rbmoler on 2014-10-29
I have OpenJDK Java installed.  That is not the problem. I would not have considered DirSyncPro if it had not had a linux version.   I did indeed download the linux version of the program with the expectation that it would run. I specifically noted the need for Java and took care of that. DirSyncPro is present in my download folder.  When I try to run the Dirsync.jar program I get a message from Ubuntu that says that the "bit" that would be there if it were an approved program is not present and it will not allow the program to run under Java.

Perhaps I've overlooked something.  That's not an unlikely possibility.

---

### Post by bab1 on 2014-10-29
> **rbmoler said:**
> I have OpenJDK Java installed.  That is not the problem. I would not have considered DirSyncPro if it had not had a linux version.   I did indeed download the linux version of the program with the expectation that it would run. I specifically noted the need for Java and took care of that. DirSyncPro is present in my download folder.  When I try to run the Dirsync.jar program I get a message from Ubuntu that says that the "bit" that would be there if it were an approved program is not present and it will not allow the program to run under Java..

For us that have never seen the "bit", what does the message *exactly *say.  I run Java apps that are not in any Ubuntu repo with no problems.

---

### Post by oldfred on 2014-10-29
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

I just use rsync. Some suggest grsync.

When I was backing up XP in Windows, it took me a while to learn where my data was stored. Some apps would store data by default in the app folder, some in Documents and some in other places. But I eventually found all of them and used my own .bat script and copy commands.

So now I use rsync, primarily /home, but some data from my data partitions to another drive. I also then use rsync to copy to my laptop and to flash drives.


 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)

I used this as my starting point:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by rbmoler on 2014-10-30
When I attempt to run "dirsyncpro.jar" a pop-up window appears with the following header "Blocked:/usr/bin/java -jar"

The message in the window reads:

"The file '/home/robert/.cache/xx-xxxxxx/DirSyncPro -1.50-Linux/dirsyncpro.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the [COLOR=#ff0000]executable.bit[/COLOR]."

The information regarding the "executable.bit" is that if it is not present Ubuntu will not allow the software to run for my own protection.  I downloaded Dir Sync Pro from source forge which, I must presume, is no longer a trusted source.

I understand that if I actually knew the procedure I could alter the permissions for the .jar file and make it executable and use it at my own risk.  I am loath to go that route.

If no-one has a reasonably simple solution for what I want to do, then I'll close this thread and revert to my default of doing what I need through win7.

---

### Post by bab1 on 2014-10-30
> **rbmoler said:**
> When I attempt to run "dirsyncpro.jar" a pop-up window appears with the following header "Blocked:/usr/bin/java -jar"

The message in the window reads:

"The file '/home/robert/.cache/xx-xxxxxx/DirSyncPro -1.50-Linux/dirsyncpro.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the [COLOR=#ff0000]executable.bit[/COLOR][COLOR=#ff0000][/COLOR]."
The file you are trying to run is at```
home/robert/.cache/xx-xxxxxx/DirSyncPro -1.50-Linux/dirsyncpro.jar'
```

This file needs to have the eXecute bit set.  You should move the file to a more permanent location.  I have my Java app in ~/bin/<javaapp> (where <javaapp> is the name of the app and ~/ means /home/<my-home>/bin .  You could then set the file to executable with this comand ```

chmod ug+x ~/bin/<javaapp>

```
The bottom line is: Setting the the application file to eXecutable is what allows it to run

---

### Post by bab1 on 2014-10-30
> The information regarding the "executable.bit" is that if it is not present Ubuntu will not allow the software to run for my own protection. I downloaded Dir Sync Pro from source forge which, I must presume, is no longer a trusted source.

Not so at all.  Linux itself is designed to only execute apps that have the execute bit set.  It's just he way it works.  The message is just saying: This app needs to have the execute bit set by you; are you sure you want to do that?  The only Ubuntu trusted source is Ubuntu's own repos.  All PPA's and external applications to that have not been vetted by Ubuntu developers or maintainers.
> 
I understand that if I actually knew the procedure I could alter the permissions for the .jar file and make it executable and use it at my own risk. I am loath to go that route.Obviously you have been using the application (running under windows) so you know it works.  What better vetting do you need?  You can always ask how to set the app up and follow the instructions of somebody who does know.  In the end it is your decision to do as you please.

---

