---
title: "[SOLVED] Can't start Gnome - unable to create ~/.gnome2 directory"
date: 2008-03-24
forum: General Help
---

### Post by lowracer on 2008-03-24
Tried to log out of gnome to clear something funky that was happening on the screen, it wouldn't log out so I hit CTRL-ALT-BACKSPACE.  When I went to log back in, I got the "session only lasted less than 10 seconds" screen.  Looking at the details of the ~/.xsession-errors file, it says:

/etc/gdm/Xsession: Beginning session setup...
(gnome-session:4238 ) libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: File exists
Could not set mode 0700 on private per-user gnome configuration directory '/home/mark/.gnome2_private/': Read-only file system 

When I check to see what is mounted, my home directory is shown as:

/dev/sdb3 on /home type ext3 (rw)

doing an ls shows the correct files for my home directory, and df shows all the usual directories I would expect to see.

not sure what to do here...  Any clues?  

I was running a crossFTP server on port 21 to allow a colleague read-only access some data files on my system.  Despite having the FTP server set to only allow one specific user to log in,  I wonder if I've been hacked somehow?  I did notice a dozen or so failed log in attempts from a non-allowed user.

Thanks,
-Mark

---

### Post by dannyboy79 on 2008-03-24
is your /home mount point full???? this is normally the cause if you know for sure that you can write to it.

df -h 
will show you whether it's at 100%. If that's not it then I am not sure what to say.

---

### Post by lowracer on 2008-03-24
sorry, forgot to mention home is at 87% utilized which is normal.

Did a cd to /home, then ls:

[1535435.572561] EXT3-fs error (device sdb3) : ext3_readdir: directory #2 contains a hole at offset 0.

cd back to /home/mark, then ls -lash,  I see lots of ? characters on many of the files, including .gnome2.  For instance file size is ?, permissions are ?---------, all other fields including owner, date, are ?

would this be something that fsck could fix?

---

### Post by lowracer on 2008-03-24
Apparently this was a loose SATA cable to the hard drive containing my /home partition.  I shut down, reseated the cables, then powered back up.  fsck ran automatically, recovered the journal, and now the system is back up.

---

### Post by dannyboy79 on 2008-03-24
can you mark the thread as solved please.

---

