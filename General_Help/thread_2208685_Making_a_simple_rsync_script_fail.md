---
title: "Making a simple rsync script fail"
date: 2014-03-01
forum: General Help
---

### Post by samwillc on 2014-03-01
Hi everyone,

TheFu kindly helped me work out how to use rdiff-backup a couple of weeks ago. However, now I am testing rsync but I can't get it to work as I would like. All I want to do is copy the following:

```

/home
/etc
/usr/local
/usr/share/bluej
/opt

```

to:

```

/media/SEAGATE #my external HDD

```

In the end I want a fully automated solution, but must learn how to walk first! I am trying just two folders for starters but can't even get that right:

```

sam@sam-pc:/$ sudo rsync -av --progress --include="/home/sam/Pictures" --include="/home/sam/Python" --exclude="*" / /media/SEAGATE/

```

In my mind, I want to copy everything from '/', excluding everything except 'Pictures' and 'Python'. This is not how it's panned out though when testing. I have tried running this from 'sam@sam-pc:/$' and from 'sam@sam-pc:~$', no good. I just keep getting nothing copied. I also tried:

```

sudo rsync -av --progress --include="/home/sam/Pictures" --include="/home/sam/Python" /media/SEAGATE/

```

...thinking that the two includes might act as the source to save having to specify one. No good, just copies 'Pictures' to the external HDD. Probably something really simple but I can't find any examples online that copy a few folders locally, examples always just show one, even on pages with 10 or 15 examples! You'd think this is pretty common.

```

sam@sam-pc:~$ sudo rsync -av --progress --dry-run --include="/home/sam/Pictures" --include="/home/sam/Python" --exclude="/" / /media/SEAGATE/

```

Glad I did this as dry run, everything got copied! How do you do this? Any advice on what Im doing wrong is very much appreciated, thanks. Once I get this sorted I can make the script.

Sam.

---

### Post by sudodus on 2014-03-01
Start with something simple, for example like I explained recently in [this post]("http://ubuntuforums.org/showthread.php?t=2208374&p=12942705#post12942705")

You can also try something like this (that works for me)

Create an empty directory
Go there (change directory to the empty directory)
```

sudodus@storen ~/test/ttt $ mkdir a1
sudodus@storen ~/test/ttt $ mkdir a2
sudodus@storen ~/test/ttt $ echo hej>a1/hej
sudodus@storen ~/test/ttt $ echo hejsan>a2/hejsan
sudodus@storen ~/test/ttt $ l a*/
a1/:
totalt 4
-rw-rw-r-- 1 sudodus sudodus 4 mar  1 22:26 hej

a2/:
totalt 4
-rw-rw-r-- 1 sudodus sudodus 7 mar  1 22:26 hejsan
sudodus@storen ~/test/ttt $ mkdir backup
sudodus@storen ~/test/ttt $ [COLOR=#0000ff]rsync -avn a1 a2 backup[/COLOR]
sending incremental file list
a1/
a1/hej
a2/
a2/hejsan

sent 112 bytes  received 26 bytes  276.00 bytes/sec
total size is 11  speedup is 0.08 (DRY RUN)
sudodus@storen ~/test/ttt $ [COLOR=#0000ff]rsync -avn a1/ a2/ backup[/COLOR]
sending incremental file list
./
hej
hejsan

sent 89 bytes  received 21 bytes  220.00 bytes/sec
total size is 11  speedup is 0.10 (DRY RUN)
sudodus@storen ~/test/ttt $ [COLOR=#0000ff]rsync -av a1/ a2/ backup[/COLOR]
sending incremental file list
./
hej
hejsan

sent 180 bytes  received 53 bytes  466.00 bytes/sec
total size is 11  speedup is 0.05
sudodus@storen ~/test/ttt $ [COLOR=#800080]rsync -av a1/ a2/ backup   # this time the files are already backup up, so no files are sent[/COLOR]
sending incremental file list

sent 80 bytes  received 12 bytes  184.00 bytes/sec
total size is 11  speedup is 0.12
sudodus@storen ~/test/ttt $ l backup
totalt 8
-rw-rw-r-- 1 sudodus sudodus 4 mar  1 22:26 hej
-rw-rw-r-- 1 sudodus sudodus 7 mar  1 22:26 hejsan
sudodus@storen ~/test/ttt $ find backup
backup
backup/hejsan
backup/hej
sudodus@storen ~/test/ttt $ rm backup/*
rm: ta bort normal fil &#8221;backup/hej&#8221;? y
rm: ta bort normal fil &#8221;backup/hejsan&#8221;? y
sudodus@storen ~/test/ttt $ [COLOR=#0000ff]rsync -av a1 a2 backup[/COLOR]
sending incremental file list
a1/
a1/hej
a2/
a2/hejsan
sent 203 bytes  received 58 bytes  522.00 bytes/sec
total size is 11  speedup is 0.04
sudodus@storen ~/test/ttt $ [COLOR=#800080]rsync -av a1 a2 backup   # this time the files are already backup up, so no files are sent[/COLOR]
sending incremental file list

sent 100 bytes  received 14 bytes  228.00 bytes/sec
total size is 11  speedup is 0.10
sudodus@storen ~/test/ttt $ find backup
backup
backup/a1
backup/a1/hej
backup/a2
backup/a2/hejsan
sudodus@storen ~/test/ttt

```

