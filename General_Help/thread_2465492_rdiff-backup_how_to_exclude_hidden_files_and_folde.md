---
title: "rdiff-backup: how to exclude hidden files and folders ?"
date: 2021-08-03
forum: General Help
---

### Post by freeflyjohn on 2021-08-03
I am using rdiff-backup to backup my Mac home folder to my Ubuntu server.

I am trying to exclude hidden files and folders (i.e. starting with a '.') using the --exclude-filelist option and specifying a text file.
 
For testing purposes I have created these dummy folders (i.e. empty) and files on the Mac in /Users/myname/rdiff_test/source...


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288913&stc=1[/IMG]

The paths specified in the rdiff-backup command are:

[INDENT]EXCLUDE LIST: /Users/myname/.rdiff-backup/exclude_list.txt[/INDENT]
[INDENT]SOURCE: /Users/myname/rdiff_test/source[/INDENT]
[INDENT]DESTINATION: /Users/myname/rdiff_test/backup[/INDENT]

The rdiff-backup command I run is:

```


rdiff-backup --exclude-filelist  /Users/myname/.rdiff-backup/exclude_list.txt /Users/myname/rdiff_test/source /Users/myname/rdiff_test/backup


```

The file exclude_list.txt contains:

```

/Users/myname/rdiff_test/source/*.Trash
/Users/myname/rdiff_test/source/*.AppleDouble
/Users/myname/rdiff_test/source/*$RECYCLE.BIN
/Users/myname/rdiff_test/source/*.ini
/Users/myname/rdiff_test/source/.*
/Users/myname/rdiff_test/source/iperf3
/Users/myname/rdiff_test/source/Applications
/Users/myname/rdiff_test/source/Applications (Parallels)
+ /Users/myname/rdiff_test/source/Desktop
/Users/myname/rdiff_test/source/Documents/Microsoft User Data
+ /Users/myname/rdiff_test/source/Documents
/Users/myname/rdiff_test/source/Downloads/svn
+ /Users/myname/rdiff_test/source/Downloads
/Users/myname/rdiff_test/source/Library
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
/Users/myname/rdiff_test/source/Nextcloud
+ /Users/myname/rdiff_test/source/Pictures 
/Users/myname/rdiff_test/source/rdiff_test
/Users/myname/rdiff_test/source/Trash
/Users/myname/rdiff_test/source/Parallels

```

I was hoping the following line would have excluded the hidden files and folders but it hasn't:

```

/Users/myname/rdiff_test/source/.*

```

What's the syntax required in the exclude file list to exclude these hidden folders and files ?

---

### Post by GhX6GZMB on 2021-08-03
From the man page, I'd say you need to use --exclude-globbing-filelist instead of just --exclude-filelist in your command.

---

### Post by TheFu on 2021-08-03
So, I tried to answer with my guess and the forum software is blocking it. Sorry.

I've never used --exclude-filelist.  I work from the opposite method.  Exclude everything, then specifically include the stuff I want.
Also, I **pull** backups, never **push** them for security reasons.
```
 rdiff-backup --exclude-special-files  \
               client-hostname::/home/username /backup/client
 rdiff-backup --remove-older-than 90d --force \
               /backup/client
```
is the basic "pull" method.

For backing up systems that can be restored to a fresh install, things are a little more complex, some setup is required to put the system data into places included in the backup and to setup a backup userid that is root-equivalent, but the rdiff-backup commands look like this:
```
sudo rdiff-backup
       --exclude-special-files \
       --exclude '**/.cache/mozilla' \
       --exclude '**/.cache/chromium' \
       --include /usr/local --include /etc --include /home --include /root \
       --exclude '**'   backup3288@${remote-machine}::/ \ 
       /Backups/${remote-machine}

sudo  rdiff-backup --remove-older-than 90d --force        /Backups/${remote-machine}
```

The order of the include/excludes matters in the precedence.

I know ZERO about OSX besides generalities. Had an OSX machine for a few weeks and before it was smashed against the wall over frustration, I gave it to a coworker.

---

### Post by freeflyjohn on 2021-08-04
> **TheFu said:**
> 
Also, I **pull** backups, never **push** them for security reasons.
```
 rdiff-backup --exclude-special-files  \
               client-hostname::/home/username /backup/client
 rdiff-backup --remove-older-than 90d --force \
               /backup/client
```
is the basic "pull" method.


Thanks TheFu

Just to clarify, I am only 'testing' rdiff-backup on the Mac, using local source and destination folders, simply to get the syntax correct for excluding files.

Once I get the syntax correct, I will be pulling a backup of the Mac from the server (via SSH) by running this command from the server:

```

rdiff-backup -v5 --exclude-filelist ~/.rdiff-backup/exclude_list.txt myname@macbookpro.fritz.box::/Users/myname /media/storage/Backup/Mac/rdiff-backup/myname

```

rdiff-backup took about 14 hours to backup 680Gb from the Mac when I first ran this command from the server, but the exclude options did not work correctly.

This is why I am testing locally on the Mac first and using empty folders as it takes seconds to test whether the exclude options work or not.

