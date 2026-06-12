---
title: "What is GVFS? I get permission denied when I rsync. Why?"
date: 2008-05-12
forum: General Help
---

### Post by Roasted on 2008-05-12
When I rsync my home directory to a spare hard drive in my system, it immediately comes up with something about gvfs and permission denied.

Why? Is that bad? Should I ignore it? Is GVFS a new thing in Hardy? I don't recall it in Gutsy... and I've had the same rsync setup for the last 2-3 years...

---

### Post by Roasted on 2008-05-12
so, I'm reading GVFS is new to Hardy. I assume that it's not important that GVFS gets rsynced when I run my script. Should I throw in an exclude tag so I don't get this error?

---

### Post by buntunub on 2008-05-12
[GVFS]("http://en.wikipedia.org/wiki/GVFS")

Its not a new Hardy thing. Its a new GNOME thing.

---

### Post by Roasted on 2008-05-12
Okay... so... how do I deal with this so my rsync is not effected (or kicking out any errors to me)??

I want to run my rsync command without it barking at me. What can I do?

---

### Post by gwi on 2008-05-16
I have a directory entry in a home directory that looks like this when listed with ls -la:
```
d?????????  ? ?      ?          ?                ? .gvfs
```

In another user's home directory it looks normal, and has the user as owner and primary group.

The directory entry shown above is inaccessible, even by root. rsync shows the following:
```
rsync: readlink "/home/username/.gvfs" failed: Permission denied (13)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
```
 Why is that directory entry there, why does it look so strange, and how can I fix it?

---

### Post by mannheim on 2008-05-16
> **Roasted said:**
> When I rsync my home directory to a spare hard drive in my system, it immediately comes up with something about gvfs and permission denied.

Why? Is that bad? Should I ignore it? Is GVFS a new thing in Hardy? I don't recall it in Gutsy... and I've had the same rsync setup for the last 2-3 years...

In Hardy, when a user has a gnome session running, the directory ~/.gvfs is a mountpoint for some sort of filesystem involving fuse. Since it is a mountpoint, nothing is actually stored on disk under ~/.gvfs in the filesystem you are backing up, so you can exclude it with some filter rule like "exclude /*/.gvfs". It will be recreated if needed, in my experience.

