---
title: "2nd HDD Permissions"
date: 2019-08-11
forum: General Help
---

### Post by brenneke on 2019-08-11
Please help step me through changing permissions for 2nd HDD to allow all users to read/write - have read through many posts but most goes over my head.

/dev/sdb1: LABEL="HDD2" UUID="dcfb3e52-e7c8-4569-921b-7ed6e47bea4b" TYPE="ext4" PARTUUID="a28f670c-f56a-453e-ad79-cd79d8db552e"

/dev/sdb1 on /HDD2 type ext4 (rw,relatime,data=ordered)

---

### Post by TheFu on 2019-08-11
Where is it mounted?
How is it mounted?
What are the current permissions? 
Which users do you want to have access?
What type of access to you want them to have?

Do you understand normal Unix permissions for files and directories?

There is no secure method to allow every user to have read-write access to an entire directory structure. 

You can easily allow 1 user full read-write and control over permissions. Just make that userid the owner.

If there are a few specific userids you want to provide read-write access, then place all those userids into a single group and make the groupid for the directory the group they all share and set the setgid permissions bit on the directory and set the group on the directory to have read-write permissions.  Any new files copied in or created under that specific directory by anyone with group membership will inherit the permissions and read-write.

But really, start by answer the first questions.  Please show proof using commands, not an interpretation what you think. We need facts.

For example, 
I mount a second storage area using the fstab. The important line looks like this:
```
/dev/mapper/ubuntu--mate--vg-stuff  **/stuff**  ext4 noatime,errors=remount-ro,noatime 0 2
```
When it is mounted it looks like this:
```
$ cd /stuff/
/stuff$ df .
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--mate--vg-stuff   99G  1.5G   92G   2% /stuff
```
Inside the directory, the files/directories are this:
```
/stuff$ ls -al
total 32
drwxr-xr-x  5 root root  4096 Mar 19 16:27 ./
drwxr-xr-x 31 root root  4096 Jul 27 09:02 ../
drwxr-xr-x  5 root root  4096 Aug 10 19:12 extra_stuff/
drwx--x--x  2 root root  4096 Mar 19 16:41 images/
drwx------  2 root root 16384 Feb 28 16:55 lost+found/

```
Which don't allow any non-root users to create files. See how root is the owner of everything?
```
/stuff/extra_stuff$ ls -al
total 88
drwxr-xr-x  5 root root  4096 Aug 10 19:12 ./
drwxr-xr-x  5 root root  4096 Mar 19 16:27 ../
drwxr-xr-x 29 tf   tf   16384 Jun 12 15:42 ale-mail-arch/
drwxr-xr-x  2 tf   tf   57344 Mar 12 21:49 tmp-photos/
drwxrw**s**r-x  2 tf   adm   4096 Jul  2 15:52 videos-tmp/

```
Inside the "extra_stuff" directory, notice the videos-tmp/ directory. The owner is tf, the group is adm and the permissions are rwxrwxr-x plus the setgroupid permissions bit is enabled, which makes it so any member of the "adm" group can create files and edit files inside the videos-tmp/ directory.

This method only works with Linux file systems, not NTFS, not exFAT, not FAT32.

---

### Post by brenneke on 2019-08-11
> **TheFu said:**
> Where is it mounted?
How is it mounted?
What are the current permissions? 
Which users do you want to have access?
What type of access to you want them to have?

Do you understand normal Unix permissions for files and directories?


/HDD2
Not sure
Not sure
Resilio Sync
Any / all permissions Resilio Sync would need to sync folders on this drive - presumably read, write, create & delete files....?
No unfortunately

I can provide the output for any commands you request.

Thanks for helping.

---

### Post by TheFu on 2019-08-11
Sorry, some of those answers don't help me at all.  Please use the commands like I've shown to provide the data. You'll need to change them for the specifics of your system locations.  I showed the minimal information.

---

### Post by brenneke on 2019-08-11
> **TheFu said:**
> Sorry, some of those answers don't help me at all. 
Sorry man, they were your questions not mine.


> **TheFu said:**
> I showed the minimal information.
Yes you did.


Just to remind you - we all have our special areas of expertise - you are incredibly talented in this realm I am sure - when you need advice in areas outside of your specialty I am sure you are grateful to those who are patient to teach and explain. This is a forum where those who don't know, ask.

---

