---
title: "Unmounting CIFS mounts"
date: 2013-09-20
forum: General Help
---

### Post by phelgan on 2013-09-20
Hi all,

I have been delving through the delights of mounting a NAS so that individual users can mount it as required for backup without needing sudo. Using mount.cifs, I have managed to do this.

I now face the problem that the user cannot unmount the NAS when finished, without recourse to sudo.

The message received is 
```
phil@pc-3:/bin$ umount /media/nas_backup
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad
umount: /media/nas_backup is not in the fstab (and you are not root)


```

From searching the web, there seems to have been a umount.cifs command, but this is not longer present?

Can anyone give me any pointers?

Thanks

Phelgan

---

### Post by nerdtron on 2013-09-21
Though you already figured out how to mount the samba share, why do you want them to unmount it manually? The share will be unmounted when their computer reboots/shutdowns.

---

### Post by phelgan on 2013-09-21
Hi nerdtron

Partly curiousity - I assume it should be possible - and partly I'd be more comfortable with the mount disabled when not required. As noted it is for backup, and all users are new to Linux to varying degrees, so safety!

Cheers,

Phelgan

---

### Post by bab1 on 2013-09-21
> **phelgan said:**
> Hi nerdtron

Partly curiousity - I assume it should be possible - and partly I'd be more comfortable with the mount disabled when not required. As noted it is for backup, and all users are new to Linux to varying degrees, so safety!

Cheers,

Phil

So how did you mount them?  In order to mount or unmount any partition you need to be root or it needs to be explicitly allowed via the fstab file.  Post the output of ```
cat /etc/fstab
```

Did you resolve this problem```
phil@pc-3:/bin$ umount /media/nas_backup
[mntent]: [COLOR="#FF0000"]line 16 in /etc/fstab is bad[/COLOR]
[mntent]: [COLOR="#FF0000"]line 17 in /etc/fstab is bad[/COLOR]
umount: /**media/nas_backup is not in the fstab** (and you are not root)
```

---

### Post by phelgan on 2013-09-22
Hi bab1

The device I'm mounting is a Seagate GoFlex Home (NAS). There are two lines related to it in the fstab, as shown below.

The relevant lines in fstab are :
```
//192.168.1.65/GoFlex\040Home\040Public    /media/nas_public    cifs    iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto    0    0&#65279;
//192.168.1.65/GoFlex\040Home\040Backup /media/nas_backup    cifs    iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto    0    0&#65279;

```

My backup script is mounting the second item (/media/nas_backup) using the line
```
mount.cifs '//192.168.1.65/GoFlex Home Backup' /media/nas_backup -o user=phil,forceuid,uid=1000
```
Curiously using 
```
mount -t cifs....
```
does not work without Sudo.

The errors thrown up when trying to unmount the drive do not occur if the command is run using sudo. The lines referred to are the twoI've listed above.

Cheers,

Phelgan

---

### Post by bab1 on 2013-09-23
> **phelgan said:**
> Hi bab1

The device I'm mounting is a Seagate GoFlex Home (NAS). There are two lines related to it in the fstab, as shown below.

The relevant lines in fstab are :
```
//192.168.1.65/GoFlex\040Home\040Public    /media/nas_public    cifs    iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto    0    0&#65279;
//192.168.1.65/GoFlex\040Home\040Backup /media/nas_backup    cifs    iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto    0    0&#65279;

```

My backup script is mounting the second item (/media/nas_backup) using the line
```
mount.cifs '//192.168.1.65/GoFlex Home Backup' /media/nas_backup -o user=phil,forceuid,uid=1000
```
Curiously using 
```
mount -t cifs....
```
does not work without Sudo.

The errors thrown up when trying to unmount the drive do not occur if the command is run using sudo. The lines referred to are the twoI've listed above.

Cheers,

Phelgan

I believe that having the term *user *in the fstab is all that is needed.  You don't need to repeat it again in a script.  I've never used the *mount.cifs *command directly either. 

When I add a line in fstab allowing a non-root user (a mortal user)  to mount a partition I use something like the following.  First the fstab entry```

# Manual mount of Samba Share (share_name) to /media/<mount_point> [COLOR="#FF0000"]**Note: The share name is the same name as the mount point (ie: backup)**[/COLOR]
//ip-addr/share_name /media/mount_point cifs user,noauto,username=<user>,credentials=/home/<user>/.smbcred,uid=<some_uid>,gid=<some_gid>,nobrl 0 0
```...note the terms such as these <some_term> are for you to fill in the specifics of your system.  Look closely.  There is both a user and username parameter in the fstab line.  The term *username* is the user that is connecting.  The term *user* allows a non-root user to mount the partition. 

With the above fstab entry you can use this simple command in your script```

mount /media/<mount_point>  [COLOR="#FF0000"]**# See the note in red above**[/COLOR]

```

I use this very simple command in a wrapper script..  The uid on the mount point is root.  The gid is a common group to all the users (e.g. a group named *users* or *sambashare*).  I manage the files and directories via the gid.  I don't care what the uid is.  On my users machines a wrapper script located at ~/<user>/bin mounts or dismounts or tells you that the share is unavailable.  I used a .desktop file to trigger the script.  When the the user clicks on the icon the share is mounted.  If the user clicks again the script will dismount the share (with appropriate warnings of course).  If the share is unavailable from the server or the network is down, the script generates a notice of that situation also.

