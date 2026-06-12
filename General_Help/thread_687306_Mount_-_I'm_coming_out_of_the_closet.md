---
title: "Mount - I'm coming out of the closet"
date: 2008-02-04
forum: General Help
---

### Post by pumahalen on 2008-02-04
Prepare!

After testing some distros during the last four years, I have now two Ubuntu boxes standing next to each other, LAMP servers. One user is identical between those machines, password and all.
 Everything works fine, except for this one thing: I have never (and as you know, that is _really_ non-frequent) managed to mount a filesystem from one of these machines to the other one.  Whatever i try of the black arts of the command line (on thursday nights with full moon  as well) there is always one of two outcomes: "Permission denied" or a page full of helptext, which of course I will be chanting as I in another year or so will be sitting somewhere rocking back and forth.

So i turn to you:

Given that all there is no problems with the installs (I can go for that), can anybody of you give me a command line that should work? 

The last year most of my efforts start with mount -t cifs //server/share /mnt/mntpoint  and so on.

Ah, that was a relief! Did it! Told it! :)

---

### Post by hyperair on 2008-02-04
xD Great presentation of your problem IMO. Try this:
```

sudo mount -t cifs //server/share /mnt/mntpoint -o user=username

```
It should then prompt you for the password of the smb username that corresponds to your username. Then it should mount.

---

### Post by pumahalen on 2008-02-04
Thank you for your answer.
My family and friends have been supporting, too. :)

Indeed your command line should work, believe me, I happened to come by it during the last years. 
To leave out any alternatives I have the same username on both machines (which is irrelevant, though) and  used identical procedures using smbpasswd -a for the same user (also irrelevant) , even using the same password on both machines (a stupid thing to do). Does the user in question have access to the mounting point in question when that mounting point (for test purposes) is chmoded  0777?.  Is that  something to consider in Linux? 

Forgive me for being ironic, it's just my frustration over my own fumbling...

---

### Post by hyperair on 2008-02-04
0777 means everybody is given read,write and execute permissions. And for directories, execute permissions means the permission to chdir into the folder.

---

### Post by pumahalen on 2008-02-05
Forgive me if I am unclear, I know of course what 0777 means, what I wanted to say was that it can not be permissions for the mount point that give the "permission denied"-message. I get this message also when I specify root as username when mounting.

---

### Post by geirha on 2008-02-05
Could you paste the permission denied message you get? I'm not sure what errors cifs give, but it could be both a local and a remote problem. 

You need to be root to mount anything, if not, you'll get a permission denied, so make sure you have "sudo" in front of the command. If you get it mounted by being root, then you know its working, and you should add an entry for it in fstab to allow regular users to mount (without using sudo)

If trying to mount with sudo/root still fails, then the problem is most likely on the other end. How does the smb.conf look on the server?

---

### Post by pumahalen on 2008-02-08
This is a typical situation:

root@client:/# mount -t cifs //server/tmp /mnt/mountpoint
mount: wrong fs type, bad option, bad superblock on //server/tmp,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail :

876.504000]  CIFS VFS: cifs_mount failed w/return code = -22
[  922.224000]  CIFS VFS: cifs_mount failed w/return code = -22

Client : 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

Server:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"

Nothing special in smb.conf, I just add the domain, specify interfaces, set security to user and add tmp as share, root = invalid user, valid users = myname. smbpasswd = linuxpassword and is the same on both machines, because I do not know which machine the password request is meant for.

smbtree shows the shares in question. 


Thank you for your interest.

---

### Post by hyperair on 2008-02-08
You didn't try with "-o user=<username>"?

---

### Post by geirha on 2008-02-08
Try using the fully qualified hostname or the ip-adress of the server, as suggested here: [http://ubuntuforums.org/showthread.php?t=332575](http://ubuntuforums.org/showthread.php?t=332575)

---

### Post by SpaceTeddy on 2008-02-08
i don't know if you want to hear this... but as for me, i would not use cifs to go from one linux server to another. i personally prefer sshfs in that case.

as long as you can login via ssh, sshfs works (for me anyway)... as for how to use it... 

> sshfs username@server:/path/on/server /local/mount/point

you'll be running around as the username on the server. of course, username as to exist on the other server maschine and it must be able to login via ssh.

don't know if that helps... but i hope it does :)

---

### Post by pumahalen on 2008-02-08
> **hyperair said:**
> You didn't try with "-o user=<username>"?

But I did, it just gave a screenfull of messages and hints, so I decided to go for these first. I have also used the credential file, not bringing me any further. Sorry.

---

### Post by pumahalen on 2008-02-08
> **SpaceTeddy said:**
> i don't know if you want to hear this... but as for me, i would not use cifs to go from one linux server to another. i personally prefer sshfs in that case.

as long as you can login via ssh, sshfs works (for me anyway)... as for how to use it... 



you'll be running around as the username on the server. of course, username as to exist on the other server maschine and it must be able to login via ssh.

don't know if that helps... but i hope it does :)

But I really like to hear this, I have been wondering what role samba and cifs have in a pure Linux setting, but have not investgated the matter. (Loosing motivation, to be true! ) So I will test this, using ssh between the different machines is no prob.

---

### Post by roaldz on 2008-02-08
> **pumahalen said:**
> But I really like to hear this, I have been wondering what role samba and cifs have in a pure Linux setting, but have not investgated the matter. (Loosing motivation, to be true! ) So I will test this, using ssh between the different machines is no prob.

Yeah, or nfs?

---

