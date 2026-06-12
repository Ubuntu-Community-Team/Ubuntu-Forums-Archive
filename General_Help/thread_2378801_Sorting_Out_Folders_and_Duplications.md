---
title: "Sorting Out Folders and Duplications"
date: 2017-11-27
forum: General Help
---

### Post by webmanoffesto on 2017-11-27
Browsing around on this laptop I see I have
/tom
and I have 
/home/tom (the older folder?)

I am now booted into the older install, Debian GNU/Linux 7, and I see that "Places / Home" brings me to "/home/tom". So I guess that is the older of the two.

I've been through a few installs on this laptop. I'm currently in the process of repairing the Grub. That means I'm currently booted into the old install, in here I see there is a difference between the files in 
/tom/Documents/Artisans.Asylum
as opposed to 
/home/tom/Documents/Artisans.Asylum (apparently, the older version)

I once had only one partition (maybe two?)
Later I correctly partitioned the HD with Root, Home, and Swap

This seems to be the older folder because it has less in it
/home/tom/Documents/Artisans.Asylum

With this being the newer
/tom/Documents/Artisans.Asylum
The "modified" dates tell me that is correct.

How can I safely combine
/tom/Documents/
and
/home/tom/Documents/
 without overwriting newer files

[[IMG]http://en.zimagez.com/avatar/differentfilesuserdocumentsvshomeuserdocuments20171127n010.png[/IMG]]("http://en.zimagez.com/zimage/differentfilesuserdocumentsvshomeuserdocuments20171127n010.php")

[[IMG]http://en.zimagez.com/avatar/differentfilesuserdocumentsvshomeuserdocuments20171127n02.png[/IMG]]("http://en.zimagez.com/zimage/differentfilesuserdocumentsvshomeuserdocuments20171127n02.php")

Writing while using the older install on this laptop
Debian GNU/Linux 7

---

### Post by oldfred on 2017-11-27
You cannot guess or it will lead to issues.
Probably best to fully back up both copies, so if you delete wrong one you still have it.

You can just copy files from one folder to another, it will offer to overwrite and on each ask if you want to replace and you can compare dates & sizes. 
Or you can use rsync and with its switches have it automatically overwrite with file with newest version.

I am no expert on rsync so I make these the first lines in every rsync file I create.
See man rsync for entire list but it is huge.
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

And another is -n so you can test command without actually running it.
       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync) 
    
And this is the command I use to copy to my flash drive labeled & mounted at data64. I have separate line for every folder in a bash file.
rsync -aruvP /mnt/data/Documents /media/fred/data64

---

### Post by untrustytahr on 2017-11-27
There is a nifty tool called FSLint.  It will handle deduplicating as well as file name clashes.

Alternatively, you write a script that hashes the files, pipe it through sort/uniq for deduping.  I'd have to think about file name clashes before offering a suggestion since a file could have different versions but the same name in different directories.

---

### Post by Impavidus on 2017-11-27
It's not normal for the directory /username to exist. The user's home directory should be /home/username (or something similar; on big systems the admins may add another level in the hierarchy). And the old and new systems have at the very least different root partitions and other partitions may not have been mounted at the same location. So the fact that we see /home/tom and /tom on the old system, with old files in /home/tom and newer in /tom, doesn't tell us anything about your new system. Investigate that first. Which one of these is your /home partition, which one is on the root partition of the old install, what is on the root partition of the new install, what is in the /etc/fstab of the new install.

For the actual copy, use rsync as oldfred suggests. I'm not an expert on rsync, but I think you need the options -a and -u (and using -ar seems redundant, as -a implies -r). Make sure you have enough disk space available for the copy. It seems the root partition of your old install is quite well-filled, but I don't know which of these directories is on that partition.

---

### Post by webmanoffesto on 2017-11-28
Thanks,

I ran
```
rsync -aruvPt --exclude-from='/exclude_me.txt' /tom/ /media/1TB_ExtHD/Root_Tom

```
with exclude_me.txt
```
.ccache
build
.java
.gvfs
.xsession-errors
.cache
Downloads
.config
```


Does this response say that the "rsync" completed correctly, with all the files copied?
It says
"some files/attrs were not transferred"

```
testing/
testing/testing.file.txt
           5 100%    0.02kB/s    0:00:00 (xfer#264774, to-check=0/460152)

sent 285659848731 bytes  received 5489227 bytes  35903391.94 bytes/sec
total size is 426747163430  speedup is 1.49
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
bash: base: command not found
bash: a: command not found
bash: would: command not found
bash: and: command not found
bash: rsync.copy.files.to.exthd..v.2017.11.27.n01.sh: line 22: syntax error near unexpected token `('
bash:  rsync.copy.files.to.exthd..v.2017.11.27.n01.sh: line 22:  `                    would include only foo/bar.c (the foo/ directory  must be'
```

More complete output [https://www.hastebin.com/rahutexepe.coffeescript](https://www.hastebin.com/rahutexepe.coffeescript)

---

### Post by webmanoffesto on 2017-11-28
Here's a related question, I moved the script to root "/" so I could copy files in /tom. Was that necessary? Is it possible to run a script in /tom (e.g. /tom/script.sh) and rsync /tom? So the script would be copying itself over to another location?

---

### Post by oldfred on 2017-11-28
Do not know, hopefully someone else does.

I do know trailing slashes matter & I have to reread my notes or man page each time I create a new one.
 man rsync has explanation of trailing /. these are the same, trailing / copies contents:
 rsync -av /src/foo /dest
 rsync -av /src/foo/ /dest/foo 

If you copy to NTFS, you lose all ownership & permissions. If just user data, you can reset those relatively easily. But if system files, just about impossible to reset as they vary too much.

---

### Post by webmanoffesto on 2017-11-29
I understand that
[FONT=courier new]rsync -aruvPt --exclude-from='/exclude_me.txt' /tom/ /media/1TB_ExtHD/Root_Tom
[/FONT]copies the contents of the folder "/tom" to the folder Root_Tom, the path to that folder is "/media/1TB_ExtHD/"

---

