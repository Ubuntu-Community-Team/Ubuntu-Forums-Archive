---
title: "permit a general user to access all directories in ubuntu 12.04"
date: 2013-03-02
forum: General Help
---

### Post by uzumakifahim on 2013-03-02
I'm using Ubuntu 12.04 as an administrator and I can access all the directories of my computer. Now I want to create another general user, who can access these directories, use wireless, mobile and wired connection without asking my (administrative) password.

How can I do that? Please help anyone.

Thanks in advance.

---

### Post by schragge on 2013-03-02
```

sudo adduser [COLOR=#0000ff]newuser[/COLOR] sudo

```where [COLOR="#0000FF"]newuser[/COLOR]  is the user whom you want to grant sudo powers.

---

### Post by uzumakifahim on 2013-03-02
@schragge, thanks for your reply. I don't want to give a general user administrative privilege, but only to access these directories, use wireless, mobile and wired connection, sharing files on local network without asking my (administrative) password.

---

### Post by schragge on 2013-03-02
> **uzumakifahim said:**
> without asking my (administrative) password.Wait, it seems like you're misunderstanding what *sudo* does. When you add a user to the *sudo* group, he/she will be asked not yours, but *his/her own* password to gain root privileges. You can fine tune what rights a user gets with sudo by editing the [/etc/sudoers]("http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html") file with the command
```
sudo visudo
``` but you should be extremely cautious when doing this: an error editing this file may easily end in a disaster.

Besides, there are some rights that may be granted to users by adding them to appropriate groups. Look at the output of
```
groups $USER
``` to see what groups you as administrator are member of, and decide which of them the general user should be added to.

E.g. you may want to add your general user to groups *netdev* and *sambashare*:
```
sudo adduser [COLOR=#0000ff]some_user[/COLOR] netdev
sudo adduser [COLOR=blue]some_user[/COLOR] sambashare

```

Or do the same with one command
```
sudo usermod -aG netdev,sambashare [COLOR=#0000ff]some_user[/COLOR]
```

See the  description of what different groups mean at [uwiki]Security/Privileges[/uwiki] in Ubuntu Wiki.

---

### Post by cortman on 2013-03-02
You can even create new usergroups with specific priveleges as well, if you want more than one user to have these capabilities.
If a user is a member of sudoers, it won't ask for *your* password when they use sudo, it'll ask for *their *password.
You do not want to give them complete non-root access to the filesystem. Make them use sudo- if nothing else it serves as a reminder that "Oh. These files are important. Perhaps I'd better not mess them up."

---

### Post by uzumakifahim on 2013-03-02
Oh!!! Really thanks to both of you for this resourceful reply.

---

### Post by uzumakifahim on 2013-03-02
@schragge, thanks for your clear explanations. It removes my misunderstandings. After adding a general user account to sudo group it can access all directories with it's own password, but problem is that it can also install/remove software. I don't want this.

Actually, I'm trying to implement Ubuntu in a small office where general users will use computer for day to day use (office works, browsing etc.). They just need to use local hard drives. They don't need complete sudo privilege. 

Could you please tell me how can I do that?

---

### Post by cwsnyder on 2013-03-02
You can either grant access to all directories including the system directories and installing software for the system, or you can confine them to their own /home/<user>/ set of folders.  If you want to give them limited access to the directories other than their own folders, YOU are going to have to define exactly what privileges they need.  If they are not to have **sudo** privileges on their own machines to mess them up at will, then they must have their privileges limited and are going to be bothering support much of the time to allow for system updates, changing their own passwords, making LAN connections, viewing thumb drives, connecting printers, etc.  There is no set of limited privileges normally defined between keeping them out of their system configuration and full access.

If you want to do a custom set of privileges, that is what group administration is for, define what a group can and can't do, then add the users to the group.  But that will be completely custom, and we can't define it for you.

---

### Post by uzumakifahim on 2013-03-02
@cwsnyder, thanks for the clarification. I find that gnome-system-tools is a good tool for this type of user management. It also allows to create new user groups, but how can I define privileges for a new user group in this tool? I don't get any help about this after web search. Is there any documentation for this?

---

### Post by prodigy_ on 2013-03-02
It's actually possible to grant users  fine-grained access to specific root-owned files/directories. Read up on [Linux ACLs](https://help.ubuntu.com/community/FilePermissionsACLs).

It's also possible to grant access to certain tasks that require root privileges without granting full root access. For example you can specify (in /etc/sudoers) which programs user can run via sudo. Even if user needs interactive root shell for some reason you can [limit what they can do there with AppArmor](http://www.novell.com/support/kb/doc.php?id=3768203).

---