---

### Post by Dennis N on 2014-03-01
Focusing on your home folder only:

no sudo needed; the man page suggests not using it. 
just list the folders you want to back up after the options. Do not use --include=

Run from your home folder as working directory:

**rsync -av Pictures Documents /media/SEAGATE**

will copy Pictures and Documents folders to the target. In the result you get:

/media/SEAGATE/Pictures
/media/SEAGATE/Documents

I don't back up anything except my home folder.

---

### Post by vasa1 on 2014-03-01
I make a file listing the stuff I want to backup. Right now, the file looks like this:

```

/etc/gtk-3.0/settings.ini
/etc/nanorc
/etc/xdg/user-dirs.conf
/etc/xdg/user-dirs.defaults
/home/vasa1/.bash_aliases
/home/vasa1/.bashrc
/home/vasa1/bin
/home/vasa1/.config/gtk-2.0
/home/vasa1/.config/gtk-3.0
/home/vasa1/.config/leafpad
/home/vasa1/.config/openbox
/home/vasa1/.config/tint2
/home/vasa1/.config/tumbler
/home/vasa1/.config/user-dirs.dirs
/home/vasa1/.conkyrc
/home/vasa1/Desktop
/home/vasa1/Documents
/home/vasa1/.gtkrc-2.0
/home/vasa1/.icons
/home/vasa1/.local/share/applications
/home/vasa1/.mozilla/firefox/ow58bw39.Australis/adblockplus/patterns.ini
/home/vasa1/.mozilla/firefox/ow58bw39.Australis/chrome
/home/vasa1/.mozilla/firefox/ow58bw39.Australis/prefs.js
/home/vasa1/.mozilla/firefox/ow58bw39.Australis/stylish.sqlite
/home/vasa1/Pictures
/home/vasa1/.themes
/home/vasa1/.xombrero
/home/vasa1/.xombrero.conf
/home/vasa1/.Xresources

```
This is the command I run (first with **--dry-run** and then, after inspecting the log, without **--dry-run**):
```
rsync -r -t -v --delete --protect-args --dry-run --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/'TOSHIBA EXT'/BACKUP/ &> rsync.log
```

Papibe helped me cook that up here: [http://ubuntuforums.org/showthread.php?t=1849674](http://ubuntuforums.org/showthread.php?t=1849674).

My main interest is the data. That's why I haven't bothered about things like permissions and groups etc.

*** *I read somewhere that sorting the list of files would make things easier for rsync but I can't remember where I read it. All the same, the contents of rsync-include.txt are in (default) sorted order.*

Found it in *man rsync* ;)

```
NOTE: sorting the list of files in the --files-from input helps rsync to be more efficient, as it will avoid  re-visiting  the  path
              elements  that are shared between adjacent entries.  If the input is not sorted, some path elements (implied directories) may end up
              being scanned multiple times, and rsync will eventually unduplicate them after they get turned into file-list elements.

```

*** If you don't want to sync everything in the list at one time, you can comment out certain lines by placing **#** at the beginning of those lines.

---

### Post by samwillc on 2014-03-02
Thanks to everyone, especially the part about the file list, that was very helpful. So I've created a file:

```

#.backmeup.sh in home folder
#!/bin/bash
sudo rsync -avr --delete --progress --files-from=/home/sam/.rsync-include.txt / /media/SEAGATE

```

and another:

