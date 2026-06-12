---
title: "[SOLVED] backup /home using 'cp' command"
date: 2007-10-26
forum: General Help
---

### Post by perixx on 2007-10-26
hello!

I'd like to back up my /home/USER directory with all hidden/special files and subfolders to /var/USER and keep the original permissions + ownership...

will
sudo cp -prbf --copy-contents *.* /var/USER
do?


perixx

---

### Post by perixx on 2007-10-26
well, that didn't work... maybe because I'm trying to write an 'USER' ownership group to a root directory?

could I alternatively create a folder with identical contents/permissions/group by copying /home/USER to /home/backup with 'gksudo Thunar' > copy all
and then change the group ownership of /home/backup back from 'root' to 'USER' again?


perixx

---

### Post by Gwasanaethau on 2007-10-26
> **perixx said:**
> hello!

I'd like to back up my /home/USER directory with all hidden/special files and subfolders to /var/USER and keep the original permissions + ownership...

will
sudo cp -prbf --copy-contents *.* /var/USER
do?


perixx

What sort of error did you get here? Did it copy everything or did it refuse to copy?

---

### Post by teqagogo on 2007-10-26
you need first to create the target directory

---

### Post by Sunforge on 2007-10-26
You could try using rsync, which was designed for things like mirroring web sites but is equally at home copying stuff between folders:

sudo rsync -avu --delete /home/(NameOfHome)/ /var/(NameOfHome)/

--delete deletes anything in the target folder that you've deleted in the original folder, which does stop you backup growing.

-a = archive mode
-v = verbose (only use it once and you'll get bored but it's fun the first time)
-u =skip files that are newer on the receiver, this only works on subsequent times but does speed things up for subsequent backups.

Here's a complete man page for you:

[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

On the other hand if you like to whip past the command line and fast forward to something a little more visual:

[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)

Either will get you to where you wish to go.

---

### Post by perixx on 2007-10-26
Well, I didn't get ANY response and nothing was copied (I was in sudo-Terminal, of course).... the folder was already in place, that wasn't the problem.

The rsync-method looks interesting! Might be very good, if it also preserves the permissions and group status. I'll have a look into that anytime soon - I'm looking for a fitting backup program anyway.

I was able to solve the copying problem and moved everything to a new partition - but I used some rather complicated procedure from the 'psychocats' website, which isn't applicable in other occasions for me...


perixx

perixx

---

### Post by Sunforge on 2007-10-27
[FONT=Tahoma]You can tell rsync to preserve whatever permissions you're interested in:
[/FONT]
-p, –perms preserve permissions-o, –owner preserve owner (root only)[FONT=Tahoma]
-g, –group preserve group[/FONT][FONT=Tahoma] 

On the other hand the graphical backup thingy has just as many options.

[/FONT]

---

### Post by louieb on 2007-10-27
**tar **is another option, it can be told to preserve permissions and ownership. Just go to the how to section and do a search on backup. Theres a couple of good post on how to use it.

---

### Post by perixx on 2007-10-27
Many thanks, Sunforge, thanks louieb...


Would you mind in also helping me on this thread?

[http://ubuntuforums.org/showthread.php?t=589635](http://ubuntuforums.org/showthread.php?t=589635)


perixx

---

### Post by perixx on 2008-01-09
Currently, as the best alternatives to 'cp' as a backup method that fit into place to satisfy my needs are:

- the 'graphical rsync' backend 'Sbackup' - in Synaptic or here:
[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html]("http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html")

- and manually doing 'rsync', as posted by Sunforge - like so:
```
sudo rsync -au --append ~/ /destination-folder
```
-> syncing all files from '/home/user' to '/destination', keeping all permissions and user/group-ownership + updating only newer files to destination 
-> elder files are ONLY being overwritten, when newer and/or bigger files exist. 
No files are deleted, even if they were in the /home folder! 

perixx

---

