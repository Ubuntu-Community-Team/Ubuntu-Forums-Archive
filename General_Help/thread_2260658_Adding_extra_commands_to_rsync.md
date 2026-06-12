---
title: "Adding extra commands to rsync"
date: 2015-01-13
forum: General Help
---

### Post by MibunoOokami on 2015-01-13
I would like to refine my rsync script to copy all files and directories that would ordinarily require permissions to copy/backup. I'm trying to learn about this myself and think I need a -r command for copying any files that need permissions which I think gets added to the -av part of the script so might be -avr. It won't let me run the script as root saying ```
sudo: incbackup: command not found
```

I would also like to be able to get it to skip the .cache/firefox directory because recently rsync seems to keep hanging (freezing) on this directory. I know I need to add a &#8211;exclude command but not sure how exactly to specify the path and if it goes before or after the ~/ part of my script.

I would appreciate it if you could teach me how to do this. Thanks

The script I use is called incbackup. 

```
#! /bin/bash 
 
#copy the contents of ~/ to the given device /media/devicename
#only changed or new files will be copied 
 
rsync -av ~/ /media/username/devicename/directoryname
```

---

### Post by ajgreeny on 2015-01-13
I can't help with the files that need root permissions, apart from suggesting using sudo to run rsync, but I can tell you that the -r option is simply the option shortcut for recursive, ie including all subdirectories of the one specified in the command.

As for excluding folders, see man rsync which tells you
```
--exclude=PATTERN
              This option is a simplified form of the --filter option that defaults to an exclude rule and  does  not
              allow the full rule-parsing syntax of normal filter rules.

              See the FILTER RULES section for detailed information on this option.

       --exclude-from=FILE
              This  option is related to the --exclude option, but it specifies a FILE that contains exclude patterns
              (one per line).  Blank lines in the file and lines starting with &#8217;;&#8217; or &#8217;#&#8217; are ignored.  If FILE is -,
              the list will be read from standard input.
```

I use the second of these two to exclude lots of folders from my backups, having made a text file called excludecache.txt with content
> .adobe/Flash_Player/AssetCache
.cache
.local/share/Trash
.macromedia
.mozilla/firefox/qn4bdmr0.default/Cache
.mozilla/firefox/qn4bdmr0.default/Cache.Trash
.thumbnails
.thunderbird/cauxhqch.default/Cache
.thunderbird/cauxhqch.default/Cache.Trash

---

### Post by oldfred on 2015-01-14
I ended up with a long enough list of exclusions that having it in one line was unwieldy, so I use the file option.

I started with this:
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603]("http://ubuntuforums.org/showthread.php?t=868244&highlight=backup")
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

# I have separate data partition and folders in it. Part of copy of separate data & copy of /home.
rsync -aruvlP /mnt/data/Notebooks /mnt/backup
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

Then my mybackup_excludes.lst:

# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
/home/*/.wine
home/*/.macromedia

---

### Post by ajgreeny on 2015-01-14
Hi oldfred.