---

### Post by phelgan on 2013-09-24
> **bab1 said:**
> I believe that having the term user in the fstab is all that is needed. You don't need to repeat it again in a script. I've never used the mount.cifs command directly either. 
There are specific users setup for access to the GoFlex Home, the user=phil specifiying the mounting in this particularly case (I believe can also be username=phil).

> When I add a line in fstab allowing a non-root user (a mortal user) to mount a partition I use something like the following. First the fstab entry```

# Manual mount of Samba Share (share_name) to /media/<mount_point> Note: The share name is the same name as the mount point (ie: backup)
//ip-addr/share_name /media/mount_point cifs user,noauto,username=<user>,credentials=/home/<user>/.smbcred,uid=<some_uid>,gid=<some_gid>,nobrl 0 0
```...note the terms such as these <some_term> are for you to fill in the specifics of your system. Look closely. There is both a user and username parameter in the fstab line. The term username is the user that is connecting. The term user allows a non-root user to mount the partition. 

I've done something very similar to this, prior to moving onto the mount.cifs command. Despite this line being present in fstab

```
//192.168.1.65/GoFlex\040Home\040Backup /media/nas_backup    cifs iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto,username=<user>,password=<password>    0    0&#65279;
&#65279;
```

If I now use "mount /media/nas_backup" I get 
```
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad
mount: can't find /media/nas_backup in /etc/fstab or /etc/mtab
```
The same response is given if the command is run wiht sudo.

(Note that neither line 16 or 18 are relevant to the line concerned.)

Being more specific...
```
mount -t cifs /media/nas_backup
mount: only root can that
```

Using the same command prefixed with sudo gives me a list of options and parameters for the command but no mounting!

In an effort to ensure the user has rights to the mount point, I have changed the mount point from /media/nas_backup to /home/<user>/nas_backup, but this does not seem to be relevant.

Regards,

Phelgan

---

### Post by bab1 on 2013-09-24
> **phelgan said:**
> There are specific users setup for access to the GoFlex Home, the user=phil specifiying the mounting in this particularly case (I believe can also be username=phil).  

***user=*** is not the same as **user**.  When it is *user=* it is a cifs mount option.  When it is *user* (bare) it is a mount option.  I've run into this before.  So I always use username= for the ownership.  You can be the owner of the files and directories and still not have the right to mount the share. > 
I've done something very similar to this, prior to moving onto the mount.cifs command. Despite this line being present in fstab

```
//192.168.1.65/GoFlex\040Home\040Backup /media/nas_backup    cifs iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev,user,noauto,username=<user>,password=<password>    0    0&#65279;
&#65279;
```

If I now use "mount /media/nas_backup" I get 
```
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad
mount: can't find /media/nas_backup in /etc/fstab or /etc/mtab
```
The same response is given if the command is run wiht sudo.

(Note that neither line 16 or 18 are relevant to the line concerned.)
IDK whether it is or is not.  I've never seen the entire fstab file.> 

Being more specific...
```
mount -t cifs /media/nas_backup
mount: only root can that
```
You don't need to declare the file system type in the script.  It's already described in the fstab file.  You just need * mount /nedia/nas_backup*> 

Using the same command prefixed with sudo gives me a list of options and parameters for the command but no mounting!

Once again, IDK what the errors are. I haven't seen them.  The example I showed you has been working for me for many years.  Currently It is being used with Ubuntu 12.04 Samba clients against a Ubuntu 12.04 Samba server (both being v3.6.3).  It is also available to Windows Vista and Windows 7 clients.
> 

In an effort to ensure the user has rights to the mount point, I have changed the mount point from /media/nas_backup to /home/<user>/nas_backup, but this does not seem to be relevant.


Correct.  Where you mount it is not relevant.  The mount point can be owned by root as long as others has r-x rights.  This is the default settings.

---

### Post by phelgan on 2013-09-29
Hi Bab1,

Thanks for your help, with some tweaking it worked.

One thing I found I had to change was the uid=0. With this in place a user (except me) could not mount ("permission denied"). By specifying the user, not just the group, this was resolved. I also had to use the filemode and dirmode options. The final relevant lines were:

```
//192.168.1.65/GoFlex\040Home\040Backup /home/<user1>/nas_backup cifs user,noauto,username=<user1>,credentials=/home/<user1>/nasbac<user1>,uid=0,gid=1004,file_mode=0777,dir_mode=0777,_netdev,nobrl 0 0
//192.168.1.65/GoFlex\040Home\040Backup /home/<user2>/nas_backup cifs user,noauto,username=<user2>,credentials=/home/<user2>/nasbac<user2>,uid=1003,gid=1004,file_mode=0777,dir_mode=0777,_netdev,nobrl 0 0
//192.168.1.65/GoFlex\040Home\040Backup /home/<user3>/nas_backup cifs user,noauto,username=<user3>,credentials=/home/<user3>/nasbac<user3>,uid=1002,gid=1004,file_mode=0777,dir_mode=0777,_netdev,nobrl 0 0
//192.168.1.65/GoFlex\040Home\040Backup /home/<user4>/nas_backup cifs user,noauto,username=<user4>,credentials=/home/<user4>/nasbac<user4>,uid=1001,gid=1004,file_mode=0777,dir_mode=0777,_netdev,nobrl 0 0
```

Thanks again!

Phelgan

---

