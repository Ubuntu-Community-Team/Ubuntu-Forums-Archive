---
title: "mounting external drives with fstab in Ubuntu 16.04"
date: 2017-05-10
forum: General Help
---

### Post by ditzel on 2017-05-10
Hey guys,

I am trying to mount external drives in the fstab file via

//xxx.xxx.xxx.xxx/Data 					/media/institute 	cifs	soft,auto,uid=1000,gid=1000,credentials=/home/myName/.secure/.credentials,domain=XXX-XXX,sec=ntlm 		0 	0

however, I am constantly experiencing freezes, i.e. hangups of the OS, sometimes only for a couple of seconds, other times for minutes, and rarely I even have to kill my lightdm service in order to come back.

Do you know what I am doing wrong here?  Sometimes it seems to work though, but not for long =(

thanks in advance

---

### Post by ditzel on 2017-05-11
anyone?

---

### Post by yancek on 2017-05-11
On newer Ubuntu releases, partitions on external drives are available to be accessed/mounted under the /media/username directory (substitute actual username).  Are the filesystems on the external drive partitions windows filesystems?  The entry you posted from fstab looks more like an entry for a network system than an external drive.

---

### Post by sp40140 on 2017-05-11
Are you able to successfully mount and access the drives with your entries?
Is is possible that your systemwide issues are caused by something different?
Having said that, my fstab entries has different format. The default fstab has syntax in comment section to help. That's what I used and my fstab works fine.
I can't say fstab allows or doesn't allow multiple formats.
But here is what I have:
The format provided by fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

```
One of my entries:
```

UUID=4788C72789C745F8	/media/DATA/DELL-M	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0

```

---

### Post by Morbius1 on 2017-05-11
You are experiencing a hang of your whole operating system or just the /media/Institute mount?

If it's the latter I would suggest exploring the version of the dialect that the SMB server is using: [https://blogs.technet.microsoft.com/josebda/2013/10/02/windows-server-2012-r2-which-version-of-the-smb-protocol-smb-1-0-smb-2-0-smb-2-1-smb-3-0-or-smb-3-02-are-you-using/](https://blogs.technet.microsoft.com/josebda/2013/10/02/windows-server-2012-r2-which-version-of-the-smb-protocol-smb-1-0-smb-2-0-smb-2-1-smb-3-0-or-smb-3-02-are-you-using/)

By default a cifs mount in Linux runs with SMB1. SMB1 is today considered "chatty" and sometimes the low level passing of information gets so discombobulated that the share disconnects or appears to freeze. SMB2 is better but SMB3 runs supreme - assuming the SMB server can handle it.

You specify this parameter in Linux with the "vers" option in your mount. For example if you are connectiong to a Win10 machine your line in fstab would look like this:
> //xxx.xxx.xxx.xxx/Data                     /media/institute     cifs     soft,auto,uid=1000,gid=1000,credentials=/home/myName/.secure/.credentials,domain=XXX-XXX,sec=ntlm[COLOR=#0000cd]**,vers=3.0**[/COLOR]          0     0
Not sure if this applies to you since the "sec=ntlm" seems a bit odd unless you are accessing a system with a very old version of Windows or SMB / Samba.

---