You need to update the path to your Firefox cache; it no longer sits in ~/.mozilla but in ~/.cache/mozilla/firefox/*.default/

---

### Post by oldfred on 2015-01-14
Thanks ajgreeny, I think I can just remove the extra entry, as I am excluding everything in .cache.

---

### Post by MibunoOokami on 2015-01-14
Thanks for the replies guys, I'll give that a go. How come you exclude the .cache directory?

---

### Post by oldfred on 2015-01-14
Nothing in .cache is worth saving, it is just temporary files that are used by various software.

---

### Post by MibunoOokami on 2015-01-14
> **oldfred said:**
> # Note: Trailing SLASHES MATTER, copy form exactly!!!

Is this just a message to me or does that actually go into the mybackup_excludes.lst file?

For now I'm only putting those first three directories in the exclude list until I read up on what the other ones are and decide whether or not I want them.

---

### Post by oldfred on 2015-01-15
It was copied from wherever I got the original example. And I left note in for my own info when I edit file to add new entries. I have troubles myself on copy commands on whether I want / or not.
# is ignored so it is just a comment in file.

---

### Post by SeijiSensei on 2015-01-15
From the backup script above:
```
mount -t ext3 /dev/sda2 /mnt/backup
```

Modern Linux systems rarely use ext3 devices any more.  I'd just omit the "-t ext3" part entirely and let mount figure out what kind of filesystem it is automatically.

The archive switch "-a" implies the recursive switch "-r".  According to the manual page for rsync, "-a" is equivalent to "-rlptgoD".

The man page for rsync also has an extensive discussion of [how filename patterns are interpreted]("https://www.samba.org/ftp/rsync/rsync.html").

---

### Post by MibunoOokami on 2015-01-17
I'm having issues getting rsync to use the exclude list but have managed to just add the one line to my script to get it to skip the .cache directory which contains the mozilla directory and is what I wanted to do.
Thank you for the help with that part.
 

 I found this info under man rsync which has something to do with permissions but I'm not sure I understand it. Does using --perm mean rsync can/will copy files and directories that require permissions?

 ```
-p, --perms 
               This  option  causes  the receiving rsync to set the destination 
               permissions to be the same as the source permissions.  (See also 
               the  --chmod  option for a way to modify what rsync considers to 
               be the source permissions.) 
  
               When this option is _off_, permissions are set as follows: 
  
               o      Existing files (including  updated  files)  retain  their 
                      existing  permissions,  though the --executability option 
                      might change just the execute permission for the file. 
  
               o      New files get their "normal" permission bits set  to  the 
                      source  file’s  permissions  masked  with  the  receiving 
                      directory’s default  permissions  (either  the  receiving 
                      process’s  umask,  or  the  permissions specified via the 
                      destination directory’s default ACL), and  their  special 
                      permission  bits  disabled except in the case where a new 
                      directory inherits a setgid bit from  its  parent  direc&#8208; 
                      tory. 
  Thus,  when  --perms  and  --executability  are  both  disabled, 
               rsync’s behavior is the same as that of other  file-copy  utili&#8208; 
               ties, such as cp(1) and tar(1). 
  
               In  summary:  to  give  destination files (both old and new) the 
               source permissions, use --perms.  To give new files the destina&#8208; 
               tion-default   permissions   (while   leaving   existing   files 
               unchanged), make sure that the --perms option  is  off  and  use 
               --chmod=ugo=rwX  (which  ensures  that  all  non-masked bits get 
               enabled).  If you’d care to make this latter behavior easier  to 
               type, you could define a popt alias for it, such as putting this 
               line in the file ~/.popt (the following defines the  -Z  option, 
               and  includes --no-g to use the default group of the destination 
               dir): 
  
                  rsync alias -Z --no-p --no-g --chmod=ugo=rwX 
  
               You could then use this new option in a  command  such  as  this 
               one: 
  
                  rsync -avZ src/ dest/ 
 

  (Caveat:  make  sure  that  -a  does  not  follow -Z, or it will 
               re-enable the two "--no-*" options mentioned above.) 
  
               The preservation of the destination’s setgid bit  on  newly-cre&#8208; 
               ated  directories  when --perms is off was added in rsync 2.6.7. 
               Older rsync versions erroneously  preserved  the  three  special 
               permission  bits  for  newly-created files when --perms was off, 
               while overriding the  destination’s  setgid  bit  setting  on  a 
               newly-created  directory.   Default  ACL observance was added to 
               the ACL patch for rsync 2.6.7,  so  older  (or  non-ACL-enabled) 
               rsyncs use the umask even if default ACLs are present.  (Keep in 
               mind that it is the version of the receiving rsync that  affects 
               these behaviors.) 
```

---

### Post by MibunoOokami on 2015-01-17
There was one more command I wanted to ask about but it slipped my mind at the time I started this thread.
I've noticed that only my home directory is copied when I back my machines up but I have other user accounts set up and would like to be able to back them up too.

Does anyone know if there is a command so I can do that from just my user account or is it necessary for me to log out and then log in to another user account to back it up?

Thanks.

---

### Post by nerdtron on 2015-01-18
> **MibunoOokami said:**
> 
Does anyone know if there is a command so I can do that from just my user account or is it necessary for me to log out and then log in to another user account to back it up?

Thanks.

If you can run rsync with sudo you basically become root and you should be able to read/backup other home folders too.

---

### Post by SeijiSensei on 2015-01-18
If you run rsync as root with sudo, the -p switch preserves the ownerships and permissions of the files copied to the target.  Like -r, -p is implied by -a.  For backup purposes, you always need to use sudo.

"Ownerships" in this case mean the UID and GID of the file.  If user 1000 is "bill" on the source machine, but "sarah" on the target machine, then the backup of /home/bill on the target will appear to be owned by sarah.  If you use "ls -ln" on the target, you'll see that the ownership still belongs to user 1000.  If both machines have identical /etc/passwd and /etc/group files, the symbolic owners ("bill", "sarah") will match correctly.

---

### Post by MibunoOokami on 2015-01-18
[FONT=Liberation Serif, serif][SIZE=3]If I try running my current rsync script which is called incbackup using sudo it spits out this message ```
sudo: incbackup: command not found
``` Is there a way to make sudo recognise incbackup as a command?[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]I know a different script has been suggested but if possible I'd prefer to keep using the one I currently have because it's simple and I'm learning to understand it a bit better.[/SIZE][/FONT]

---

### Post by oldfred on 2015-01-19
Did you change incbackup to executable?.
Similarly from link in post #3.
chmod +x mybackup.sh

I run mine with 
sudo bash mybackup.sh

---

### Post by MibunoOokami on 2015-01-19
I just double checked and it is marked as executable. I'll see if typing bash works.

---

### Post by kpatz on 2015-01-19
When running a script you have to specify the path to it*.  If you're in the directory that the script is in, use ./scriptname.  (That's dot slash and the name of your script).  So, **sudo ./incbackup** to run your incbackup script in the current directory as root.

*The exception is if the script or program is in a directory listed in your PATH environment variable.  But normally your home folder isn't there, so you have to use the ./

---

### Post by MibunoOokami on 2015-01-19
[FONT=Liberation Serif][SIZE=3]@ Oldfred, thanks for the suggestion, unfortunately it didn't work.[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]@ Kpatz, thanks for the suggestion, that worked for me*. [/SIZE][/FONT] 
 [FONT=Liberation Serif][SIZE=3]Is there a way to get terminal to open in the directory where the script is housed by default every time terminal is open?[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]*Having said that, running as sudo doesn't seem to have made a difference to the directories requiring permissions.[/SIZE][/FONT]

---

### Post by kevdog on 2015-01-20
Ok -- I'm no rsync export -- but its funny.  I just wrote a script that would run rsync but would globally skip all Cache directories or files with cache or Cache in the name. 

I first ran a script that performed a global find looking for all Cache or cache files or directories with Cache or cache in the file name, and then basically wrote this list to a file --- which would be my rsync-exclude list.

find /Users/kevdog -regex ".*/*[Cc]ache*"  -o -type d -name *[Cc]ache* | sed "s/\/Users\/kevdog\///g" > /Users/kevdog/tmp/rsync-excludes.txt