I am not interested in backing up system files, just personal data.

---

### Post by freeflyjohn on 2021-08-04
> **ml9104 said:**
> From the man page, I'd say you need to use --exclude-globbing-filelist instead of just --exclude-filelist in your command.

Thanks ml9104

I did initially use the --exclude-globbing-filelist option when I performed the first backup using the following:

```


**.Spotlight
**.Trash
**.AppleDouble
**$RECYCLE.BIN
**.ini
**/.*
**iperf3
**/Applications
**/Applications\ (Parallels)
+ **/Desktop
**/Documents/Microsoft User Data
**/Documents/Parallels
+ **/Documents
**/Downloads/svn
+ **/Downloads
**/Library
+ **/Movies
+ **/Music
**/Nextcloud
**/Parallels
+ **/Pictures
**/Public
**/Trash


```

It correctly excluded the hidden files and folders, but it excluded _any_ folder called 'Applications'.

I only wanted to exclude the one folder called 'Applications' at the top level in the users home folder to be excluded, not every single folder called 'Applications' !

For example, here is the source which has a folder called 'Applications' in the 'Pictures' folder:


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288922&stc=1[/IMG]

And here is the backup, where the 'Applications' folder in the 'Pictures' folder has not been copied (when I want it to be included):

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288923&stc=1[/IMG]


This is the only 'Applications' folder I want to be excluded, not any other folders by the same name:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288924&stc=1[/IMG]


This is why I tried the --exclude-filelist option in the hope I could explicitly exclude flles and folders using full paths (like I used to do with rsycn).

I don't quite understand this globbing syntax, its all new to me.

---

### Post by TheFu on 2021-08-04
**/Applications

matches any parent directories with 'Applications' in the name.  The '**' says to match any number of parent directories - 1, 2, 3, 200, 900 .... doesn't matter.

---

### Post by freeflyjohn on 2021-08-04
> **TheFu said:**
> **/Applications

matches any parent directories with 'Applications' in the name.  The '**' says to match any number of parent directories - 1, 2, 3, 200, 900 .... doesn't matter.

So how do I resolve this ?

If I use the --exclude-filelist option I can define the following so it only excludes the 'Applications' folder at the top level which I want to exclude...

```

/Users/myname/rdiff_test/source/Applications

```

But then I cant seem to use the --exclude-filelist option to exclude the hidden files and folders at the top level.

So how do I use the --exclude-globbing-filelist option to only exclude only the 'Applications' folder at the top level, not every single folder called 'Applications' ?

---

### Post by freeflyjohn on 2021-08-04
Think I've solved it.

I can define absolute paths for the folders I want to include/exclude as shown below and this seems to work !

```

**.Spotlight
**.Trash
**.AppleDouble
**$RECYCLE.BIN
**.ini
/Users/myname/rdiff_test/source/.*
/Users/myname/rdiff_test/source/iperf3
/Users/myname/rdiff_test/source/Applications
/Users/myname/rdiff_test/source/Applications (Parallels)
+ /Users/myname/rdiff_test/source/Desktop
/Users/myname/rdiff_test/source/Documents/Microsoft User Data
/Users/myname/rdiff_test/source/Documents/Parallels
+ /Users/myname/rdiff_test/source/Documents
/Users/myname/rdiff_test/source/Downloads/svn
+ /Users/myname/rdiff_test/source/Downloads
/Users/myname/rdiff_test/source/Library
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
/Users/myname/rdiff_test/source/Nextcloud
/Users/myname/rdiff_test/source/Parallels
+ /Users/myname/rdiff_test/source/Pictures
/Users/myname/rdiff_test/source/Public
/Users/myname/rdiff_test/source/Trash



```

---

### Post by freeflyjohn on 2021-08-04
I'm so confused by this exclude list because the moment I change the order of any of the lines, depending on the order it either includes everything or excludes everything.

At the moment it seems to work correctly if the order is as shown below:

```

**.Spotlight
**.Trash
**.AppleDouble
**$RECYCLE.BIN
**.ini
/Users/myname/rdiff_test/source/.*
/Users/myname/rdiff_test/source/iperf3
/Users/myname/rdiff_test/source/Applications
/Users/myname/rdiff_test/source/Applications (Parallels)
+ /Users/myname/rdiff_test/source/Desktop
/Users/myname/rdiff_test/source/Documents/Microsoft User Data
/Users/myname/rdiff_test/source/Documents/Parallels
+ /Users/myname/rdiff_test/source/Documents
/Users/myname/rdiff_test/source/Downloads/svn
+ /Users/myname/rdiff_test/source/Downloads
/Users/myname/rdiff_test/source/Library
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
/Users/myname/rdiff_test/source/Nextcloud
/Users/myname/rdiff_test/source/Parallels
+ /Users/myname/rdiff_test/source/Pictures
/Users/myname/rdiff_test/source/Public
/Users/myname/rdiff_test/source/Trash

```

But if the order is changed as shown below, it includes everything:

