---
title: "[SOLVED] Complicated rsync question"
date: 2008-02-20
forum: General Help
---

### Post by hackle577 on 2008-02-20
I have an external HDD that I use to backup my home dir. The command I use for the backup is:

```
rsync -a --delete --exclude=".*" /home/adam/ /media/Seagate/backup/
```

As you can see, I've excluded all hidden dirs and files, and the --delete flag tells rsync to delete files on the receiving side that aren't on the sending side. The problem is, I also have several other operations taking place in the backup script, namely:

```
cp -u /home/adam/.conkyrc /media/Seagate/backup/
mv /media/Seagate/backup/.conkyrc /media/Seagate/backup/conkyrc

cp -ru /home/adam/.tomboy /media/Seagate/backup/
mv /media/Seagate/backup/.tomboy /media/Seagate/backup/tomboy
```

Those create a non-hidden file "conkyrc" and a non-hidden dir "tomboy" in the same backup folder. 

HOWEVER, the problem is that when rsync sees these two things during its run, it notices they aren't on the sending side and deletes them, which results in them being written to the disk over and over again when they don't need to be. What I would like to find out is if there's some sort of exclude option for the --delete switch which would make rsync ignore the conkyrc file and tomboy directory. 

I've looked through the man page for rsync, but I'm afraid the solution, if there is one, is over my head. I could just take out the --delete altogether, but then I would have an unnecessary buildup of old files on my external drive.

Solutions?

---

### Post by p_quarles on 2008-02-20
I can think of a couple:
1) Instead of excluding files with a regular expression (i.e., ".*") try using an exclude file that specifies which directories you specifically want it to ignore.

2) Create a separate directory on the external drive, say /media/Seagate/backup-hidden, and send .conkyrc and.tomboy to that.

---

### Post by astrotech226 on 2008-02-20
You can also use --include to override excludes if they come first in the command.  Try this:

rsync -a --delete --include=".conkyrc" --exclude=".*" /home/adam/ /media/Seagate/backup/

---

### Post by hackle577 on 2008-02-20
OK, I got it working properly, but now I'm getting a few errors.

rsync is failing to delete files and set modification times. "ls -l /media" gives:

```
total 12
lrwxrwxrwx 1 root root    6 2008-01-15 12:31 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-01-15 12:31 cdrom0
lrwxrwxrwx 1 root root    7 2008-01-15 12:31 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2008-01-15 12:31 floppy0
drwxr-xr-x 3 adam root 4096 2008-02-20 10:48 Seagate

```

I am the owner, so I'm not sure what's causing this.... am I missing something?

---

### Post by astrotech226 on 2008-02-20
This should delete and update access times.  Add a "-v" in your command and when you run it, it will display which files it is updating/copying and which ones it is deleting.

```
rsync -a -v --delete --include=".conkyrc" --exclude=".*" /home/adam/ /media/Seagate/backup/
```

If this still doesn't work, try to perform the same rsync to another local directory like /home/adam-bakup and see if the files delete/update correctly.  Just out of curiosity, is the external drive the same filesystem type as /home/adam?  Like ext3?

---

### Post by hackle577 on 2008-02-20
Ahh, sorry. I should have been more specific. 

When it tried to delete the extraneous files and update mod times, rsync outputs that my external drive is a "read-only filesystem", which must mean that I don't have permissions to write to it somehow, even though I am the owner. Both my internal and external drives are ext3.

EDIT: Ok, nevermind I got it working. Marking as solved....

---

### Post by SumnerBoy on 2008-02-20
Hi - sorry to jump on this thread but I am setting up my backup routines using rsync from my ext3 HDD to an NTFS external USB drive. I am using the following rsync command...

rsync -auv --delete --exclude-from=/etc/backup/exclude /src /dst

I was assuming the -a flag would ensure all permissions and ownerships were copied across but all files/dirs are copied with the root owner/group.

Is this something to do with the fact the external drive is not ext3? What would happen if I needed to restore from my backup? All my permissions would be lost - correct?

---

### Post by astrotech226 on 2008-02-20
Yes, going from ext3 to ntfs you will most likely lose some of the permissions/ownership you are wanting to keep,  I have seen scripts that tar up the ext3 directories and then archive those to overcome that type of problem.

---

