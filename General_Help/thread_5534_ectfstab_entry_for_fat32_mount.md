---
title: "ect/fstab entry for fat32 mount"
date: 2004-11-19
forum: General Help
---

### Post by rikkulinux on 2004-11-19
[FONT=Book Antiqua]OK, I've read every post regarding fat32 mounts and I still can't really find the answers I'm looking for, so here it goes...

I can get my fat32 partition opened and can open files in it, but can't write to it (or save files to it).  I have the following in my fstab:

/dev/hda1	/mntpoint	vfat 	users,umask=777		0 	0

I've seen a million different things to put in this fstab line, so eventually I'll probably be able to figure it out, but the main thing I'm wondering, is what do all these things mean.  For example 'defaults', users, auto, noauto, and the two 0's at the end.  Any other things you would put there that you can tell me about would be good also (I've seen gid / uid and have no idea what that is).

Also, can someone who has a lot of experience writing to FAT32 using linux talk a little about the risks?  Is it any riskier than writing to an etc partition?  I have a drive I want to share between Win and Ubuntu that will be used often by both, so I want to make sure there won't be any problems.

Thanks in advance.

-rikku

[/FONT]

---

### Post by Razvan on 2004-11-19
your line looks good!

except the 777 - you shouldt even be ablt to read files! change it to 000 fot full read/write/exec acces for everybody 

here is, how the numbers go :

0 full
 +1 for no exec
 +2 for no write
 +4 for no read

first number is for the owner (the one that mounts is - usually root)
second for the owners group
third for the rest

add user and users if you want to mount yourself, auto to mount automatically at boot

the two 0s or 1s in the end are to indicate how often and in what order to check...dunno just leave them at 0 ;-)

welcome, Martin

---

### Post by FLeiXiuS on 2004-11-19
yes, umask is the opposite of chmod.

---

### Post by mr_ed on 2004-11-19
I see you made your way here too, rikku.  ;)

I answered your post on usalug last night.

---

### Post by rikkulinux on 2004-11-20
[FONT=Book Antiqua]Yep,  Made my way here.  Your reply on the other forum helped me get as far as I did.     I was using Debian for a while before finding Ubuntu a few weeks ago.  Debian was getting to be too much work and Ubunto has been great so far.  I think I'll stick around this forum for a while, at least until I can start answering other people's posts.  :)

I understand the number system for permissions, but didn't know umask was opposite of cmod...

I'm still wondering if anyone has problems using vfat file systems in linux on a regular basis.  I don't want to get too deep into this and have to start everything over again....

Thanks for all the help.

[/FONT]

---