This is a common problem with fuse-mounted files systems I think: not even root can access them, unless a configuration setting is changed somewhere for the mount. rsync throws up that error even if given the --one-file-system option (so it doesn't descend past the mountpoint).

---

### Post by Roasted on 2008-05-16
So, I can't read/access gvfs. Okay. How can I exclude gvfs from my script so I can avoid attempting to copy it (which inevitably fails anyway). ??

---

### Post by mannheim on 2008-05-16
The syntax depends how you are running it, but if you are backing up all home directories for all users, it could be something like

```
sudo rsync -ax --exclude='/*/.gvfs' /home/ /media/big-drive/backup-of-home/ 
```

For an individial user:

```
sudo rsync -ax --exclude='/.gvfs' /home/joe/ /media/big-drive/backup-for-joe/ 
```

I'm just typing this live, so I may have mistyped these.

---

### Post by gwi on 2008-05-18
Can someone explain why ls can't even show the directory entry .gvfs normally?

---

### Post by mannheim on 2008-05-18
> **gwi said:**
> Can someone explain why ls can't even show the directory entry .gvfs normally?

There is a bug in gvfs, reported [in launchpad]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/212789"), which puts it into that state (which I don't understand). When the bug is not showing itself, the usual behavior is:

```

ls -ld .gvfs
dr-x------ 2 joe joe 0 2008-05-14 08:23 .gvfs    [COLOR="Blue"]# no problem for owner[/COLOR]

sudo ls -ld .gvfs
ls: cannot access .gvfs: Permission denied    [COLOR="Blue"]# root can't access joe's fuse-mounted filesystem[/COLOR]

```

---

### Post by Roasted on 2008-05-18
Is it a problem if I just let the rsync fire out the gvfs error and rsync anyway?

---

### Post by Roasted on 2008-05-19
All right. This is enraging me. It won't even delete the files it should, despite the fact I have a --delete tag in there.

Can anybody help me fix this?

I'm starting to miss the days of Gutsy... back when things just worked. :(

edit - okay, I just did a man rsync and noticed the exclude tag. I threw it in my script. My script is as follows.



#!/bin/bash
sudo mount /dev/sdb2 /media/share
sudo mount /dev/sdc1 /media/drivec
sudo rsync -a --progress --delete --exclude=.gvfs ~/ /media/share/jason
sudo rsync -a --progress --delete --exclude=.gvfs /media/share /media/drivec

It worked perfectly. Now when I rsync, it deletes stuff it should. Before, my --delete tag seemed to not work due to the gvfs errors I got. It simply said "OI Error - skipping file deletion." Now it works great.

Easy fix. But let's hope the bug gets fixed so I can someday take out the exclude tag and just run a straight up rsync command to back my stuff up. :)

---

### Post by zadirion on 2008-06-13
you can fix it this way:
```

umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs
```

for some reason only some users' home dir have unaccessable .gvfs .

---

### Post by Zack McCool on 2008-07-10
This will also (obviously) affect an rsnapshot backup.  For that, add an exclude line in /etc/rsnapshot.conf like this:

```

exclude      .gvfs

```

in the excludes section, and the error will go away.

---

### Post by zedcar on 2008-08-04
Preferring as I do the easy way out with a nice UI... I use Grsync for backups & I found the same problem with gvfs. Since all I was trying to was to back up my data in /home (and the mounted data on a network drive is already backed up) I was able to simply select the option 'Do not leave filesystem' in Grsync to stop these errors (and stop it trying to back up the whole company network...)

But if you DO want to back up a network share, I think Grsync lets me do so if before I try to run the backup, I have accessed the share and entered my network password. I guess that's the expected behaviour.

---

### Post by sbergman27 on 2008-08-07
Weird problem with one of the gvfs packages.  It acts fine for the owner, but gives weird permissions and permission denied to root.  Quite bizarre.  Bring up synaptics, search on "gvfs" and reinstall the 4 or so packages that show to already be installed.  This has fixed it for me and an opensuse guy who had the problem recently.

---

### Post by glenmo on 2008-11-04
well, in case anyone was wondering... i did this:

rsync -r -t -v --progress -u -c -l -z -b --exclude=*.gvfs // /media/disk/backup/

and my system froze at some point... had to do a hard restart,  everything came back up the same... and i have a 5.4 gb directory with all the folders, in alphabetical order up to h 

i guess it died before finishing, but how do i find out what's wrong?

i'll try it out again and report back...

---

### Post by dslehman on 2009-01-06
I had the same permission error:

root@lennon:~# ls -l .gvfs 
ls: cannot access .gvfs: Permission denied
root@lennon:~# ls -ld .gvfs 
ls: cannot access .gvfs: Permission denied
root@lennon:~# file .gvfs
.gvfs: ERROR: cannot open `.gvfs' (Permission denied)

I then ran:

root@lennon:~/bin# aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0

Then it was instantly fixed:

root@lennon:~# ls -ld .gvfs
drwx------ 2 lehman cis-unix 4096 2009-01-04 05:28 .gvfs


Odd.

Thanks all.

---

### Post by woodenfox on 2009-03-20
> **dslehman said:**
> I had the same permission error:

root@lennon:~# ls -l .gvfs 
ls: cannot access .gvfs: Permission denied
root@lennon:~# ls -ld .gvfs 
ls: cannot access .gvfs: Permission denied
root@lennon:~# file .gvfs
.gvfs: ERROR: cannot open `.gvfs' (Permission denied)

I then ran:

root@lennon:~/bin# aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0

Then it was instantly fixed:

root@lennon:~# ls -ld .gvfs
drwx------ 2 lehman cis-unix 4096 2009-01-04 05:28 .gvfs


Odd.

Thanks all.

THANK YOU! X 100!
This is the official solution:

sudo aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0

---

### Post by OptikKnight on 2009-04-14
We're encountering this problem when trying to sync a user's account during logout. In our case, the best solution is to:
```
umount $homedir/.gvfs
```
...as root. 

For syncing while the user is still logged in, an rsync exclusion seems most sensible. 

Reinstalling the gvfs packages each time I want to sync is definitely not a good option. I would not recommend classifying it as an "official" solution in any automated systems.

---

### Post by Cresho on 2009-07-10
8)

