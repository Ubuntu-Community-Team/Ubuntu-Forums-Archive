---
title: "sharing mounted drives with samba"
date: 2006-10-26
forum: General Help
---

### Post by rhuarch on 2006-10-26
I am trying to set up a linux fileserver on a pc with 3 hard drives.  I got samba working just tonight, and started copying files over from my windows PCs.  The drive I installed linux to works just fine when I try to copy files to it, but the 2 drives I mounted to /mnt/firetree and /mnt/blackhand respectively (firetree and blackhand being the names of the drives/shares) are giving me problems.  I can browse to them from the windows PCs with no trouble but I can't actually copy anything to them.  it just gives me an error saying I may not have the permissions.  When I checked the samba share settings for those drives, it looks like I have them configured for read/write access. I am hoping someone can help me out with this problem  What I want to accomplish is to have my 2 mounted drives shared out via samba so that I can copy files to them as well.  Thanks in advance. ](*,)

---

### Post by ciscosurfer on 2006-10-26
Check out these points on the ubuntuguide.org wiki ::
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server)

---

### Post by rhuarch on 2006-10-26
> **ciscosurfer said:**
> Check out these points on the ubuntuguide.org wiki ::
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server)

That is the guide I used to set up samba in the first place.  The share I made from my home folder works perfectly, I can read/write/delete anything I want in that one.  The ones that don't work are the mounted 2nd and 3rd drives.  Would it work better if I mounted those drives into folders inside my home folder and then shared those?  I am extremely new to linux so mone of this is intuitive to me. Thanks.

---

### Post by dbott67 on 2006-10-26
Here's a thread on [how to mount SMB shares]("http://www.ubuntuforums.org/showthread.php?t=280473").

-Dave

---

### Post by rhuarch on 2006-10-27
> **dbott67 said:**
> Here's a thread on [how to mount SMB shares]("http://www.ubuntuforums.org/showthread.php?t=280473").

-Dave

That's not exactly what I am trying to do, although it is cool.  What I am trying to do is share out two extra drives that I mounted in linux.  I think the problem I am running into is that I am trying to share out the folders that the drives are mounted to and root owns those drives.  When I connect to my linux machine from a windows pc I can see all 3 shares.  I just can't write to the 2 shares that are my extra hard drives.  I think I am not explaining this well because I don't know linux well enough. ](*,)

---

### Post by Spano on 2006-10-28
I think you need to change ownership (chown) of blackhand and firetree.
In terminal try
```
sudo chown rhuarch /mnt/blackhand
```
the rhuarch part of the command is your computer user name.
now you should have write permmision.  Check these two threads for more detail:
[http://www.ubuntuforums.org/showthread.php?t=282459&highlight=chown](http://www.ubuntuforums.org/showthread.php?t=282459&highlight=chown)
[http://www.ubuntuforums.org/showthread.php?t=285801&highlight=chown](http://www.ubuntuforums.org/showthread.php?t=285801&highlight=chown)
Good Luck
Something else I notice is that in nautilus if you right click on  a folder one of the options on the drop down menu is _S_hare.  Try opening nautilus as root from the terminal (sudo nautilus), browse to blackhand and right click> _S_hare > Samba.

---

