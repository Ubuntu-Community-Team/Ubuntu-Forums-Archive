---
title: "error with mount.cifs at bootup"
date: 2008-04-18
forum: General Help
---

### Post by ashrack on 2008-04-18
This is the error I receive at bootup when it mounts my CIFS share. But the cifs share works great.
The error log:
```
unknown mount option f

Usage:  /sbin/mount.cifs <remotetarget> <dir> -o <options>

Mount the remote target, specified as a UNC name, to a local directory.

Options:
        user=<arg>
        pass=<arg>
        dom=<arg>

Less commonly used options:
        credentials=<filename>,guest,perm,noperm,setuids,nosetuids,rw,ro,
        sep=<char>,iocharset=<codepage>,suid,nosuid,exec,noexec,serverino,
        directio,mapchars,nomapchars,nolock,servernetbiosname=<SRV_RFC1001NAME>

Options not needed for servers supporting CIFS Unix extensions
        (e.g. unneeded for mounts to most Samba versions):
        uid=<uid>,gid=<gid>,dir_mode=<mode>,file_mode=<mode>,sfu

Rarely used options:
        port=<tcpport>,rsize=<size>,wsize=<size>,unc=<unc_name>,ip=<ip_address>,
        dev,nodev,nouser_xattr,netbiosname=<OUR_RFC1001NAME>,hard,soft,intr,
        nointr,ignorecase,noposixpaths,noacl

Options are described in more detail in the manual page
        man 8 mount.cifs

To display the version number of the mount helper:
        /sbin/mount.cifs -V

```
The fstab line that connects to my other computer which has Win2k3:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d064ff64-d14a-4339-8daa-1065cfe28610 /               reiserfs notail,relatime  0       1
# /dev/sda1
UUID=D42898CC2898AF4C /media/win      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=774cf38a-00be-4440-9ee7-bca3c30000b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# network
//192.168.0.1/d /media/x cifs credentials=/root/ashrack.cred,noperm,nocase,file_mode=0777,dir_mode=0777 0 0

```

I am using latest Hardy

---

### Post by herbster on 2008-04-18
Can you paste your entire fstab?

---

### Post by ashrack on 2008-04-18
pasted. Did not paste it before because removing the line that connects to the other computer fixes the error and thus didn't thing the entire fstab was neccessary

---

### Post by herbster on 2008-04-18
I'm leaning towards it being an unnecessary character in your ashcrack.cred file. The line itself is fine.

---

### Post by dschaefer79 on 2008-04-25
I have the same problem

---

### Post by herbster on 2008-04-25
Can you paste your fstab dschaefer79? Also the output of "sudo fdisk -l" in [code] tags please.

---

### Post by ashrack on 2008-04-26
> **herbster said:**
> I'm leaning towards it being an unnecessary character in your ashcrack.cred file. The line itself is fine.

this is the ashrack.cred file:
```
username=foo
password=foo
```

I see nothing wrong with it

---