### Post by oldfred on 2019-08-12
Never heard of Resilio-Sync
[https://www.capterra.com/p/173194/Resilio-Sync/](https://www.capterra.com/p/173194/Resilio-Sync/)
It seems to be a paid backup solution. Most with Linux use built in Linux tools for backup.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

---

### Post by brenneke on 2019-08-12
> **oldfred said:**
> Never heard of Resilio-Sync
[https://www.capterra.com/p/173194/Resilio-Sync/](https://www.capterra.com/p/173194/Resilio-Sync/)
It seems to be a paid backup solution. Most with Linux use built in Linux tools for backup.


2-way sync, multi platform, back-up only also if you wish.
[https://www.resilio.com/individuals-sync/](https://www.resilio.com/individuals-sync/)
[https://www.linuxbabe.com/ubuntu/install-resilio-sync-ubuntu-16-04-16-10](https://www.linuxbabe.com/ubuntu/install-resilio-sync-ubuntu-16-04-16-10)

What is UEFI?

---

### Post by yancek on 2019-08-12
In post # 3 above, you indicate that your hard drive is mounted at /HDD2 which would mean you or some other user of your computer manually created the mount point.   If that's the case, obtaining user:group and permissions would be as simple as using the command:

```
ls -l /HDD2
```

The how is it mounted questions would be either configured to have the system mount or you as the user manually mount it using the mount command.  Often, external drives are available under the /media or /media/username directory and can be mounted by simply clicking on the entry in the file manager.  Have you created an entry in the /etc/fstab directory to mount the external drive partition(s) at the location you specified in your post, /HDD2?

The links below give detailed explanation of user:group permissions on Linux.  The last link below gives detailed info on UEFI. 

[https://www.linux.com/learn/understanding-linux-file-permissions](https://www.linux.com/learn/understanding-linux-file-permissions)

[URL="https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions"]https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions


[https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)



[/URL]

---

### Post by TheFu on 2019-08-12
> **brenneke said:**
> Sorry man, they were your questions not mine.

The questions were asked in an attempt to help you get to a good solution. No other reason.

> **brenneke said:**
> 
Yes you did.

The minimal way to get the required information is what I showed using a real example that I hoped you could follow.  It would save time for you and us to have that data.  If you don't understand something, please tell us.  Nobody knows all this stuff. I had to check that the commands already posted would actually provide the needed data and not leave anything out. I did that hoping not to waste any of your time, so a solution would be quicker.

There is no way for someone here to know your level of expertise.  We are chastised for under estimating someone's knowledge. We are chastised for over estimating someone's knowledge.  We really just want to help you get a working solution, perhaps even the best possible solution.

I showed commands in a logical order for what will be necessary to the solution.

How the storage is mounted matters, so I asked.  If it isn't mounted in the needed way, then we need to fix that.

Which file system it uses matters.  If the wrong file system is used, we can't fix it without drastic, usually painful, changes. The wrong file systems don't support Unix permissions.

Defining the required permissions based on some software is only slightly helpful.  In general, backup tools need to be run as root or the software cannot access and store the data. This is pretty standard across all Unix-like computers.  Knowing that it is for backups means we probably really don't care about all the permissions, provided it is a Unix file system, since root will have access if it is mounted read-write, not read-only.

With exact examples, you can look up each command and the options to learn what is being requested.  That is faster for you and it doesn't waste the time of others. 

Can you please try to run the commands I've shown, modified for your specific system, with the top directory changed to what makes sense on your computer, we could get the solution you seek.  Basically, that means to use /HDD2 in the commands where I've used /stuff.  If you don't understand and google doesn't answer sufficiently, please as a specific question that can be answered.  Can't tell if you aren't answering because you don't want to or for some other reason. Please help us to help you.

---

### Post by brenneke on 2019-08-12
> **yancek said:**
> In post # 3 above, you indicate that your hard drive is mounted at /HDD2 which would mean you or some other user of your computer manually created the mount point.   If that's the case, obtaining user:group and permissions would be as simple as using the command:

```
ls -l /HDD2
```




```
gw@GW:~$ ls -l /HDD2
total 16
drwxrwxrwx+ 5 gw gw 4096 Feb 14 11:39 Backups
drwxrwxrwx+ 6 gw gw 4096 Oct  1  2018 Documents
drwxrwxrwx+ 5 gw gw 4096 Oct  2  2018 Phones
drwxrwxrwx+ 6 gw gw 4096 Mar 17  2017 Plex
gw@GW:~$
```

From: [https://blog.benjie.me/installing-resilio-sync-and-running-it-as-a-regular-user/](https://blog.benjie.me/installing-resilio-sync-and-running-it-as-a-regular-user/)

"By default, Resilio runs as rslsync user. This can cause annoying permisison errors some times."

Would I be right is saying that I need to give User rslsync same permissions as gw to HDD2?

---

### Post by brenneke on 2019-08-12
> **TheFu said:**
> Can you please try to run the commands I've shown, modified for your specific system, with the top directory changed to what makes sense on your computer, we could get the solution you seek.  Basically, that means to use /HDD2 in the commands where I've used /stuff.  If you don't understand and google doesn't answer sufficiently, please as a specific question that can be answered.  Can't tell if you aren't answering because you don't want to or for some other reason. Please help us to help you.

Yes I did that but unfortunately did not get any meaningful results:

```
gw@GW:~$ /dev/mapper/ubuntu--mate--vg-HDD2  /HDD2  ext4 noatime,errors=remount-ro,noatime 0 2
bash: /dev/mapper/ubuntu--mate--vg-HDD2: No such file or directory
gw@GW:~$ 
```

```
gw@GW:~$ /HDD2$ ls -al
bash: /HDD2$: No such file or directory
gw@GW:~$ 
```

```
gw@GW:~$ /HDD2/extra_HDD2$ ls -al
bash: /HDD2/extra_HDD2$: No such file or directory
gw@GW:~$ 
```

Maybe I did it wrong?

---

### Post by brenneke on 2019-08-12
Not sure if this helps at all:

```
gw@GW:~$ ps aux | grep rslsync
rslsync   2046  0.4  0.6 1066364 25064 ?       Ssl  Aug11   3:44 /usr/bin/rslsync --config /etc/resilio-sync/config.json
gw@GW:~$
```

```
gw@GW:~$ sudo systemctl cat resilio-sync.service
[sudo] password for gw: 
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

lines 1-23...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
lines 1-24...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStartPre=/bin/chown -R ${SYNC_USER}:${SYNC_GROUP} ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
lines 1-25...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStartPre=/bin/chown -R ${SYNC_USER}:${SYNC_GROUP} ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStart=/usr/bin/rslsync --config ${SYNC_CONF_DIR}/config.json
lines 1-26...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStartPre=/bin/chown -R ${SYNC_USER}:${SYNC_GROUP} ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStart=/usr/bin/rslsync --config ${SYNC_CONF_DIR}/config.json
ExecStartPost=/bin/sleep 1
lines 1-27...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStartPre=/bin/chown -R ${SYNC_USER}:${SYNC_GROUP} ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStart=/usr/bin/rslsync --config ${SYNC_CONF_DIR}/config.json
ExecStartPost=/bin/sleep 1

[Install]
lines 1-29...skipping...
# /lib/systemd/system/resilio-sync.service
[Unit]
Description=Resilio Sync service
Documentation=https://help.resilio.com
After=network.target network-online.target

[Service]
Type=forking
UMask=0002
Restart=on-failure
PermissionsStartOnly=true

User=rslsync
Group=rslsync
Environment="SYNC_USER=rslsync"
Environment="SYNC_GROUP=rslsync"

Environment="SYNC_RUN_DIR=/var/run/resilio-sync"
Environment="SYNC_LIB_DIR=/var/lib/resilio-sync"
Environment="SYNC_CONF_DIR=/etc/resilio-sync"

PIDFile=/var/run/resilio-sync/sync.pid

ExecStartPre=/bin/mkdir -p ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStartPre=/bin/chown -R ${SYNC_USER}:${SYNC_GROUP} ${SYNC_RUN_DIR} ${SYNC_LIB_DIR}
ExecStart=/usr/bin/rslsync --config ${SYNC_CONF_DIR}/config.json
ExecStartPost=/bin/sleep 1

[Install]
WantedBy=multi-user.target
~
~
gw@GW:~$
```

---

### Post by oldfred on 2019-08-12
First comand was this, assuming you have mounted it at /HDD2 which now seems incorrect:
$ cd /stuff/
Where in your case /stuff/ is really /HDD2/
or 
cd /hdd2/

But it looks like you do not have it mounted anyway. the line above was from fstab to show the mount, so we know you have it mounted or where you have it mounted. And if not even mounted that is first issue.
Post this:
cat /etc/fstab

Please review these:
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Many are older and ext4 is now used, not ext3 for example
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by brenneke on 2019-08-12
> **oldfred said:**
> First comand was this, assuming you have mounted it at /HDD2 which now seems incorrect:
$ cd /stuff/
Where in your case /stuff/ is really /HDD2/
or 
cd /hdd2/

Post this:
cat /etc/fstab

```
gw@GW:~$ cd /hdd2/
bash: cd: /hdd2/: No such file or directory
gw@GW:~$ 
```


```
gw@GW:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=c49326a9-91c4-4a62-9f1a-5267c6f0a399 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=83a39169-ba85-495b-ad8c-2c0ee3425760 none            swap    sw              0       0
UUID=dcfb3e52-e7c8-4569-921b-7ed6e47bea4b   /HDD2    ext4    defaults    0    2
gw@GW:~$ 
```

---

### Post by oldfred on 2019-08-12
In Linux case matters.
this was wrong:
cd /hdd2/
this is where you have it mounted
cd /HDD2/

---

### Post by brenneke on 2019-08-12
> **oldfred said:**
> In Linux case matters.
this was wrong:
cd /hdd2/
this is where you have it mounted
cd /HDD2/

OK, thanks. Any suggestions on how I can give User rslsync permissions to this drive? Am I using the right terminology?

---

### Post by TheFu on 2019-08-12
So, it appear the fstab is used to mount ext4 storage onto /HDD2.
That is all excellent.  It means that full Unix permissions are available and that access to the storage should be very fast.

Looking at the** ls -l /HDD2** output, there are 2 important things that I see.
[LIST=1]
[*]Normal Unix permissions are already wide open. There is no way to open them wider. Seriously, it is a security rick, IMHO.  It is effectively 777 permissions, which I think should always be avoided.  I'm not a big fan of always, but in this situation I am.
[*]ACLs are being used with the directories.  That means we aren't actually seeing all the permissions.  To see them all, the **getfacl** command must be used.  My ACL-fu is weak.  In 25+ yrs as a Unix admin, I've needed ACLs less than 5 times.  If you were to remove the ACLs (and I don't know how to do that), then any tool you have should work to write/read in those directories.
[/LIST]

 I hope you can find the solution you seek.   Since I know nothing about *Resilio Sync*, I'll bow out now.

---

### Post by brenneke on 2019-08-12
> **TheFu said:**
> So, it appear the fstab is used to mount ext4 storage onto /HDD2.
That is all excellent.  It means that full Unix permissions are available and that access to the storage should be very fast.

Looking at the** ls -l /HDD2** output, there are 2 important things that I see.
[LIST=1]
[*]Normal Unix permissions are already wide open. There is no way to open them wider. Seriously, it is a security rick, IMHO.  It is effectively 777 permissions, which I think should always be avoided.  I'm not a big fan of always, but in this situation I am. 
[*]ACLs are being used with the directories.  That means we aren't actually seeing all the permissions.  To see them all, the **getfacl** command must be used.  My ACL-fu is weak.  In 25+ yrs as a Unix admin, I've needed ACLs less than 5 times.  If you were to remove the ACLs (and I don't know how to do that), then any tool you have should work to write/read in those directories. 
[/LIST]

 I hope you can find the solution you seek.   Since I know nothing about *Resilio Sync*, I'll bow out now.

Thank you, much appreciated. 

Are you saying that all users should already have wide open access to this drive?

---

### Post by TheFu on 2019-08-13
> **brenneke said:**
> Thank you, much appreciated. 

Are you saying that all users should already have wide open access to this drive?

The permissions for /HDD2 haven't been shown, so we really don't know about it, but all the directories inside it are open for the world to delete everything.

ACLs can override any Unix permissions. We have not seen the ACLs. If you didn't use **setfacl**, I don't know how the ACLs were added.  I've never seen any program add ACLs.  Something smells funny to me.

Also, "drive" is the wrong term.  "Partition" is correct.  In some situations, mixing those 2 up will cause total data loss.

---

### Post by brenneke on 2019-08-13
> **TheFu said:**
> ACLs can override any Unix permissions. We have not seen the ACLs. If you didn't use **setfacl**, I don't know how the ACLs were added.  I've never seen any program add ACLs.  Something smells funny to me.

Not smelly, would have been added by me following installation instructions from here: (link posted earlier in this thread)
[https://www.linuxbabe.com/ubuntu/install-resilio-sync-ubuntu-16-04-16-10](https://www.linuxbabe.com/ubuntu/install-resilio-sync-ubuntu-16-04-16-10)

> Also, "drive" is the wrong term.  "Partition" is correct.  In some situations, mixing those 2 up will cause total data loss.
Not saying you are wrong but this is a separate drive from the OS drive.

---

### Post by brenneke on 2019-08-13
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAn8AAAEiCAIAAAAH1CMYAAAAA3NCSVQICAjb4U/gAAAgAElEQVR4Xu3dCZQU9YHH8RoYhmu47/uG4b6FETwQVCRqwg0SgzEas5rdmEWNGJ9Gk5dj3X1vNU8xkSiGVWMwJhsOQVEEMRyuIAMSDuW 5BhgZriv/Q1lOm0f1dXd1f p7v7O4/F6qv/1Pz7/on/9r6puctq1a2fxgwACCCCAAAIGBSoZbIumEEAAAQQQQKBcgPTlOEAAAQQQQMC0AOlrWpz2EEAAAQQQIH05BhBAAAEEEDAtQPqaFqc9BBBAAAEESF OAQQQQAABBEwLkL6mxWkPAQQQQAAB0pdjAAEEEEAAAdMCuaYbpD0EMlSgdu3alStXrlmzpj2 kpKSM5d/MnS4DAsBBJISIH2T4mNnBBo1alS/fn07esM1Tp48qRjev38/MRyOwxYEslkgh2 azObpZ zJCChxW7Zsqb9ViVK2uLhYQRuosGrVqnpKwawFsTbu2bPnwIED58 fT6ZF9kUAgYwRIH0zZioZiFGBtm3bNm3aVE0eOnRIyeqwtNXiWCGtMFaZLVu2nDhxwmhHaQwBBHwpULlevXq 7BidQsCnArm5uQUFBQ0aNNB6d8OGDUrfCxcuOPRVxbTqVRnt0rBhw3PnzmmLQ3meQgCBbBAgfbNhlhmjlwKKXp1SVuh 9tlnilKXVZeVlem8tNJXGXz06FH3O7qsn2IIIJBeApx5Tq/5orcVLKBzyPpR9H7  ecJdEV3RHfr1k07FhUVOZysDtSsmG/WrFnILV1KceW3 sBV5ASmgF0Q8IkAa1 fTATdSAMBpWCHDh103njTpk2JdVdL3tOnT tKsE5fK0GdK1HudurUKS8vT3F75MgR/a0fZbYiXAvoY8eOuclv5yZ4FgEEKkqATxxVlDztpp AVr3q9I4dO5Lpun1rtAJYi9fge6RD6lTSt2nTRkm/cePG8DWu7uFKpg/siwACFS7Ad11V BTQgfQQ0IpTiWgvQJPs8c6dO1WDlrYO9Sie9ezmzZvDo1fby7/Fg /xcODjKQR8L0D6 n6K6KA/BOw41N3LSXZHoavg1KLW eMG9uqWiE1Sm90R8K0A6evbqaFjvhNQFuq8cTLdss8n68Yr 5yzvosjmdrYFwEE0leA677pO3f03KiALvcmecVX3VXo6nKvltH20rZGjRrR4txe9SqeoxUIDN7 vi2dzQ75Hg/d2NW5c2fVY9 ebTeq1lVeZ9HVtD6CrP7oWzBDLj rbyoT JauaMWM6tMYAhknwD3PGTelDCg1Asok52/VcNmsbnVWVfn5 SrvcBVZbSkv69atq3uedae0w eDVZvOZl 6dEl3QQf3QfdFa7uaC6yz9Wvz5s1Vs0pqo 6 VsQ2adIk PPHCuYePXqoe7rL2t5Xxez3CiEh7XK8FEMAgYgCrH0jsrARga8IKH769u2b8Md8QzQDi1GdiI4GrajT3c76gJO z9L Ssvy 6zOnLFXz8HXg9Urfe2lriKHLM3tu7r0bKAJfeO0vuoyeDGtZ3v27Kn6Ax9f1o3WKrZ /Xq ETPa1LAdAU8ESF9PGKkkwwXsVa9941Vi37MRAqRKlKPOXzmpAmvXrrXvtdaJYr0DUFrrR6eFdfNXcNYqRJWgwaepVVi7aPEanNPqQ8gd1HbE2ktbPWs3odqI3gw/oBmeDwRIXx9MAl3wvUAgtBTAisOIn8GNdxDBq1KHfRWEwVmo9LX/gwd1Sf 7g72jrt0qfbX8Daxr7fu5Yl4zDmnXjmHn9wQOXeUpBBBwL Drb5ps3LhJ1arV3A GkggggAACGS9w6tSpw4cPpvswff2Jo7w8vtAn3Q8w o8AAgh4LFCtWiasynydvjk5OR5PGtUhgAACCKS5QGZEg6/TN82PELqPAAIIIIBAZAHSN7ILWxFAAAEEEEidAOmbOltqRgABBBBAILIA6RvZha0IIIAAAgikToD0TZ0tNSOAAAIIIBBZgPSN7MJWBBBAAAEEUidA qbOlpoRQAABBBCILED6RnZhKwIIIIAAAqkTIH1TZ0vNCCCAAAIIRBYgfSO7sBUBBBBAAIHUCZC qbOlZgQQQAABBCILkL6RXdiKAAIIIIBA6gRI39TZUjMCCCCAAAKRBUjfyC5sRQABBBBAIHUCpG/qbKkZAQQQQACByAKkb2QXtiKAAAIIIJA6AdI3dbbUjAACCCCAQGSBLE3f8ePHPfTQg5FJ2IoAAggggECKBbI0fceNG3fNNdckYNusWdM ffoksCO7IIAAAgggEBDI8PTNz89fsGDe0qVLvIrMmTNnTp/ MAcQAggggAACyQhkePqOHj26evXqJ06cmDLltmSY2BcBBBBAAAEPBXI9rMtvVVWpUmXcuDGrV6/euXPXxIkT2rdvv23btoidnDBh/Jgxo vVq7d79 7f/372smUf2MXuuGPqVVdd1bhxo2rVqhcVFU2b9oC2N23aRItpPVi6dNljjz0esUI2IoAAAggg4CCQyWvfESOG161bd 7c fPmzRfBuHFjI0Lcddd37rvv3oMHD86dO08L5Z/ 9MlevXraJYcPH96 fbsVK1YsXLhw48aN9sayshOzZr2sP0uWlGcwPwgggAACCMQrkMlr37Fjxxw7dkzZeeHChU8//fT660fMmPF8aWlpsFHNmjUnTZq4ZcuWRx55VNsXLVo0c YLN9/8taKi9Xax8 cv/Pznvwzepays7KWXZsULTXkEEEAAAQQCAhm79i0oKOjUqdPixe8qejXaBQveysvLGznyxpC579ChvU5Qd 7cef78ufqj6FWBZs2ac4gggAACCCCQOoGMXfveeustUtPZ5uATzrfccvOcOW8Ea549e06/rlu37sUXZwW2nzhRFl38UvSneAYBBBBAAAFXApmZvtWqVbvuumHFxUfnzy /4mv/DBkyRBdxe/bsuX79 osXL TlVcnJydFtVufOndMNWbt27SouLo5pphPXujkrNzf3/PnzMQtTAAEEEEAAgYgClZUlEZ/ww8Y6deom1g3dLaX01c1Wzz//mzVr1tp/zp8/pwBW4i5f/mFh4eDWrVt36dLl/fffV5QOGDDgpptGtmvXtrCwcOrUqatXf6QPKalp3QitTwzPnj070A2doy4o6NK7d2/9PWjQoFWrViXWQ/ZCAAEEEEhYoKTkeML7 mTH3CuuGOSTroR3Y// A Eb3WwZOfIGFXvvva/ck6wPCN1///3XXnvt008/89xzMx54oKbWwadPn37hhZla0Y4aNUqZrRXtjh07dSU4WiuKc XxgAH9O3bsqPPV0YqxHQEEEEAgdQJ Ti6Xo86ZOHGSy6LmiyWcvua7SosIIIAAAsYE9KW/xtpKUUMZe89ziryoFgEEEEAAgeQFSN/kDakBAQQQQACB ARI3/i8KI0AAggggEDyAqRv8obUgAACCCCAQHwCpG98XpRGAAEEEEAgeQHSN3lDakAAAQQQQCA AdI3Pi9KI4AAAgggkLwA6Zu8ITUggAACCCAQnwDpG58XpRFAAAEEEEhegPRN3pAaEEAAAQQQiE A9I3Pi9IIIIAAAggkL0D6Jm9IDQgggAACCMQnQPrG50VpBBBAAAEEkhcgfZM3pAYEEEAAAQTiEyB94/OiNAIIIIAAAskLkL7JG1IDAggggAAC8QmQvvF5URoBBBBAAIHkBUjf5A2pAQEEEEAAgfgESN/4vCiNAAIIIIBA8gKkb/KG1IAAAggggEB8ArnxFTdbevHixWYbpDUEEEAAgTQQuP32b6ZBLx27yNrXkYcnEUAAAQQQSIEA6ZsCVKpEAAEEEEDAUYD0deThSQQQQAABBFIgQPqmAJUqEUAAAQQQcBQgfR15eBIBBBBAAIEUCJC KUClSgQQQAABBBwFSF9HHp5EAAEEEEAgBQKkbwpQqRIBBBBAAAFHAdLXkYcnEUAAAQQQSIEA6ZsCVKpEAAEEEEDAUYD0deThSQQQQAABBFIgQPqmAJUqEUAAAQQQcBQgfR15eBIBBBBAAIEUCJC KUClSgQQQAABBBwFSF9HHp5EAAEEEEAgBQKkbwpQqRIBBBBAAAFHAdLXkYcnEUAAAQQQSIEA6ZsCVKpEAAEEEEDAUYD0deThSQQQQAABBFIgQPp6hvrOO29v3LjRs qoKIsF/vjH19evX28M4MSJE2   afS0tIEWozW1WTqTKAb7IJA2gnknjx5Iu06bb7D3/ved7/97TsHDRq8adOmBg0aNGrUKLwP77337vXX39CtW7fwp9Jly8WLFx999JFhw67TQNz0Od7ybuq0yzg4u6/EoWRIzxNoLoFdHPoT8tTq1auaNWvmvnygZGK9Onbs6MKFb1199TW1atUKVKX4fOWV//n73zdeuHBh4sRJQ4YMjdifaF2NWGfEGtiIQAICGZBcufn5 QmM3P 7zJjx7Lp16/QiW7Vq1WbNmvfr1  664bn5eUl1nPtWKVK b7PPPPfiuGI6ZtYzb7aq1KlSi1atKhXr57LXsVb3mW1BpxDep7AtCawi/vhJ1zSw1799a//u3fv3jvvvKtq1byGDSO83Uy4k yIQPICGZBcuckr LOGI0eK /TpM3z4iJKS0r179yxYMH/VqlXTpj2Q2JzVrFkzP7 mP0fqba/uu 9f46ow3vJxVZ7Swunb85SyBCrfunXr0KFDe/bsaaY5WkEg2wQyNn01kfXq1e/UqbMe9O/f/8orhzz55E/ 9Kc3pk69Q1t0Mu0vf/nz3/724ZkzZ/T6MnHi5Lp162r7rFkvbdmyuaSkRI/79Ok7Zco3q1evrsdt27YLvP1/4YXf6o82PvXUf9WpU0cPAj LF7 jarXgDt530aKFb7 96OTJk1oxq6Hu3bu/ OLvjh4tnjbtQXvH3/xmRuXKuXfddff58 ffeGPOqlUrtTLr1au3TvdVq1YtuP7Zs3 /adPfjx07VqVKlb59 02YMNHuXrQd58z54/r1RcXFxToB8MADD6kn9uj06 DBhfp75coVqq1du/Z33/1dW2D69B/ptLPOE6jdJUveU89VoH79 vfee1 LFi3DtwSXj1c1vLbgwYY4R6vc3uWll148fPjwgw8 pF/1ZuuJJ37yi1/8StcI9Ovjjz82YMCAW265NURDy8TASFUspLlopAn3MKKnm1ailbl06dL8 fOWLn1fh5bO7vzoRw/rqHA/kHPnzumSrQ427dWyZcvgcdmPT506KTH90a8PPzy9TZu2Ef/JBO8Yrc5oQwiZkcROtof3nC0IpIVAJqdv8AQ0bNhQlzPffXexAjU3N1evIx98sGzs2HFa086d 9fnnnt2 vRHcnJyNm/e1LVrtyuuGFRcfERBqFtRVF713HPP9wK1aa8ePXro1/BltEJal8dKS0v0shLYt3Pnzi1btqpSJXf58uW//e3zv/rVU7169VJa6CVJPdFr6JYtWxS0qvDVV19ROk6d m315A9/ePXPf35z8uTbgkexceOnXboU6PKzuqduP/PM03rNddhxzZqPO3fuMmXK7XqBVhRpdN26dR80aNCePXv0yqtefeMbo/Pyqs6Z8/rrr792zz3/EtyWMuy1115Vx9q3b69gq1 /QfiW4PJ6HJdqzNpCnKNVbvdByB9//H9K6MqVK2/btk0bt2/friGfOnXqwIH9QtCWEI2Qzoc0F3MutHtcPYw4XjetRCuj43P58g  /vVvNG3aTG/m7OgN71W03XVNt6ho3fjxE2rVqv3RR6tDNOxfR4362sCBA/W4UaPGzv52 Wh1RuuD84xE7BIbEcgYgWxJX01Yq1atzp49e/To0Ro1aiiGb7ttytChV2m7rnQ 9tijRUVFvXv31q9aBxQUFOiB1nxaWNjpGzzfWghqFRjxCOjYsaOWtnpKrbz//hJ7X60s7cKtWrXWWnP//n3du/fQ lihq1u0du7codtbtEV/f/jh8h/ cJrdellZqfI7JH1VT vWrbt27aoHbdq0efLJJzZs2NCuXTuHHVWsS5fy7LF/NFhFkf6sW/eJzg3ofcbl3hbrIl gjP2gtLRMD3r37qM3LvYQwrcE76L x6XqXJtqDnZ2rlyF9aZEk7tr1051dfPmzZrizz7bqiWvTp8qlvQGwu5qiEZw/0OacyAN7BVXD8PH62bGo5XRuwqdOQgcw/EOpKysbMWKv91553f0Tk77NmrUMGIA165d2z7UY/qrkmh1RhtCzBkJHhSPEcg8gSxK38DkaRWidae9HtLGJk2a6GVUKWinb6BY48ZNjh8/ntiUa60Q2HfNmjW6ofTgwS/ss8SnTp3WA W0Vh5KX32wpEOHjrqurFWv1sE6HWq3qMdayelUXmBNE9ITrVx1rnjHju26ISyuHe16GjRoePz4Mfux1rV6iVQlWnMHWlEPdd7 Zz978qqrrtaJaN2KFb4luEvxqjrXFjLYmJXrLYLmUXf8Xk7fTTfdNGrlypWqRI/15iOaYUgrgV/VXLykMXsYPl43rUQr88UXB4KP4XgHoqNRA9SBF23HeP1VPlqd0YYQ76S47CrFEEgXgSxK3127dunWZaWIlnpupkevDlqhhpQMzieHSgL77tu3T5d1b775lr59v6X1ylNP/Ye9l67a6pKqzusqm4cMGaKNOgutv  99/v21Uq7mL0xWkO6PKwCCexoNxcYnc7Waot tR8EmtZNavZbB63jf/CD xXH4Vui9S3a9oCMuu1Qm0vn4FZ69uylM/M6q69RXHPNtTpTqjdAOjcwbNiwaJ0JbA9pzg1pvD0MH6 bVqKVUXaq8 F9cDkQJbd219u7mDLuC0SrM9oQ3NdMSQQyUiBbvm3j0KFDOlM3YMBAvRboZJpeoLdu3WLP6MGDB3Vfkk4Lu5lgLVt1DdVNSbuM3virLd3yo6WqfQuYvX3gwCuUDbpupxPR9ulfLbX10nnkyGHdexL4CX95DTStPuv8tm63iXdH951Xuuvk7Y9//Kg6v3TpUu0YviVQWwKqDrWFOLupXB8q03lmLXl15V53q2lhpxnXRV/dARdzyCHNuSFNoIch43VoJTDv0cpou2rT ZKQobkcSPPmLXRY6rO8MWXsAg7 ga5GqzPaEFw2TTEEMlUgk9e WuPqEqDugdq9e7e CkM3LY8bN14TqdO8ugNLN61cflx 15WiVx9PcjPHuuy6bNkynbZVtXqVt 8TdthROao1wbx5c3Wjlr1esQvraw20Snv99T9ou66uaaPu4dLXHehar65f6sVO131VeeD0eKCJFStWqGRubhV9hqpp06a6YVuvwm52dOhkxKf279 /ffu25s2bnzx5qqTkuK4uh28J3jFeVefawp1jTpniVmK67dy fUwTqlvctV6POUcaRXhzMUnDd3HuYfh4HWa8du06ujCh1bw6H7En0tYVAd06d/r0ab0D06Hev/8AvecI71XE3dX0iBHXy0cHW vWbfQeMeIxENjoMLnBXY1Yp8MwA/XrUwZPPPH4DTfceOONI517wrMIZIxAxqZvgwb1P/nkE5041edq9PKkc796cQx828aYMWM1hfarj 6TmjTpNodVZvBkjxs34Xe/m/nss7/WpWIla8xXdq0adWuMTjIrgNW6dgl8bvjqq69du3bt0KFXB qfNGmyXqpUWFdhdYZct7OGH2dastjnVDt16jR16vcVvSrjZsfwqpy36AVRH2g5cuSIllN6nyFAvYkJ2RJSQ1yq4fU7O8esXDM4eHCh3mbZN77169df4VRYWOg8TPvZ8GmNSRq i3MPI443Wiu33vr11157RWvTwsIro5XRdoXiW28t0O1O jBbQUFXpW94r6LtPnr0GO2uG XUMR11ujoe8vE2l5Mb3NVodUbrg5upoQwCmSqQM3nyZN O7eWXZ/u2bxXSseAP11ZIB2gUAQQQ8IPA1Km3 6EbyfQhW677JmPEvggggAACCHgrQPp660ltCCCAAAIIxBbI2Ou sYeehiX07Ylp2Gu6jAACCCAQKsDaN1SE3xFAAAEEEEi1gLn01WcbUj0Y6kcAAQQQQCAtBMylb1pw0EkEEEAAAQQMCJC BpBpAgEEEEAAga8IkL4cEAgggAACCJgWIH1Ni9MeAggggAACpC/HAAIIIIAAAqYFSF/T4rSHAAIIIIAA6csxgAACCCCAgGkB0te0OO0hgAACCCBA nIMIIAAAgggYFqA9DUtTnsIIIAAAgiQvhwDCCCAAAIImBYgfU2L0x4CCCCAAALm0jcvLw9uBBBAAAEEEJCAufSFGwEEEEAAAQRsAdKXIwEBBBBAAAHTAqSvaXHaQwABBBBAgPTlGEAAAQQQQMC0AOlrWpz2EEAAAQQQIH05BhBAAAEEEDAtQPqaFqc9BBBAAAEESF OAQQQQAABBEwLkL6mxWkPAQQQQAAB0pdjAAEEEEAAAdMCpK9pcdpDAAEEEECA9OUYQAABBBBAwLQA6WtanPYQQAABBBAgfTkGEEAAAQQQMC2QW1ZWZrpN2kMAAQQQQCAJgQxIrtz8/PwkBNgVAQQQQAAB0wIZkFyceTZ90NAeAggggAACpC/HAAIIIIAAAqYFSF/T4rSHAAIIIIAA6csxgAACCCCAgGkB0te0OO0hgAACCCBA nIMIIAAAgggYFqA9DUtTnsIIIAAAgiQvhwDCCCAAAIImBYgfU2L0x4CCCCAAAKkL8cAAggggAACpgVIX9PitIcAAggggADpyzGAAAIIIICAaQHS17Q47SGAAAIIIED6cgwggAACCCBgWoD0NS1OewgggAACCJC HAMIIIAAAgiYFiB9TYvTHgIIIIAAAqQvxwACCCCAAAKmBUhf0 K0hwACCCCAAOnLMYAAAggggIBpAdLXtDjtIYAAAgggQPpyDCCAAAIIIGBagPQ1LU57CCCAAAIIkL4cAwgggAACCJgWIH1Ni9MeAggggAACpC/HAAIIIIAAAqYFSF/T4rSHAAIIIIAA6csxgAACCCCAgGkB0te0OO0hgAACCCBA nIMIIAAAgggYFqA9DUtTnsIIIAAAgiQvhwDCCCAAAIImBYgfU2L0x4CCCCAAAKkL8cAAggggAACpgVIX9PitIcAAggggADpyzGAAAIIIICAaQHS17Q47SGAAAIIIED6cgwggAACCCBgWoD0NS1OewgggAACCJC HAMIIIAAAgiYFiB9TYvTHgIIIIAAAqQvxwACCCCAAAKmBXJNN2ikvdLS40baoREEEEAAgcQFatWqk/jOab5nZqZvNs9omh QdB8BBBDICgHOPGfFNDNIBBBAAAFfCZC vpoOOoMAAgggkBUCpG9WTDODRAABBBDwlQDp66vpoDMIIIAAAlkhQPpmxTQzSAQQQAABXwmQvr6aDjqDAAIIIJAVAqRvVkwzg0QAAQQQ8JUA6eur6aAzCCCAAAJZIUD6ZsU0M0gEEEAAAV8JkL6 mg46gwACCCCQFQKkb1ZMM4NEAAEEEPCVAOnrq mgMwgggAACWSFA mbFNDNIBBBAAAFfCZC vpoOOoMAAgggkBUCpG9WTDODRAABBBDwlQDp66vpoDMIIIAAAlkhQPpmxTQzSAQQQAABXwmQvr6aDjqDAAIIIJAVAqRvVkwzg0QAAQQQ8JUA6eur6aAzCCCAAAJZIUD6ZsU0M0gEEEAAAV8J5PqqN3QGAQQQyBKBOcWVpm7NOZ8low0bprLn5U6Xxte/GPZMtmxg7ZstM804EUDAVwLZHL2aCL3tkICvZsRwZ0hfw A0hwACCJQLZO2qNzD9WS5A vJCgAACCCCAgGkB0te0OO0hgAACCCBA nIMIIAAAgggYFqA9DUtTnsIIIAAAgiQvhwDCCCAAAIImBYgfU2L0x4CCCCAAAKkL8cAAggggAACpgVIX9PitIcAAggggADpyzGAAAIIIICAaQHS17Q47SGAAAKGBQbVsuZ1s44XWievtJb3skY3 Gf7hwdbC7t/ euoeta5IdabXS2CwcAEgWwAmSYQQACBChMYWa88cQfWsmZ9Yf16n9U0rzxf/615aH8Ka1lzuloflli3bbKy978 CFVJ4e/8H0cpxKVqBBBAoGIF9P8YzOholV2w q219p4t78vPdlsf9bF 0dZ65aB15B9ftdyrhjW/u7XxpHXrRuv0pYrtcra0zto3W2aacSKAQBYK9Khhta1qzT74ZfRKoPSC9ew q0Yla0TdLz1aV7Xe6WntPmON3GCVXMhCpIoZMulbMe60igACCBgQaFylvJFdZ77S1I7LvzbJ 3Jj1xqWiq0qtY5m f86ZGA gprgzLNZb1pDAAEEDAocPFfeWKuqX2myzeVfD11 Sj9LjlvbTlt3N7WqV7K tcXixPNXsFL2C2vflNFSMQIIIFDRAhtOli98b29sNf/HSrdmJeveZtaZS9a7x77s3NmL1l1braf3Wd9sbP1nu4rucda0z9o3a6aagSKAQPYJaCF73 fWX7pZa/tarx2yzly0xja0OlSzHtpu2cviAMkPt1kt86x/b2F9XGa9eij7pIyPmLWvcXIaRAABBAwKzCu2hhVZ605Y32lS/kGjI esiZusp/aG9kA5fccWa sp67mO5THMT6oFWPumWpj6EUAAgQoW KDEumFD5D40XPnP7WUXrc4fRy7GVs8FWPt6TkqFCCCAAAIIxBAgfWMA8TQCCCCAAAKeC5C npNSIQIIIIAAAjEESN8YQDyNAAIIIICA5wKkr ekVIgAAggggEAMAdI3BhBPI4AAAggg4LkA6es5KRUigAACCCAQQ4D0jQHE0wgggAACCHguQPp6TkqFCCCAQGwBvuooywVI39j/SCiBAAIIeC7wcqdL2Rw/GrsEPFdNowqzefbTaJroKgIIZJrA PoXxw/KtEExHvcCrH3dW1ESAQQQQAABbwRIX28cqQUBBBBAAAH3AqSveytKIoAAAggg4I0A6euNI7UggAACCCDgXoD0dW9FSQQQQAABBLwRIH29caQWBBBAAAEE3AuQvu6tKIkAAggggIA3AqSvN2Et 7MAAAIuSURBVI7UggACCCCAgHsB0te9FSURQAABBBDwRoD09caRWhBAAAEEEHAvQPq6t6IkAggggAAC3giQvt44UgsCCCCAAALuBUhf91aURAABBBBAwBsB0tcbR2pBAAEEEEDAvQDp696KkggggAACCHgjQPp640gtCCCAAAIIuBcgfd1bURIBBBBAAAFvBHydvm /vcibUVILAggggECmCCxatDADhpIzefLkDBgGQ0AAAQQQQCCNBHy99k0jR7qKAAIIIICAewHS170VJRFAAAEEEPBGgPT1xpFaEEAAAQQQcC9A rq3oiQCCCCAAALeCJC 3jhSCwIIIIAAAu4FSF/3VpREAAEEEEDAGwHS1xtHakEAAQQQQMC9AOnr3oqSCCCAAAIIeCNA nrjSC0IIIAAAgi4FyB93VtREgEEEEAAAW8ESF9vHKkFAQQQQAAB9wKkr3srSiKAAAIIIOCNAOnrjSO1IIAAAggg4F6A9HVvRUkEEEAAAQS8ESB9vXGkFgQQQAABBNwLkL7urSiJAAIIIICANwKkrzeO1IIAAggggIB7AdLXvRUlEUAAAQQQ8EaA9PXGkVoQQAABBBBwL0D6ureiJAIIIIAAAt4IkL7eOFILAggggAAC7gVIX/dWlEQAAQQQQMAbAdLXG0dqQQABBBBAwL0A6eveipIIIIAAAgh4I0D6euNILQgggAACCLgXIH3dW1ESAQQQQAABbwRIX28cqQUBBBBAAAH3Av8PYqLQpe1PtncAAAAASUVORK5CYII=[/IMG]

---

### Post by oldfred on 2019-08-13
Did you post something? Please do not post screen shots if terminal output. Copy & paste terminal output & use code tags to preserve formatting. If from gui app, attach screen shot with paperclip icon in Forum's advanced editor.

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 
    
Think of a drive as a file cabinet and the drawers as the partitions. You then can have one file cabinet with one drawer or many drawers.
Microsoft confuses "drive" and partitions as a "d" drive in Windows can be a second partition on the first drive or the first partition on the second drive. In Linux drives are clear separated as sda, sdb, sdc etc, or newer NVMe as nvme0n1, nvme0n2.  And partitions are the number at the end or sda1, sda2.

LVM uses volumes but often is inside one large partition on a drive. LVM can span drives.

---

### Post by brenneke on 2019-08-13
Good learning thank you.

User "rslsync" does not have permissions to this partition. What if the user was Mary, how could we sort this out so she would have all required permissions?

```
rslsync:x:999:999::/home/rslsync:/sbin/nologin
```

---