### Post by The Cog on 2013-03-02
uzumakifahim: Can we go back to basics here - why do you want to give this user access to directories outside of his home? They will have read access to pretty-much everything anyway. And I can't think why you would want to give them write access outside of their home. I'm thinking maybe there is some misunderstanding, and that you simply **think** they need this access for something when in fact they don't.

---

### Post by uzumakifahim on 2013-03-02
Actually the users are using Windows 7 now. They are using a general user account and they has read-write permission on the local hard drives. But they can't install or remove software. I am looking for same user privilege with Ubuntu 12.04.

Hope now it's clear to everybody that what I want actually.

Thanks to all.

---

### Post by gordintoronto on 2013-03-02
When you say "access," do you mean you want the person to be able to read/copy files from all folders? In order to edit or add files, the users needs administrative privileges.

---

### Post by uzumakifahim on 2013-03-03
@gordintoronto, I've mentioned in my last post that I want a user will be able to read and write files in local hard drives., but he can't be able to install or remove a software that affects all users. This is possible in Windows 7 (a general user can read and write files on drive, like C, D, E etc., but he can't install or remove any software). 

I want to replace windows 7 with Ubuntu 12.04. That's why I need this in Ubuntu 12.04.

---

### Post by Impavidus on 2013-03-03
You can just make a general data storage directory somewhere on your system, where every user has full read and write access.

---

### Post by uzumakifahim on 2013-03-03
How can I do that with my existing partition?

---

### Post by Impavidus on 2013-03-03
In /media or wherever you like you can make a directory where you can mount your data partitions. Use /etc/fstab to mount them.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you want to give users access to the root partition for data storage (a less elegant solution, but it works), you can just make a directory. For example call this directory /media/bar/. To make it accessable to all the easiest way is probably to create a group for all people who are allowed to use the general storage. Let's call this group foo. See further:
[http://manpages.ubuntu.com/manpages/precise/en/man8/groupadd.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/groupadd.8.html) -- create a group
[http://manpages.ubuntu.com/manpages/precise/en/man5/group.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/group.5.html) -- add users to a group
I'm sure there's also a GUI way.

By default all files are created with read and write permissions for the group to which they belong (because by default your umask is 0002, blocking only write permission for others). This means that you have to make sure all files in /media/bar belong to group foo, which can be arranged with the set group ID bit on the directory.
```

#Create directory
sudo mkdir /media/bar
#Set group of directory
sudo chgrp foo /media/bar
#Set permissions
sudo chmod 2776 /media/bar

```
New files created in this directory or copied to it will have the correct group and permissions. If someone moves an entire directory to this general data directory this may not be the case, but a recursive chgrp and chmod can fix this quickly.

Note that groups are also a useful way of giving certain people write access to particular system directory, so that you can make a user the admin for a data directory of one particular application.

---

### Post by schragge on 2013-03-04
> **uzumakifahim said:**
> Actually the users are using Windows 7 now. They are using a general user account and they has read-write permission on the local hard drives. But they can't install or remove software. I am looking for same user privilege with Ubuntu 12.04.Maybe I'm misunderstanding who general users are. But: I have three user accounts on my Windows 7 machine. Only one of them, who's in the group *Administrators*, can install/remove software. And only this user can write to *C:\*. The other two can't. So, I doubt a general user has full write access to local hard drives even on Windows 7. Sure, you can *grant* them that right for specific folder outside of *C:\Users* by changing *Properties* of that folder. The Linux equivalent of it is to set up group permissions as **Impavidius** suggested.

Perhaps it would be more helpful if you created a test user on your Ubuntu installation, logged in as that user, and tried all the actions you think such user should be able to do, then posted here what hadn't worked.

---

### Post by uzumakifahim on 2013-03-05
@[[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515"), thanks that you understand what exactly I want, but unfortunately your solution is not working yet.

I have created a group named "impavidius", and assign a test user to that group, but after logging in that user is not able to open any local drives without administrator password.

---

### Post by schragge on 2013-03-05
Then we need more info about your configuration. How are your disk partitions laid out? Are all drives mounted on boot? What groups is your test user member of? Please post the output of following commands:
```

lsblk -o name,fstype,mountpoint,owner,group,mode,ro,rm,rota,size,state
blkid -c /dev/null
mount
findmnt -s
groups [COLOR=red]testuser[/COLOR]

```where [COLOR=red]testuser[/COLOR] is the username of your test user.

---

### Post by Impavidus on 2013-03-05
First you have to mount all "drives" (typically partitions xisting on a drive, but windows confusingly calls them drives). You can do so automatically at boot using /etc/fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
They will all be mounted on a mount point. You have to make the mount point owned by the group and set the permissions as indicated a few posts back.

The root partition has a somewhat special mount point to which you can better not give everyone full access, as they will be able to modify software (and destroy your system). If you want to give users access to that partition you can make a directory somewhere in the file system on that partition and set the owner and permissions on that directory.

Oh, and there's no need to name the group after a misspelling of my user name. It's an honour too great for me.

---

### Post by uzumakifahim on 2013-03-06
Here is the O/P of your commands.
```
lsblk -o name,fstype,mountpoint,owner,group,mode,ro,rm,rota,size,state

NAME    FSTYPE MOUNTPOINT        OWNER GROUP  MODE       RO RM ROTA   SIZE STATE
sr0                              root  cdrom  brw-rw----  0  1    1  1024M running
sda                              root  disk   brw-rw----  0  0    1 149.1G running
&#9500;&#9472;sda1                           root  disk   brw-rw----  0  0    1  23.3G 
&#9500;&#9472;sda2                           root  disk   brw-rw----  0  0    1     1K 
&#9500;&#9472;sda5         /media/ALL NEEDS_ root  disk   brw-rw----  0  0    1  18.6G 
&#9500;&#9472;sda6         /media/OTHERS     root  disk   brw-rw----  0  0    1    28G 
&#9500;&#9472;sda7         /media/DFDD-A2C5  root  disk   brw-rw----  0  0    1    28G 
&#9500;&#9472;sda8         /media/TUTORIALS  root  disk   brw-rw----  0  0    1  31.7G 
&#9500;&#9472;sda9         [SWAP]            root  disk   brw-rw----  0  0    1   1.9G 
&#9492;&#9472;sda10        /                 root  disk   brw-rw----  0  0    1  17.7G 
zram0          [SWAP]            root  disk   brw-rw----  0  0    0 989.6M 
fd0                              root  floppy brw-rw----  0  1    1     4K
 
=========================================================================================

groups test

test dip plugdev fuse lpadmin netdev impavidius
```

Hope this can make understand the condition.

---

### Post by schragge on 2013-03-07
Sorry, I didn't realized you should *sudo* to see filesystem type and UUID. Could you please repeat:
```

sudo blkid -c /dev/null

```

Also, please post the output of the commands
```

mount
findmnt -s

```

---

### Post by uzumakifahim on 2013-03-08
@schragge, Here is the output.

```
sudo blkid -c /dev/null

/dev/sda1: UUID="52B415BBB415A311" TYPE="ntfs" 
/dev/sda5: LABEL="ALL NEEDS" UUID="A7B3-0C93" TYPE="vfat" 
/dev/sda6: LABEL="OTHERS" UUID="64E9-0539" TYPE="vfat" 
/dev/sda7: UUID="DFDD-A2C5" TYPE="vfat" 
/dev/sda8: LABEL="TUTORIALS" UUID="B85E-1929" TYPE="vfat" 
/dev/sda9: UUID="1c986bc2-7382-4df9-bf9a-b71c62a8421e" TYPE="swap" 
/dev/sda10: UUID="a7dcadb6-3391-4bcc-a317-5fea6c7e4ae7" TYPE="ext4" 
/dev/zram0: UUID="70a896bb-b40b-4fe8-a992-bcccc33fb247" TYPE="swap" 

```

```
mount

/dev/sda10 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fahim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fahim)
/dev/sda8 on /media/TUTORIALS type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda7 on /media/DFDD-A2C5 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda6 on /media/OTHERS type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda5 on /media/ALL NEEDS_ type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```

```
findmnt -s

TARGET         SOURCE                                    FSTYPE OPTIONS
/proc          proc                                      proc   nodev,noexec,nosuid
/              UUID=a7dcadb6-3391-4bcc-a317-5fea6c7e4ae7 ext4   errors=remount-ro
none           UUID=1c986bc2-7382-4df9-bf9a-b71c62a8421e swap   sw
/media/floppy0 /dev/fd0                                  auto   rw,user,noauto,exec,utf8


```

---

### Post by schragge on 2013-03-08
Currently, the four FAT drives (TUTORIALS, DFDD-A2C5, OTHERS, ALL NEEDS_) are mounted by user *fahim* from the file manager by clicking on their labels/icons. Therefore, they are exclusively owned by this user and other users cannot access them. If you reboot, log in as user *test*, and mount them again by clicking on them, then they will be exclusively owned by *test* and not accessible to *fahim*. First come, first served. Till the next reboot. If this suites you, fine. If not, read further.

I suppose these drives are not removable thus I suggest that you permanently mount them on boot. See [uhelp]community/MountingWindowsPartitions[/uhelp].

---