```

**.AppleDouble
**.ini
**.Spotlight
**.Trash
**$RECYCLE.BIN
/Users/myname/rdiff_test/source/.*
/Users/myname/rdiff_test/source/Applications
/Users/myname/rdiff_test/source/Applications (Parallels)
/Users/myname/rdiff_test/source/Documents/Microsoft User Data
/Users/myname/rdiff_test/source/Documents/Parallels
/Users/myname/rdiff_test/source/Downloads/svn
/Users/myname/rdiff_test/source/iperf3
/Users/myname/rdiff_test/source/Library
/Users/myname/rdiff_test/source/Nextcloud
/Users/myname/rdiff_test/source/Parallels
/Users/myname/rdiff_test/source/Public
/Users/myname/rdiff_test/source/Trash
+ /Users/myname/rdiff_test/source/Desktop
+ /Users/myname/rdiff_test/source/Documents
+ /Users/myname/rdiff_test/source/Downloads
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
+ /Users/myname/rdiff_test/source/Pictures

```

The same applies if its changed to the order below:

```

+ /Users/myname/rdiff_test/source/Desktop
+ /Users/myname/rdiff_test/source/Documents
+ /Users/myname/rdiff_test/source/Downloads
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
+ /Users/myname/rdiff_test/source/Pictures
**.AppleDouble
**.ini
**.Spotlight
**.Trash
**$RECYCLE.BIN
/Users/myname/rdiff_test/source/.*
/Users/myname/rdiff_test/source/Applications
/Users/myname/rdiff_test/source/Applications (Parallels)
/Users/myname/rdiff_test/source/Documents/Microsoft User Data
/Users/myname/rdiff_test/source/Documents/Parallels
/Users/myname/rdiff_test/source/Downloads/svn
/Users/myname/rdiff_test/source/iperf3
/Users/myname/rdiff_test/source/Library
/Users/myname/rdiff_test/source/Nextcloud
/Users/myname/rdiff_test/source/Parallels
/Users/myname/rdiff_test/source/Public
/Users/myname/rdiff_test/source/Trash

```

It makes absolutely no sense how the change in order completely breaks the exclude function ???

I know TheFu said 'the order of the include/excludes matters in the precedence' which is why I tried moving the + lines at the top and at the bottom, but it made no difference.