---

### Post by brallan on 2009-07-24
Can one use a user-defined mountpoint in gvfs-mount such as /mnt/networkdrive or /media/LANdisk to avoid problems? I am a bit frustrated, since gvfs mounts the disk without errors but mount-t cifs and smbmount, which would allow me to do this, have systematically [given me error messages where the "Connect to server" option in the GUI has not.]("http://ubuntuforums.org/showthread.php?t=1032394").

But the point of mounting the network drive is in large part, to give me someplace to back up my /home/username directory!!!! so find grsync recursively writing the filesystem itself inside the backup is alarming.

anyone using KDE able to do this easily? I am told there is something called kio which does this with no problems.

---

### Post by kastanedowski on 2009-08-25
Hi, got .gvfs': Permission Denied

when trying to repair my /home/ permissions

"user's home .dmrc file is being ignored ubuntu"


I am trying this possible solution but this error keeps appearing:

sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
I am really new in this and I am thinking to re-intall again,any comments? thanks!

---

### Post by mcduck on 2009-08-25
> **kastanedowski said:**
> Hi, got .gvfs': Permission Denied

when trying to repair my /home/ permissions

"user's home .dmrc file is being ignored ubuntu"


I am trying this possible solution but this error keeps appearing:

sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
I am really new in this and I am thinking to re-intall again,any comments? thanks!

Only use "sudo" when you really need to run things as root. (and never with graphical programs, which is probably what caused your problem in the first place. Always use "gksudo" when launching graphical apps)

```
sudo chown -R ricardisimo /home/ricardisimo
chmod -R 700 /home/ricardisimo
chmod 644 /home/ricardimo/.dmrc
```

(You don't need "sudo" to change permissions of files you already own)

---

### Post by prylux on 2009-10-02
My simple solution was to open a terminal and enter

[INDENT]sudo umount /home/*user*/.gvfs[/INDENT]

Then open the home folder in the GUI and view hidden files
Right click on .gvfs and change the permissions to "Create and Delete Files"

After that you should have access to 

[INDENT]sudo chmod 644 /home/*user*/.gvfs
sudo chmod -R 700 /home/*user*[/INDENT]

---

### Post by mac357 on 2009-11-04
> **prylux said:**
> My simple solution was to open a terminal and enter[INDENT]sudo umount /home/*user*/.gvfs[/INDENT]Then open the home folder in the GUI and view hidden files
Right click on .gvfs and change the permissions to "Create and Delete Files"

After that you should have access to[INDENT]sudo chmod 644 /home/*user*/.gvfs
sudo chmod -R 700 /home/*user*[/INDENT]

Your solution helps also if you have a permission problem with. gvfs folder while trying to backup systempartition with fsarchiver.
fsarchiver is a super linux tool for filesystem backup even ext4 is supported !

---

### Post by AlexanderDGreat on 2010-09-08
Thanks for this post. Here's my rsync command:

```
sudo rsync -avz --delete --exclude-from '/media/backups/exclude.txt' /home/ /media/backups/home/
```

exclude.txt: .VirtualBox .gvfs

It works great.

---

### Post by Spirobranchus on 2010-11-24
> **zadirion said:**
> you can fix it this way:
```

umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs
```

for some reason only some users' home dir have unaccessable .gvfs .
This still works! Thanks!

---

