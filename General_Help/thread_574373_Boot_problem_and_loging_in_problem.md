---
title: "Boot problem and loging in problem"
date: 2007-10-12
forum: General Help
---

### Post by paulie69 on 2007-10-12
Hey guys i just installed Ubuntu 7.04 and i need some help big time, i don't know what iv done but i think it's something to do with the samba smb.conf file. while i was setting up a domain controller i must have changed something that it did not like because now when i boot my system i get some errors and it asks me to enter the root pass, after entering that it comes to a command line but i don't know how to fix it so i just type exit and it brings me to the login.

Here is a log file from /var/log/fsck/checkfs

Log of fsck -C -R -A -a 
Sat Oct 13 08:41:51 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  e2fsck: Cannot continue, aborting.


fsck.ext3: No such file or directory while trying to open /dev/sda4

/dev/sda4: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Oct 13 08:41:51 2007


Now when i login to my account it displays an error:

"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

after that it logs me in ok.
I'm not sure what iv done wrong to upset the boot and permissions but I'm sure iv stuffed up somewhere lol.
I seen some other people had a problem like this but was different in ways.

Thanks, Paul

---

### Post by Pumalite on 2007-10-12
This you can ignore safely:

'"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

The rest I don't know.

---

### Post by paulie69 on 2007-10-13
Hey thx heaps for your reply but you can consider this problem FIXED with a format lol :), i just got sick of it because file sharing would not work nor would domain logins and it became very laggy. :mad:

Thanks again. Paul

---

### Post by Pumalite on 2007-10-13
You are welcome. Good luck.

---