I later expanded this find to find and list all ~/tmp and ~/mnt directories --- since I did not want to back these up either. 

find /Users/kevdog -regex ".*/*[Cc]ache*" -o -regex ".*/mnt" -o -regex ".*/tmp" -o -type d -name *[Cc]ache* | sed "s/\/Users\/kevdog\///g" > /Users/kevdog/tmp/rsync-excludes.txt

I then used this list as an exclusion list for rsync:

rsync -avz --exclude-from=/Users/kevdog/tmp/rsync-excludes.txt -e "ssh -p 222" /Users/kevdog/ kevdog@<IP>:~/backup/Users/kevdog/

I put these two commands within a single script, and then called this script from a user crontab.  
Hopefully this might help you.

---

### Post by kpatz on 2015-01-20
> **MibunoOokami said:**
> Is there a way to get terminal to open in the directory where the script is housed by default every time terminal is open?

I assume you're using Unity (regular Ubuntu GUI as opposed to XFCE, LXDE, Gnome, etc.).

1.  Open a terminal.
2.  Copy the file /usr/share/applications/gnome-terminal.desktop to ~/.local/share/applications, and rename it to something else such as gnome-terminal-yourdirectory.desktop.
3.  Open the file in an editor (i.e. gedit gnome-terminal-yourdirectory.desktop &)
4.  Change the Name line to something to distinguish it from the default terminal (i.e. "Terminal in yourdirectory")
5.  On the line that reads Exec=gnome-terminal, add --working-directory=yourdirectory afterward (so, for example, if yourdirectory is /usr/share, the line would read **Exec=gnome-terminal --working-directory=/usr/share**
6.  Change the comment line (if desired).
7.  Save the file.
8.  Restart Unity (log out and back in).
9.  Open the Dash (search) and type in "terminal".  You should see your new entry in the list.  Launch it.  You should see a terminal in the directory you specified.
10.  Right click the icon in the launcher and select "Lock in launcher" (if you want it to stay there).

---

### Post by MibunoOokami on 2015-01-20
[FONT=Liberation Serif][SIZE=3]Just to confirm, is “yourdirectory” to be the directory that contains my script?[/SIZE][/FONT] And w[FONT=Liberation Serif][SIZE=3]hen changing the “exec-gnome-terminal” line am I specifying the path where my script is?

I just want to make sure I understand correctly. Thanks.
[/SIZE][/FONT]

---

### Post by kpatz on 2015-01-20
Correct.  Change "yourdirectory" to the path of the directory you want the terminal to open up in.  It can be the directory your script is in.

---

### Post by MibunoOokami on 2015-01-20
That took me quite a while to sort out. Incbackup lives in /home/bin which I added to the file but terminal opened in /home like it always does, I changed the path to ~/bin which didn't work so I finally decided to move the directory to /usr/share and terminal opened in that location.
The only problem with that was it wouldn't recognise sudo ./incbackup or just incbackup as a command.
Whilst I was changing directories in terminal I realised you can't just type cd /home and be in your home directory you have to type cd /home/username. So I copied the bin directory back into the home one then changed the “exec=gnome-terminal” line to read “exec=gnome-terminal –working-directory=/home/username/bin”, restarted the machine instead of logging in and out, opened terminal and voila it was opened in the correct directory. Then I typed sudo ./incbackup and it worked.

Now if I could just work out why there are still permission errors even when using sudo.

---

### Post by MibunoOokami on 2015-01-20
[FONT=Liberation Serif, serif][SIZE=3]@ Kevdog, thanks for your post. I think for now I'll just stick with my one line exclusion command in my script because I don't know if I need to/should exclude any other directories or files  and when I tried using an exclusion list rsync still copied what I wanted excluded.[/SIZE][/FONT]

---

