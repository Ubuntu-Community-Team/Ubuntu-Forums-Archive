---
title: "'Unable to mount location' - 'Failed to mount Windows Share: Permissions denied'"
date: 2017-01-25
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-01-25
I've been trying to share a folder, it's actually an 'external' (permanent internal) HDD connected to another computer. I have a bunch of movies and TV shows, and I would like to access from other computers on my network.

I went into properties and went to the share tab via nautilus file manager, and it shows up on my network, and the folder as well, but I get this error, whether I sign in or by guest/anonymous:

Error when connected via sign-in:
'Unable to mount location

Failed to mount Windows share: Invalid argument'

Error when connecting via guest/anonymous:
'Unable to mount location

Failed to mount Windows share: Permissions denied'

I tried setting the permissions for that folder as 'sambashare'.

---

### Post by TheFu on 2017-01-25
What OS is the computer the disk is physically attached to running?
What OS are all the devices you want to provide access to the media running?

---

### Post by 99victor on 2017-01-25
If you follow this guide below to the tee and it still doesn't work, your problem probably resides in how your remote shared drive is configured.[URL="https://wiki.ubuntu.com/MountWindowsSharesPermanently"]
https://wiki.ubuntu.com/MountWindowsSharesPermanently[/URL]

EDIT: This is of course assuming you are trying to connect to a remote share from an Ubuntu OS.

---

### Post by ThePowerpuffGirls on 2017-01-26
Both computers are running Ubuntu 16.04 64-bit.

---

### Post by TheFu on 2017-01-26
Unix to Unix file sharing should use NFS. That is the native storage sharing protocol for Unix/Linux. It provides the same file/directory permissions as other Unix storage and it is faster than other methods.

There is an nfs-server that needs to be installed (it is a kernel module) and some common nfs libraries for both sides.  Configure the server to "export" the storage you want shared, how you want it shared; read-write, read-only, strict mounts, soft-mounts, etc. Then you mount it from the client using the /etc/fstab or a manual mount command.  File and directory permissions work as you expect provided the numbers for the uid/gid match for all the files between all the involved systems.  Normally, that means real people userids have the same uid (a number) and gid (also a number) between both systems.  

So you should decide which sort of file sharing you'd like to use between these systems. If you want to use NFS, I can help. If you want to use Samba (which is really cifs), I've never set that up using a GUI and cannot help.  I have used samba with a few text file managed configurations, but have never used a Linux client to connect to a Linux Samba server. 

Someone else will have to help if you want to do that via a GUI.  I'd check the "[Ubuntu Desktop Guide]("https://help.ubuntu.com/lts/ubuntu-help/index.html")" and "[Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/")" for how-tos for each part - client and server, respectively. There are probably other how-tos from respectable websites too, but those will make many assumptions that may or may not be true for your systems.

---

### Post by yancek on 2017-01-26
The link below is to the official Ubuntu documentation on installing nfs server and client which also has example entries for your /etc/exports and /etc/fstab files.  Interesting that you get the message in your thread when both computers are using Ubuntu?

[URL="https://help.ubuntu.com/community/SettingUpNFSHowTo"]https://help.ubuntu.com/community/SettingUpNFSHowTo



[/URL]

---

### Post by Morbius1 on 2017-01-26
If you are still interested in pursuing Samba, go to the machine where you created the share and post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

A "Failed to mount Windows share: Permissions denied" error is generally a Linux issue not a Samba issue but we really won't know until we see how samba is set up on that machine.

Just in case this is something else post your host name on that machine as well please:
```
hostname
```

---

### Post by ThePowerpuffGirls on 2017-01-26
I think I might go with the Samba for now, it appears to be easier.

testparm -s
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb




[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

net usershare info --long
```



[Videos]
path=/media/alexa/6TBHDD/Videos
comment=
usershare_acl=Everyone:R,Unix User\alexa:F,
guest_ok=y

```

hostname
```

Alexas-PC

```

---

### Post by TheFu on 2017-01-26
> **ThePowerpuffGirls said:**
> I think I might go with the Samba for now, it appears to be easier.


Appearance is deceiving. NFS is extremely flexible (hence all the complex options), but a normal use is pretty trivial to configure provided the storage is all Linux/Unix formatted (not NTFS/vfat/fat32). Plus the storage is mounted for everyone, not just 1 userid.

I know a little about samba.  It appears that the config file posted doesn't have any shares configured. Nothing is shared.
I've never used the "usershare" stuff or seen the ACLs used in this way. That's all new to me.

First, the storage in /media/alexa isn't a good place to have shared storage.  That area is for automatic, temporary, storage that the OS mounts only as requested by a user. It isn't there at boot. It isn't mounted until a user requests it. There are other reasons to move the storage that I've learned over the years. Let's say we move it to /Videos/6TBHDD (do this in the fstab).

Then, I would add a stanza to the /etc/samba/smb.conf file that looks like this:
```
[Videos]
path=/Videos/6TBHDD
comment=6TBHDD Videos
browseable = yes
guest ok = yes
```
This share will be available even if you don't log into the system, provided the storage is mounted at boot via the fstab.

Whatever you did to make the "usershare" would need to be removed/cleaned up too.

HowToGeek had a usable samba how-to a few years ago that seemed to work. 
There is also howToForge with guides for all sorts of things. Both are fairly reputable.

Anyway, that is what I would do if staying with samba.

Wish I could help more. Sorry.

---

### Post by ThePowerpuffGirls on 2017-01-27
Update: I got ti working, however it only works on mine., and half of the movies show up as like a code,
Maybe I added 'force user = alexa'
I haven't tried it on another computer yet, but will when I get up. Any idea why some of the movie files are showing up in 'code'?

[http://i68.tinypic.com/2m7akxk.png](http://i68.tinypic.com/2m7akxk.png)

---

### Post by TheFu on 2017-01-27
I have **NEVER** used "force user" in the last 20 yrs running samba.

Please post a link to the img, so people with limited bandwidth or using cell phones don't have to download it.

If you are talking about filenames showing up as 8.3 and not what is expected, my only guess is that a different character encoding is being used at display than what the file system was written using. That is just a **locale** setting difference. [https://unix.stackexchange.com/questions/2089/what-charset-encoding-is-used-for-filenames-and-paths-on-linux](https://unix.stackexchange.com/questions/2089/what-charset-encoding-is-used-for-filenames-and-paths-on-linux)  Think it is possible to change it at mount time using the iocharset option for some file system types - usually non-Linux file systems.

---

### Post by Morbius1 on 2017-01-27
> [Videos] path=/media/alexa/6TBHDD/Videos
comment=
usershare_acl=Everyone:R,Unix User\alexa:F,
guest_ok=y
The system creates /media/alexa not you and it set's permissions such that only "alexa" can get to whatever is beyond it. "force user = alexa" is an acceptable solution to this issue. Especially since this is a guest accessible share.

> Any idea why some of the movie files are showing up in 'code'?
I'm not sure what you are referring to there.

---

### Post by ThePowerpuffGirls on 2017-01-27
It works, I'm able to browse the movies on another computer, tested with both computer, one with the 6TB and another with the 4TB HDD.
Both some movies show up as 'code', by code' I mean, random letters and numbers, like 1AKXJT-0.AVI, 20270Z-9.MKV, A6V3YL-9.MKV, if you look at the photo, you'll see what I mean. They only show up like that when viewing remotely. I don't know why only some show up like that.

I don't know how to edit the photo to only a hyperlink, and it won't let me view it HTML, but I will try and fix it.
Update: I've fixed the photo to only show as a hyperlink. :)

Update:
I counted 14 movies on the 4TB HDD, that have been 'coded', and TV shows, there are 4, along with all the files in the in a certain TV shows that has been coded, are 'coded' as well.
For example, the folder 'Beyond Belief: Fact Or Fiction? (1997&#8211;2002) (Completed)' is now 'BV50M5~2'.
Here is a screenshot of the files in that folder.
[http://i64.tinypic.com/wsv4oy.png](http://i64.tinypic.com/wsv4oy.png)

---

### Post by TheFu on 2017-01-27
Perhaps an **iocharset** issue with the mount?
You can compare the file sizes on both systems to figure out what the real name should be.

---

