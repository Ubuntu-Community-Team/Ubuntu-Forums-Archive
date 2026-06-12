---
title: "aMule - can't open .temp?"
date: 2005-04-18
forum: General Help
---

### Post by Revan on 2005-04-18
Hi everyone!

This is my first post here, I'm a VERY newbie Ubuntu user and I write you this message because I didn't find anything like the problem that occured to me. I really hope I'm writing you every necessary information about my PC.

I've installed aMule and, since I want to use the same aMule .temp files that I use under WindowsXP, I decided to put them on a FAT32 partition that is usually mounted with the following line in /etc/fstab

/dev/sdb1	/mnt/share	vfat	user,auto,umask=000	0	0

This is my problem: as long as I launch aMule as root (writing <sudo aMule> in a terminal window), there is no problem... but when I try to launch aMule as a normal user, the program can't open my .temp files and can't resume downloading them.

I get this kind of error messages in aMule:

18/04/2005 22:25:21: Failed to open /mnt/share/Warez/eMule Temp/052.part.met

and then, some lines below,

18/04/2005 22:25:26: Can't open file '/mnt/share/Warez/eMule Temp/052.part'

But as a root it works really fine!

I can't understand what the problem could be... is there an error in the fstab configuration? Is it just a bug of aMule?

---

### Post by alastair on 2005-04-18
This is just a VFAT mount/permissions issue.

See : man mount

You could add the following options (alongside "user" etc.) to your fstab file :

uid=<your user uid>,gid=<your group id>

You can find your user/group id by typing "id" in a shell, as yourself.

/dev/sdb1 /mnt/share vfat user,auto,uid=N,gid=M,umask=000 0 0

---

### Post by Revan on 2005-04-19
Thanks for the reply.

I've tried to modify the fstab as you suggested, but it didn't work :(

My uid and gid are 1000.

Any other idea?

---