I'm getting extremely frustrated with rdiff-backup and seriously beginning to dislike it, purely down to these exclude issues.  It doesn't help that the manual is poor ([https://rdiff-backup.net/docs/rdiff-backup.1.html](https://rdiff-backup.net/docs/rdiff-backup.1.html))

For example, in the manual it states there is an option called "--exclude-special-files", but there is no explanation anywhere in the manual as to what this option does.

I might go back to using rsync at this rate because with rdiff-backup I have no confidence its including and excluding the correct files and folders.

At least with rsync its straight forward to include and exclude files and folders, unlike rdiff-backup

---

### Post by TheFu on 2021-08-04
From the manpage:

```
       --exclude-special-files
              Exclude all device files, fifo files, socket  files,  and  sym&#8208;
              bolic links.
```
If that isn't clear, then you are lacking some basic knowledge.  It is extremely clear to administrators.

What manual are you using if not the manpage on your system, for the exact version of rdiff-backup being used?  The local manpage should be the primary source of information for every command.

I've already said to *exclude* everything and *include* what you want backed up.  For some reason you've decided to reject that idea. Good luck.

---

### Post by freeflyjohn on 2021-08-04
> **TheFu said:**
> From the manpage:

```
       --exclude-special-files
              Exclude all device files, fifo files, socket  files,  and  sym&#8208;
              bolic links.
```
If that isn't clear, then you are lacking some basic knowledge.  It is extremely clear to administrators.

What manual are you using if not the manpage on your system, for the exact version of rdiff-backup being used?  The local manpage should be the primary source of information for every command.

I've already said to *exclude* everything and *include* what you want backed up.  For some reason you've decided to reject that idea. Good luck.

Your'e correct, I'm not a Linux server expert, my server is mainly for storing large amounts of data (which would otherwise be too large to fit on a laptop), in addition to a Plex Media Server and Nextcloud. I've also implemented other things such as SSH with keys and remote desktop with NoMachine.  The only other thing I would like to add is backups.

I have no idea what fifo and socket files are and when I looked into symlinks I got confused by soft and hard symlinks (I'm used to Windows shortcuts or Mac aliases).

I didnt reject your idea about *excluding* everything and *including* what I want backed up, its simply the fact that I had already created the exclude list and was trying to understand how it worked.  It also meant I didn't have the extra work of having to negate the list I had already created.

I am more than happy to try your idea, but if I can't make sense of the exclude list then what's to say I will be able to make sense of the include list !?

It would be more useful if you could explain the issues Im having with the exclude list so that I can then implement your suggestion to *exclude* everything and *include* what I want backed up

I've already taken your useful advice about a) pulling backups rather than pushing and b) using rdiff-backup rather than rsync.

I was hoping for a little support to understand these exclude and include lists as thats the final hurdle thats blocking me.

The manual I have been using is on the rdiff-backup website....

[https://rdiff-backup.net/docs/rdiff-backup.1.html](https://rdiff-backup.net/docs/rdiff-backup.1.html)

The server is running version 2.0.0 and the Mac is running 2.0.5

I do get a warning about the different versions, but again, not being a linux expert I don't know how to upgrade the server version or downgrade the Mac version

---

### Post by TheFu on 2021-08-04
I don't have any interest in figuring out how to make exclude lists work on a Mac or even on Linux. I don't use them.  Never tried using specific file lists for either include or exclude purposes. I fall into the *practical solution* group, not the *it must work this way based on my reading of the manual* group. Sorry.

Understanding what special files are isn't too important for backups except that those really should never be included, ever, in a backup.  Just add the option not to include them. Trust me.

For fun, run this command: **cat /dev/urandom**  That is a special file.  What happens?  How long does it take?  The other special files bring similar issues for backup programs.  They can be located anywhere on a file system, not just in /dev/. Running programs will sometimes create FIFOs as a way to communicate between multiple processes. I'd done that in a few of my solutions. A backup tool wouldn't like that much at all. It would choke and never end. A 5 minute backup would become a 45day backup - the reboot would end it.

I have both plex and nextcloud servers. I don't trust either to manage any data and generally provide just read-only access to the files they access.

Don't use website man pages. Use the manpages on your system. Those aren't likely to be for the version that you have installed.  BTW, 20.04 and later rdiff-backup changed to python3. It is incompatible with a python2 client. Just be aware. The incompatibility is purely in the python versions, not the rdiff-backup code. Because I run older servers, I ended up porting the python2 and rdiff-backup dependencies to 20.04 for compatibility.  I'll need to keep that until all my systems are to 20.04 or later, which is probably at least a year away.

---

### Post by freeflyjohn on 2021-08-04
> **TheFu said:**
> I don't have any interest in figuring out how to make exclude lists work on a Mac or even on Linux. I don't use them.  Never tried using specific file lists for either include or exclude purposes. I fall into the *practical solution* group, not the *it must work this way based on my reading of the manual* group. Sorry.

Understanding what special files are isn't too important for backups except that those really should never be included, ever, in a backup.  Just add the option not to include them. Trust me.

For fun, run this command: **cat /dev/urandom**  That is a special file.  What happens?  How long does it take?  The other special files bring similar issues for backup programs.  They can be located anywhere on a file system, not just in /dev/. Running programs will sometimes create FIFOs as a way to communicate between multiple processes. I'd done that in a few of my solutions. A backup tool wouldn't like that much at all. It would choke and never end. A 5 minute backup would become a 45day backup - the reboot would end it.

I have both plex and nextcloud servers. I don't trust either to manage any data and generally provide just read-only access to the files they access.

Don't use website man pages. Use the manpages on your system. Those aren't likely to be for the version that you have installed.  BTW, 20.04 and later rdiff-backup changed to python3. It is incompatible with a python2 client. Just be aware. The incompatibility is purely in the python versions, not the rdiff-backup code. Because I run older servers, I ended up porting the python2 and rdiff-backup dependencies to 20.04 for compatibility.  I'll need to keep that until all my systems are to 20.04 or later, which is probably at least a year away.

OK I'll try with include lists instead of exclude lists

Maybe I'm being naive, but I would have though exclude lists work the same way as include lists, only they are negated ?

Are you saying I should use the --exclude-special-files option as well then ?  So I just need to add this to the command line ? i.e.

```

rdiff-backup -v5 --exclude-special-files --exclude-globbing-filelist ~/.rdiff-backup/exclude_list.txt myname@macbookpro.fritz.box::/Users/myname /media/storage/Backup/Mac/rdiff-backup/myname

```

Like I said, I just want to bakcup my personal data at this stage, I'm less interested in backing up system files at the moment.

I can always re-install an OS if system files are lost, but I will never be able to restore personal data if that is lost.

PS. the principle of rdiff-backup seems similar to the tool SVN which I have used extensively in my job over the last 10 years for version control.

PPS. I tried the command cat /dev/urandom and it just spat out lots of garbage in the terminal window which I had to CTRL-C to stop !  As an embedded software and controls engineer, I understand FIFO being first in first out.  But when it comes to Linux I've only just scratched the surface, hence the reason for posting on this forum for help

---

### Post by TheFu on 2021-08-04
I'm suggesting that you not use any list of files at all and use --exclude and include as shown in post #3 above, in the order shown.

A pattern to exclude dot files/directories is 
```
--exclude ignorecase:'**/.[a-z0-9]*'
```
If you only want a single HOME directory, then list that in the --includes.
```

rdiff-backup
       --exclude-special-files \
       --exclude '**/.[a-Z0-9]*'  \
       --include /Users/myname/rdiff_test  \
       --exclude '**'   backup3288@${remote-machine}::/ \ 
       /Backups/${remote-machine}
```

That seems much easier to me.

If you only want to include:
+ /Users/myname/rdiff_test/source/Documents
+ /Users/myname/rdiff_test/source/Downloads
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
+ /Users/myname/rdiff_test/source/Pictures
and nothing else, 
```

rdiff-backup
       --exclude-special-files \
       --exclude '**/.[a-Z0-9]*'  \
       --include  /Users/myname/rdiff_test/source/Documents  \
       --include  /Users/myname/rdiff_test/source/Downloads  \ 
       --include  /Users/myname/rdiff_test/source/Movies  \
       --include  /Users/myname/rdiff_test/source/Music  \
       --include  /Users/myname/rdiff_test/source/Pictures \ 
       --exclude '**'   backup3288@${remote-machine}::/ \ 
       /Backups/${remote-machine}
```

Does that not work?

---

### Post by freeflyjohn on 2021-08-05
> **TheFu said:**
> I'm suggesting that you not use any list of files at all and use --exclude and include as shown in post #3 above, in the order shown.

A pattern to exclude dot files/directories is 
```
--exclude ignorecase:'**/.[a-z0-9]*'
```
If you only want a single HOME directory, then list that in the --includes.
```

rdiff-backup
       --exclude-special-files \
       --exclude '**/.[a-Z0-9]*'  \
       --include /Users/myname/rdiff_test  \
       --exclude '**'   backup3288@${remote-machine}::/ \ 
       /Backups/${remote-machine}
```

That seems much easier to me.

If you only want to include:
+ /Users/myname/rdiff_test/source/Documents
+ /Users/myname/rdiff_test/source/Downloads
+ /Users/myname/rdiff_test/source/Movies
+ /Users/myname/rdiff_test/source/Music
+ /Users/myname/rdiff_test/source/Pictures
and nothing else, 
```

rdiff-backup
       --exclude-special-files \
       --exclude '**/.[a-Z0-9]*'  \
       --include  /Users/myname/rdiff_test/source/Documents  \
       --include  /Users/myname/rdiff_test/source/Downloads  \ 
       --include  /Users/myname/rdiff_test/source/Movies  \
       --include  /Users/myname/rdiff_test/source/Music  \
       --include  /Users/myname/rdiff_test/source/Pictures \ 
       --exclude '**'   backup3288@${remote-machine}::/ \ 
       /Backups/${remote-machine}
```

Does that not work?

Thanks TheFu, I see what you are saying now and will try your suggestion.

The original reason for using a file list was to avoid having a long string for the command line and to make the excludes and includes easier to work with and more readable.

I used rsycn with a file list and it worked without any problems, so its strange that rdiff-backup doesn't seem to work the same way with a separate file list ?

I have recently created a bash .sh script for the rdiff-backup command, so a long command string will not be an issue now.

And the way you have shown how to add each include on separate lines (by terminating with the \ character) makes it much more readable and maintainable than a long command string.

So just for my understanding, these first two lines exclude EVERYTHING and the lines after explicitly include the folders to backup ?

```

       --exclude-special-files \
       --exclude '**/.[a-Z0-9]*'  \

```

---

### Post by freeflyjohn on 2021-08-05
Hmmmm.... I cant seem to get that to work either.

And this time I'm testing it on the server (rather than the Mac)

When I run the script below:

```

#!/bin/bash
rdiff-backup -v5 --print-statistics \
        --exclude-special-files \
        --exclude '**/.[a-Z0-9]*'  \
        --include  /home/myname/rdiff-test/source/Desktop \
        --include  /home/myname/rdiff-test/source/Documents \
        --include  /home/myname/rdiff-test/source/Downloads \
        --include  /home/myname/rdiff-test/source/Movies \
        --include  /home/myname/rdiff-test/source/Music \
        --include  /home/myname/rdiff-test/source/Pictures \
        /home/myname/rdiff-test/source \
        /home/myname/rdiff-test/backup

```

I get a whole load of errors:

```

Using rdiff-backup version 2.0.0
    with cpython /usr/bin/python3 version 3.8.10
    on Linux-5.4.0-80-generic-x86_64-with-glibc2.29, fs encoding utf-8
Found interrupted initial backup. Removing...
Unable to import win32security module. Windows ACLs
not supported by filesystem at /home/myname/rdiff-test/source
-----------------------------------------------------------------
Detected abilities for source (read only) file system:
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Unable to import win32security module. Windows ACLs
not supported by filesystem at /home/myname/rdiff-test/backup/rdiff-backup-data/rdiff-backup.tmp.0
-----------------------------------------------------------------
Detected abilities for destination (read/write) file system:
  Ownership changing                           Off
  Hard linking                                 On
  fsync() directories                          On
  Directory inc permissions                    On
  High-bit permissions                         On
  Symlink permissions                          Off
  Extended filenames                           On
  Windows reserved filenames                   Off
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Backup: escape_dos_devices = 0
Backup: escape_trailing_spaces = 0
Exception 'bad character range a-Z at position 7' raised of class '<class 're.error'>':
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 390, in error_check_Main
    Main(arglist)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 412, in Main
    take_action(rps)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 348, in take_action
    Backup(rps[0], rps[1])
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 429, in Backup
    backup_set_select(rpin)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 456, in backup_set_select
    rpin.conn.backup.SourceStruct.set_source_select(rpin, select_opts,
  File "/usr/lib/python3/dist-packages/rdiff_backup/backup.py", line 76, in set_source_select
    sel.ParseArgs(tuplelist, filelists)
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 255, in ParseArgs
    self.add_selection_func(self.glob_get_sf(arg, 0))
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 612, in glob_get_sf
    sel_func = self.glob_get_normal_sf(glob_str, include)
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 679, in glob_get_normal_sf
    glob_comp_re = re_comp(b"^%b($|/)" % self.glob_to_re(glob_str))
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 676, in re_comp
    return re.compile(r, re.S)
  File "/usr/lib/python3.8/re.py", line 252, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python3.8/re.py", line 304, in _compile
    p = sre_compile.compile(pattern, flags)
  File "/usr/lib/python3.8/sre_compile.py", line 764, in compile
    p = sre_parse.parse(p, flags)
  File "/usr/lib/python3.8/sre_parse.py", line 948, in parse
    p = _parse_sub(source, state, flags & SRE_FLAG_VERBOSE, 0)
  File "/usr/lib/python3.8/sre_parse.py", line 443, in _parse_sub
    itemsappend(_parse(source, state, verbose, nested + 1,
  File "/usr/lib/python3.8/sre_parse.py", line 598, in _parse
    raise source.error(msg, len(this) + 1 + len(that))


Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 32, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 390, in error_check_Main
    Main(arglist)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 412, in Main
    take_action(rps)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 348, in take_action
    Backup(rps[0], rps[1])
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 429, in Backup
    backup_set_select(rpin)
  File "/usr/lib/python3/dist-packages/rdiff_backup/Main.py", line 456, in backup_set_select
    rpin.conn.backup.SourceStruct.set_source_select(rpin, select_opts,
  File "/usr/lib/python3/dist-packages/rdiff_backup/backup.py", line 76, in set_source_select
    sel.ParseArgs(tuplelist, filelists)
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 255, in ParseArgs
    self.add_selection_func(self.glob_get_sf(arg, 0))
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 612, in glob_get_sf
    sel_func = self.glob_get_normal_sf(glob_str, include)
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 679, in glob_get_normal_sf
    glob_comp_re = re_comp(b"^%b($|/)" % self.glob_to_re(glob_str))
  File "/usr/lib/python3/dist-packages/rdiff_backup/selection.py", line 676, in re_comp
    return re.compile(r, re.S)
  File "/usr/lib/python3.8/re.py", line 252, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python3.8/re.py", line 304, in _compile
    p = sre_compile.compile(pattern, flags)
  File "/usr/lib/python3.8/sre_compile.py", line 764, in compile
    p = sre_parse.parse(p, flags)
  File "/usr/lib/python3.8/sre_parse.py", line 948, in parse
    p = _parse_sub(source, state, flags & SRE_FLAG_VERBOSE, 0)
  File "/usr/lib/python3.8/sre_parse.py", line 443, in _parse_sub
    itemsappend(_parse(source, state, verbose, nested + 1,
  File "/usr/lib/python3.8/sre_parse.py", line 598, in _parse
    raise source.error(msg, len(this) + 1 + len(that))
re.error: bad character range a-Z at position 7

```

I removed the lines from the script file and added them back one by one and found the issue is with this line, it must be a syntax error somewhere ?

```

        --exclude '**/.[a-Z0-9]*'  \

```

The error appears to state:

```

Exception 'bad character range a-Z at position 7' raised of class '<class 're.error'>':

```

---

### Post by freeflyjohn on 2021-08-05
OK, I seem to have fixed the syntax error by changing:

```

--exclude '**/.[a-Z0-9]*'  \

```

to:

```

 --exclude ignorecase:'**/.[a-z0-9]*' \

```



So the script file is now:

```

#!/bin/bash
rdiff-backup -v5 --print-statistics \
        --exclude-special-files \
        --exclude ignorecase:'**/.[a-z0-9]*' \
        --include /home/myname/rdiff-test/source/Desktop \
        --include /home/myname/rdiff-test/source/Documents \
        --include /home/myname/rdiff-test/source/Downloads \
        --include /home/myname/rdiff-test/source/Movies \
        --include /home/myname/rdiff-test/source/Music \
        --include /home/myname/rdiff-test/source/Pictures \
        /home/myname/rdiff-test/source \
        /home/myname/rdiff-test/backup



```

However, for some reason none of the include folders specified are in the backup.

The backup is empty, other than the rdiff-backup-data folder.

So why aren't the include folders being, included ?

This is the error... 

```

./rdiff_test_local.sh 
Using rdiff-backup version 2.0.0
	with cpython /usr/bin/python3 version 3.8.10
	on Linux-5.4.0-80-generic-x86_64-with-glibc2.29, fs encoding utf-8
Found interrupted initial backup. Removing...
Unable to import win32security module. Windows ACLs
not supported by filesystem at /home/myname/rdiff-test/source
-----------------------------------------------------------------
Detected abilities for source (read only) file system:
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Unable to import win32security module. Windows ACLs
not supported by filesystem at /home/myname/rdiff-test/backup/rdiff-backup-data/rdiff-backup.tmp.0
-----------------------------------------------------------------
Detected abilities for destination (read/write) file system:
  Ownership changing                           Off
  Hard linking                                 On
  fsync() directories                          On
  Directory inc permissions                    On
  High-bit permissions                         On
  Symlink permissions                          Off
  Extended filenames                           On
  Windows reserved filenames                   Off
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Backup: escape_dos_devices = 0
Backup: escape_trailing_spaces = 0
[COLOR=#ff0000]Fatal Error: Last selection expression:[/COLOR]
[COLOR=#ff0000]    Command-line include glob: b'/home/myname/rdiff-test/source/Pictures'[/COLOR]
[COLOR=#ff0000]only specifies that files be included.  Because the default is to[/COLOR]
[COLOR=#ff0000]include all files, the expression is redundant.  Exiting because this[/COLOR]
[COLOR=#ff0000]probably isn't what you meant.[/COLOR]



```
[FONT=Verdana]
[/FONT]

---

### Post by TheFu on 2021-08-05
Where's the my
```
--exclude '**'  
```
?????
That's what excludes everything. Order matters. Details matter.  I can promise you that the example in post #3 works on a v1.2.x rdiff-backup.

---

### Post by freeflyjohn on 2021-08-05
Thanks TheFu..... AT LAST ITS WORKING ! 

Well... I tested using the empty dummy folders and it worked.  I've just started the REAL backup and that will need to run overnight.

When I was testing I was using local source and local destination paths on the server, rather than using a remote source path via SSH, so this is why I had left your remote line out in addition to the --exclude '**' (not knowing what it meant)...

```

       --exclude '**'   backup3288@${remote-machine}::/ \ 
[\CODE]

Since correcting this, the local test bash script now looks like this:

[CODE]
#!/bin/bash
rdiff-backup -v5 --print-statistics \
	--exclude-special-files \
	--exclude ignorecase:'**/.[a-z0-9]*' \
        --include /home/myname/rdiff-test/source/Desktop \
	--include /home/myname/rdiff-test/source/Documents \
	--include /home/myname/rdiff-test/source/Downloads \
	--include /home/myname/rdiff-test/source/Movies \
	--include /home/myname/rdiff-test/source/Music \
        --include /home/myname/rdiff-test/source/Pictures \
	--exclude '**' /home/myname/rdiff-test/source \
	/home/myname/rdiff-test/backup

```

And for the real backup using a remote source path via SSH it looks like this:

```

#!/bin/bash
rdiff-backup -v5 --print-statistics \
	--exclude-special-files \
	--exclude ignorecase:'**/.[a-z0-9]*' \
        --exclude /Users/myname/Documents/Microsoft\ User\ Data \
	--exclude /Users/myname/Documents/Parallels \
        --exclude /Users/myname/Downloads/svn \
        --include /Users/myname/Desktop \
	--include /Users/myname/Documents \
	--include /Users/myname/Downloads \
	--include /Users/myname/Movies \
	--include /Users/myname/Music \
        --include /Users/myname/Pictures \
	--exclude '**' myname@macbookpro.fritz.box::/Users/myname \
	/media/storage/Backup/Mac/rdiff-backup/myname

```

One final thing, what does the line --exclude '**' prior to the source path do, I don't understand it ?

All the excludes are done at the top of the script, followed by the includes.

But then the source path its preceded by --exclude '**' ?

PS.  I find your implementation of excluding everything then including the paths I want backed up much easier. As well as doing it all in the command line within the bash script, rather than having to handle both the bash script AND the exclude file list which was harder to maintain.  So thanks again for explaining this.

---

### Post by TheFu on 2021-08-05
Plug the command into explainshell.com and learn.

Remember when I said the order matters?

The base command is this:
```
$ rdiff-backup [email]myname@macbookpro.fritz.box[/email]::/Users/myname /media/storage/Backup/Mac/rdiff-backup/myname
     command                  {source}                              {target}
```

The source is myname@macbookpro.fritz.box::/Users/myname, but you don't want the entire source tree, just specific directories which are in --include parameters.

The --exclude '**' says to NOT include what the source says. It says exclude everything.  Put that before the --includes and nothing will get backed up.  The order of the include/exclude options matters.  I've not tried this, but the source could be /tmp, perhaps?  Maybe that would work?  I have doubts. Never tried it. Maybe that would be clearer?

Then we prepend the --includes so something is included.  Without the --exclude '**', everything in the {source} gets included so all the includes, which are below the source, get included. It is redundant and causes an error (see above).

You said you didn't want **any** dot files or directories.  I think this is a bad idea, but it's your system and your recovery.  To me, those hold the settings that make a system "mine". I want them in the restore, though I don't want any cache or temporary files and some web 'local storage' files which get used for advertising tracking.  But this is your system, not mine.

---

### Post by freeflyjohn on 2021-08-06
> **TheFu said:**
> Plug the command into explainshell.com and learn.
You said you didn't want **any** dot files or directories.  I think this is a bad idea, but it's your system and your recovery.  To me, those hold the settings that make a system "mine". I want them in the restore, though I don't want any cache or temporary files and some web 'local storage' files which get used for advertising tracking.  But this is your system, not mine.

Thanks TheFu, 

I'm now a bit concerned about excluding **all** dot files, as you say its a bad idea.

I'm just concerned in case there are any dot files/folders in any of these paths that should be backed up...


[LIST]
[*]Desktop
[*]Documents
[*]Downloads
[*]Movies
[*]Music
[*]Pictures
[/LIST]

How do I only exclude the dot files/folders in the user home path (as shown by the red boxes in the picture below) BUT include all other dot files/folders ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288930&stc=1[/IMG]

Below is the command I'm using at the moment:

```


#!/bin/bash
rdiff-backup -v5 --print-statistics \
    --exclude-special-files \
    --exclude ignorecase:'**/.[a-z0-9]*' \
        --exclude /Users/myname/Documents/Microsoft\ User\ Data \
    --exclude /Users/myname/Documents/Parallels \
        --exclude /Users/myname/Downloads/svn \
        --include /Users/myname/Desktop \
    --include /Users/myname/Documents \
    --include /Users/myname/Downloads \
    --include /Users/myname/Movies \
    --include /Users/myname/Music \
        --include /Users/myname/Pictures \
    --exclude '**' myname@macbookpro.fritz.box::/Users/myname \
    /media/storage/Backup/Mac/rdiff-backup/myname


```


Is this the line that excludes all dot files/folders ?

```

--exclude ignorecase:'**/.[a-z0-9]*' \

```

What do I need to change or add to exclude the dot files/folders in the user home path BUT include all other dot files/folders ?

[U]Or would I be better not excluding any dot files/folders at all - in which case what do I need to change or add ?
[/U]
Presumably if I modify the command with the fix to include the dot files/folders and then perform another backup, it will add these dot files/folders as the next version ?

Which shouldn't take long as I guess the dot files/folders won't be that large in size ?

PS. The backup performed successfully over night :P Are the warnings at the bottom (in red) anything to worry about ?

```

--------------[ Session statistics ]--------------
StartTime 1628191541.00 (Thu Aug  5 20:25:41 2021)
EndTime 1628229152.96 (Fri Aug  6 06:52:32 2021)
ElapsedTime 37611.96 (10 hours 26 minutes 51.96 seconds)
SourceFiles 156650
SourceFileSize 645317042978 (601 GB)
MirrorFiles 1
MirrorFileSize 0 (0 bytes)
NewFiles 156649
NewFileSize 645317042978 (601 GB)
DeletedFiles 0
DeletedFileSize 0 (0 bytes)
ChangedFiles 1
ChangedSourceSize 0 (0 bytes)
ChangedMirrorSize 0 (0 bytes)
IncrementFiles 0
IncrementFileSize 0 (0 bytes)
TotalDestinationSizeChange 645317042978 (601 GB)
Errors 0
--------------------------------------------------
[COLOR=#ff0000]Unable to import module (py)xattr.[/COLOR]
[COLOR=#ff0000]Extended attributes not supported on filesystem at /Users/myname[/COLOR]
[COLOR=#ff0000]Unable to import module posix1e from pylibacl package.[/COLOR]
[COLOR=#ff0000]POSIX ACLs not supported on filesystem at /Users/myname[/COLOR]
[COLOR=#ff0000]Unable to import win32security module. Windows ACLs[/COLOR]
[COLOR=#ff0000]not supported by filesystem at /Users/myname[/COLOR]

```

---

### Post by freeflyjohn on 2021-08-06
Also, how do I exclude ANY folders matching this:

[INDENT]*.Trash
*.AppleDouble
*$RECYCLE.BIN[/INDENT]

And ANY files matching this:
[INDENT]*.ini[/INDENT]

I originally had the above defined in the exclude globing list, but now I'm no longer using the list I need to define these excludes in the command string somehow.

Unfortunately, the above folders and files are in the backup I performed last night.

If I can add the above excludes to the command line, when I run another backup I don't think they will be removed from the backup will they ?

Is the easiest way to get rid of these files to run a fresh new backup with the correct excludes in the command line ?

I don't suppose there is a command to delete files from the backup ?

And you cant simply delete these files from the backup, otherwise it will screw up the rdiff-backup-data ?

---

### Post by freeflyjohn on 2021-08-06
This seems to have worked...

```


#!/bin/bash
rdiff-backup -v5 --print-statistics \
    --exclude-special-files \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \    
        --exclude /Users/myname/Documents/Microsoft\ User\ Data \
    --exclude /Users/myname/Documents/Parallels \
        --exclude /Users/myname/Downloads/svn \
        --include /Users/myname/Desktop \
    --include /Users/myname/Documents \
    --include /Users/myname/Downloads \
    --include /Users/myname/Movies \
    --include /Users/myname/Music \
        --include /Users/myname/Pictures \
    --exclude '**' myname@macbookpro.fritz.box::/Users/myname \
    /media/storage/Backup/Mac/rdiff-backup/myname

```

---