```

#.rsync-include.txt in home folder
/home/sam/Android
/home/sam/C++
/home/sam/Documents
/home/sam/dosbox
/home/sam/Downloads
/home/sam/Drupal
/home/sam/Java
/home/sam/Music
/home/sam/Open\ University
/home/sam/OSX
/home/sam/Pictures
/home/sam/Programming
/home/sam/Python
/home/sam/Videos
/home/sam/Win7
/home/sam/Work
/home/sam/.dosbox
/home/sam/.backmeup.sh
/home/sam/.bash_history
/home/sam/.bashrc
/home/sam/.bash_profile
/home/sam/.fonts
/home/sam/.rsync-include.txt
/home/sam/.Xmodmap
/home/sam/.xinitrc
/etc
/usr/local
/usr/share/bluej
/opt

```

Ran:

```

sudo bash .backmeup.sh

```

And hey presto! Copied the files I wanted, recursively, and keeping permissions. I thought this is pretty far from dynamic, so I tried:

```

sudo rsync -avr --delete --progress --dry-run --files-from=/home/sam/.rsync-include.txt / --exclude=".*" /media/SEAGATE

```

with my txt file looking like this:

```

/home
/home/sam/.dosbox
/home/sam/.backmeup.sh
/home/sam/.bash_history
/home/sam/.bashrc
/home/sam/.bash_profile
/home/sam/.fonts
/home/sam/.rsync-include.txt
/home/sam/.Xmodmap
/home/sam/.xinitrc
/etc
/usr/local
/usr/share/bluej
/opt

```

...as I thought I want everything in home except for certain files/folders beginning with a dot, but I want to keep SOME of them. However, the above --exclude just excluded everything beginning with a dot. I thought the include-files (i.e. /home/sam/.dosbox) might override this and exclude everything beginning with a dot apart from things specified on my list. I thought this would be a good idea in case I add folders to my home directory but forget to update rsync-include.txt.

Another part of me just says copy the whole lot in home, then when it comes to restore, just restore the bits you need. It's not like I'm gonna run out of space, all my files in total only clocks up to about 120GB and the external is 500GB.

Sam.

---

### Post by vasa1 on 2014-03-03
For what it's worth, I'm now using this:
```
rsync -r -t -v --delete --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/'TOSHIBA EXT'/BACKUP/ &> $(date +%s)rsync.log
```where **$(date +%s)** adds a timestamp in epoch format.

---

### Post by samwillc on 2014-03-19
My script doesn't seem to be doing what it's supposed to be doing. This is it:

```

sudo rsync -av --delete --progress --files-from=/home/sam/.rsync-include.txt / /media/SEAGATE

```

I deleted a bunch of music from 'Music' folder (which is included in .rsync-include.txt), when I run the above script again, the music I deleted is still on the destination drive. I thought it would be automatically deleted in order to keep a exact mirror of my internal drive? In terminal:

```

sam@sam-pc:~$ sudo bash .backmeup.sh
building file list ... 
27 files to consider
home/sam/
home/sam/.backmeup.sh
         105 100%    0.00kB/s    0:00:00 (xfer#1, to-check=24/27)
home/sam/Music/

sent 730 bytes  received 37 bytes  1534.00 bytes/sec
total size is 7465  speedup is 9.73

```

The folders of music are still on my SEAGATE drive.

Owner/group of music folders = sam/sam, both are ext4 drives, all music folders are 700. Any ideas?

Sam.

**EDIT**

Seems I needed to add 'r' to my script i.e.

```

sudo rsync -avr --delete --progress --files-from=/home/sam/.rsync-include.txt / /media/SEAGATE

```

i though 'a' meant archive which includes 'r' already but makes a difference for me.

---

### Post by Dave_L on 2014-03-19
> i though 'a' meant archive which includes 'r' already but makes a difference for me.

>   -a, --archive
              This  is equivalent to -rlptgoD. It is a quick way of saying you
              want recursion and want to preserve almost everything  (with  -H
              being  a  notable  omission).   [B]The  only exception to the above
              equivalence is when --files-from is specified, in which case  -r
              is not implied.[/B]

              Note  that  -a  does  not  preserve  hardlinks,  because finding
              multiply-linked files is expensive.  You must separately specify
              -H.

[http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html)

---

### Post by samwillc on 2014-03-19
@Dave_L, thanks for pointing that out, explains exactly what happened in my case.

---

