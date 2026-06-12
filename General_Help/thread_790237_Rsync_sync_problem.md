---
title: "Rsync sync problem"
date: 2008-05-11
forum: General Help
---

### Post by Ganymedes on 2008-05-11
I am trying to copy from Windows XP Pro to Ubuntu 7.10 so that the end result would be a mirrored copy (meaning that everything is updated on the target as well deleted if the source has changed).

In the Windows world "robocopy.exe" does this elegantly with the /mir option. In Ubuntu I have tried to do this with rsync with some options - there is no mirror option - which I believe I have figured out. Although as a secondary problem, I do not think that the end result is a complete mirror.

But my first problem is that it just does not work. What happens are two things (in different cases, with different computers):

- there is a difference in number of files. I suspect that some files might have "illegal" characters in them and thus are skipped. It does not complain about these problems.

- rsync sometimes, in an abstract fashion, deletes files from the target and does not copy them immediately again. However, if you run it again then it copies them, but might delete some other files. I have checked the files and tried to give them new time stamps, but nothing like that seems to help.

So, if somebody has better suggestions than rsync or an update to rsync or something, I would be very interested to here about them.

**Here is how I mount:**
(no line feeds in reality)

sudo mount -t smbfs -o codepage=cp850,iocharset=utf8,username=user,password=password //192.168.1.2/myshare$ /mnt/my_server_files

**Here is how I copy:**
(no line feeds in reality)

rsync -v -r -u --delete-before /mnt/my_server_files/ /home/my_home_files/

---

### Post by mcarni on 2008-05-12
I'm a newbie so maybe what I'm going to say will completely make no sense.... :)

in the following forum they speak about an option that help when using rsync between ubuntu and windows maybe it helps also from windows to ubuntu:

[http://ubuntuforums.org/showthread.php?t=209724&page=5](http://ubuntuforums.org/showthread.php?t=209724&page=5)

> **kowal said:**
> From [http://www.samba.org/rsync/FAQ.html](http://www.samba.org/rsync/FAQ.html)

Quote:
copies every file
Another common cause involves sending files to an Microsoft filesystem: if the file's modified time is an odd value but the receiving filesystem can only even values, then rsync will re-transfer too many files. You can avoid this by specifying the --modify-window=1 option.

Works right with Fat32! ^^


hope this solves your rsync problem...

by the way, I've been trying to do the opposite of what you do, 
I have a folder on a samba share that I would like to keep synchronised with a Master folder on my ubuntu, this is supposed to be the destination folder as I see with Nautilus
smb://toshiba/E/BACK-UP_SU_TRISTAN

Me being a noob, I'm using grsync but I'm stuck because when I copy and paste the above for the destination folder, rsync just doesn't work.
I guess I'm forgetting something silly, like mounting the samba shares...
I tried to mount the samba share but not sure, could you shed some light on the mount command you are using?

thank you so much

M

---

### Post by Ganymedes on 2009-06-21
If anybody is interested the problem that I describe above was resolved with newer version of Ubuntu. I think after 8.04 (or possibly 8.10) it works correctly with rsync -urv -command that I describe above (used mostly with NTFS on Windows (FAT32 - not used much = not sure).

---

