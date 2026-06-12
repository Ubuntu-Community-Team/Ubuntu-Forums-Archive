---
title: "updatedb and locate commands"
date: 2008-02-13
forum: General Help
---

### Post by goodrench on 2008-02-13
I am having some trouble with the updatedb command.
I can run it and it looks like it is indexing the media/data folder (which is on another partition)
But when I try to use the locate command it only finds files in my home directory.
I have edited the /etc/updatedb.conf file so that it will not exclude my media folder.
It was working great until a little while ago.
I am not sure if another program broke this one or maybe indexing is turned off for the partition.
Has anyone else had this problem?

---

### Post by cadebou on 2008-02-24
Here you have the answer:

[http://ubuntuforums.org/showthread.php?t=697468](http://ubuntuforums.org/showthread.php?t=697468)

Good luck, Pau.

---

### Post by goodrench on 2008-02-24
Thank you for the reply but I did that already.
Refer to first post.
Line 4.

---

### Post by bwhite82 on 2008-02-24
You need to run the command with sudo to index everything. You also need root priveleges when locating something (not in your home dir) as well.

-Cheers

---

### Post by goodrench on 2008-02-24
> **Soldierboy said:**
> You need to run the command with sudo to index everything. You also need root priveleges when locating something (not in your home dir) as well.

-Cheers

This is true.
updatedb will not even run without sudo.

```

drew@laptop:~$ updatedb
updatedb: fatal error: You are not authorized to create a default slocate database!
drew@laptop:~$ 

```




I have been using updatedb for about six months and it works great.
I am not sure what happened but it just will not locate files on my /media/data drive anymore.

---

### Post by bwhite82 on 2008-02-24
Silly question, is it mounted when you updatedb or locate?

---

### Post by goodrench on 2008-02-24
yes it is.

---

### Post by goodrench on 2008-02-24
Now for my silly question.
Does updatedb use any files in the home directory?
I have reinstalled my system and I am still having trouble with this.
When I reinstalled I did not format my home partition.
Maybe this will help diagnose this?

---

### Post by bwhite82 on 2008-02-24
Could you post the contents of your 'updatedb.conf' please? Also, I know you already stated that you are indeed using sudo to update the database, but are you also using it to locate things?

Edit: On my system, updatedb is indeed indexing the contents of my home folder.

---

### Post by goodrench on 2008-02-24
I use updatedb to update the database and then when I want to search for a file I use

```
locate <name of file>
```

Here is my updatedb.conf
```


# This file sets environment variables which are used by updatedb

# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
export FINDOPTIONS
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf"
export PRUNEFS
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs"
export PRUNEPATHS
# netpaths which are added
NETPATHS=""
export NETPATHS
# run find as this user
LOCALUSER="nobody"
export LOCALUSER
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10
export NICE
# cron.daily: I/O priority
# 1 for real time, 2 for best-effort (3 for idle is only allowed for root!)
IONICE_CLASS=2
export IONICE_CLASS
# 0-7 (for IONICE_CLASS 1 and 2 only), 0=highest, 7=lowest 
IONICE_PRIORITY=7
export IONICE_PRIORITY


```

---

### Post by bwhite82 on 2008-02-24
Alright, on my system (Debian Testing) I have to use 'sudo locate' for any file outside of my home directory. I also notice that your home directory is set to not be indexed. Remove 'alex' from that config file if you wish it to be indexed as well.

-Cheers

---

### Post by goodrench on 2008-02-24
sudo locate does not search other directories on my ubuntu 7.10
It does search my home directory using locate and sudo locate.
I removed alex from the config file and ran sudo updatedb -v and then "locate *.iso" and then 'sudo locate *.iso"
both results the same.
Only shows files in my home directory.

---

### Post by bwhite82 on 2008-02-24
Hmm, well I gave it all I can, I am at a loss. Perhaps someone with more knowledge than I can offer some advice. Good luck. If either yourself or someone else figures it out, I'd be interested in knowing the solution. I love learning new things on linux.

-Cheers

---

### Post by goodrench on 2008-02-24
Thanks very much for the help.
Maybe someday I will format My home partition and see if that works.
Thanks again for you help.

---

### Post by goodrench on 2008-02-29
Solved.

I was able to solve the issue with one command.


```
sudo locate -u
```

Not sure why this worked, but everything is good now.

---

### Post by Topstar on 2008-04-09
> **goodrench said:**
> Solved.

I was able to solve the issue with one command.


```
sudo locate -u
```


Have an issue with updatedb as well (won't exclude nfs share) but i'm unable to find anything on the -u-parameter.

```
sudo locate -u
locate: invalid option -- u
```

---

