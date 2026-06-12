---
title: "Emergency: Undo a &quot;rm -R&quot;..."
date: 2007-05-16
forum: General Help
---

### Post by billybag on 2007-05-16
I accidently removed a directory with the "rm -R" command. i do not know where my head was... i mean to chmod the directory. Is their any way at all that i can undo this?

please help

---

### Post by stchman on 2007-05-16
> **billybag said:**
> I accidently removed a directory with the "rm -R" command. i do not know where my head was... i mean to chmod the directory. Is their any way at all that i can undo this?

please help

You can try this:

[http://www.perlmonks.org/?node_id=106709](http://www.perlmonks.org/?node_id=106709)

In the future use Nautilus and then send the files/folders to the Trash Can.  You can recover the trash if you have not emptied it.

Good luck.

---

### Post by billybag on 2007-05-16
that link isn't working for me for some reason

---

### Post by qix on 2007-05-16
Is it an ext3 filesystem? If so, there is no way back.
If it is an ext2 filesystem, there may be help out there. Search google.

---

### Post by billybag on 2007-05-16
nevermind. i lied. it just took a long time

---

### Post by billybag on 2007-05-16
> **qix said:**
> Is it an ext3 filesystem? If so, there is no way back.
If it is an ext2 filesystem, there may be help out there. Search google.
i am not sure. i think it is ext3 :( how can i find out for sure though?

---

### Post by qix on 2007-05-16
In a terminal, write:
sudo mount -l

This will print the currently mounted partitions. Try to find the correct one (each line tells which device is mounted where, so you just need to find the line telling which is mounted where your file was placed.)
After the mount location, it says "type xxxx" where xxxx is the filesystem.

---

### Post by billybag on 2007-05-16
> **qix said:**
> In a terminal, write:
sudo mount -l

This will print the currently mounted partitions. Try to find the correct one (each line tells which device is mounted where, so you just need to find the line telling which is mounted where your file was placed.)
After the mount location, it says "type xxxx" where xxxx is the filesystem.
yeah it is ext3. damitall

---

### Post by qix on 2007-05-16
Too bad. I did the same some time ago (deleted all of my emails from the last 6 years). I searched google a lot, and found out the ext3 really deletes the file. So I'm rather sure you can't get it back.

btw, I was lucky and found a 1 week old backup!

---

### Post by strabes on 2007-05-16
Yeah, external hard drive backups are your friend. sbackup is great.

---

### Post by ricrac on 2007-05-16
The trash icon is basically just a pointer to a specific directory that's out of the way or hidden from view, such as ~/Desktop/Trash or ~/.gnome-desktop/Trash. When you drag a file to the trash can, you're really just moving it to that directory. 

Create or use a script or alias like this [http://directory.fsf.org/cn.html](http://directory.fsf.org/cn.html)  when using the terminal.  

Create or use an intelligent script or alias to force single interactive mode. (one yes answer required)

Use a replication backup hardlink system like snapback2.  You'd still want to script a rsync/flush before the delete to be auditable.

Use interactive mode. Be careful when doing dangerous tasks. Remember many people want the opposite, they want to be sure that the file is not recoverable when they hit delete.


I have used Ontrack and others in-house services but only for Novell and microshaft partition types, usually for physically hardware problems. Spindle, electronics, headcrash, etc.  Ontrack doesn't like ext3 for their software but many others I have not tried do.
Has anybody here tried any of these or other new data recovery packages?  Many come up in websearch. [http://www.datarecoverylinux.com/](http://www.datarecoverylinux.com/) [http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm) 

You probably already know this...if you ever do delete files "on your own system, don't do this at work" You should turn off the machine asap.  Do not shutdown, this will write loads of temp and log data to the disk potentially overwriting it.  Never boot to the "corrupted" drive again. Boot to cd or alternate harddrive.  Don't use any cd or system that automounts drives.  This could write .desktop files or lost&found dir corrupting existing data. Standard operating procedure for deletion or positive intrusion detection.  Overwriting is confined to the physical areas of mount points (this is very simplified overview).  Therefore use more mount points.  Home should be it's own mount.  Don't go too crazy but for a home system
/   root partition            leave "system" on one for easy tracking and rebuild
/   alt root                       have "dual boot" partition ready, usually 6gb suffices full installs
***This allows you to alternate partitions during new version installs instead of upgrades, some settings will be retained through separate home partition.  Mandatory for alternate OS installs.

/home/username        each username has it's own space
/home/username/documents each username has it's own space for critical work
/mysql-databases       databases should always reside on their own mount point
/webroot                        separate from system, potential for heavy file activity 
/video,/audio,/images  separate mounts for mimetypes, potential for heavy file activity 

The main key is to get logging, tmp and caching off the data drives.
If you delete files off a separately mounted "data" drive they can most likely be recovered.

---

