---
title: "Trouble with smb mounts unmounting"
date: 2023-11-27
forum: General Help
---

### Post by dansity on 2023-11-27
Hello,
I have the following issue: I mount smb shares from my NAS to my /mnt folder with the following fstab entry:
```
//192.168.1.200/Private                     /mnt/Private    cifs   credentials=/home/daninet/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,_netdev   0 0
//192.168.1.200/Work                        /mnt/Work       cifs   credentials=/home/daninet/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,_netdev   0 0
//192.168.1.200/Download                    /mnt/Download   cifs   credentials=/home/daninet/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,_netdev   0 0
```

When I open up my system in the morning it is a hit or miss if any of these mounted properly. In some other case they are mounted and I find after an hour they are not reachable anymore.
However it is always the mount directory that breaks. So I can access /mnt/Private/Documents but the mount dir /mnt/Private unreachable. They also look like this in the file system:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293125&stc=1[/IMG]

I have that little remount.sh script there that unmounts them then mounts -a so the issue can be fixed, but this is still a hassle.
I'm unable to find pattern or causes. Sometimes it is related when I use the xdg-desktop-portal to save a file, in some other cases it happens the same time when I access the same shares in a windows guest in KVM.
Only my kubuntu install is affected with this trouble. My NAS is an unraid server, I don't have reliability or access issues to it on any other device.

I have extracted my syslog [can be checked here]("https://drive.tevehome.eu/s/SDYqBqMyAD966Qj"). You can search for "/mnt/Private" in it to see the mounts and issues.

Kubuntu 23.10
Kernel 6.5.0-13
Plasma 5.27.8

---

### Post by TheFu on 2023-11-27
You should use NFS, not CIFS for Unix-based NAS devices.  Look up how to enable NFS.

While I wouldn't mount anything under /mnt that isn't just for temporary administrative needs, at least you didn't mount under /media and are stuck fighting with gvfs and/or gio crab mounts.

I don't know which versions of CIFS are supported by your NAS.  I don't mount CIFS in the fstab. I use autofs, but here's an example mount with options:
```
win7ult  -fstype=cifs,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7-D.credentials  ://172.22.22.8/Data
```
You can figure out the options, I'm certain.

Win7 supports only version 2.1.
autofs only mounts the storage when it is requested and while it is being used.  If there aren't any open files on the mount, it will be automatically removed after 2 minutes. It is all automatic.

Here's an example NFS auto.nfs config:
```
/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D1
```

In fact, this should work well enough, if you don't want the other options:
```
/d/D1 -fstype=nfs  istar:/d/D1
```

That would be 
```
istar:/d/D1    /d/D1    nfs   defaults   0    0 
```
In an fstab.

---

### Post by dansity on 2023-11-27
Thank you,
I have setup autofs and I have the shares mounted now. I have things mounted in /mnt because the directory name is mount. I think it is logical but of course linux community always has different opinions :) I had my hard drives mounted for quite same time windows-like /d /e and so on :)  I guess thats inherent sin as well :)
I had some hard drives mapped with fstab in /mnt, seems like autofs and fstab does not work together for the same directory, my mapped drive directories disappeared. Is this the case and I have to map the drives in autofs also or am I missing something and they should work together?

---

### Post by TheFu on 2023-11-27
> **dansity said:**
> Thank you,
I have setup autofs and I have the shares mounted now. I have things mounted in /mnt because the directory name is mount. I think it is logical but of course linux community always has different opinions :) I had my hard drives mounted for quite same time windows-like /d /e and so on :)  I guess thats inherent sin as well :)
I had some hard drives mapped with fstab in /mnt, seems like autofs and fstab does not work together for the same directory, my mapped drive directories disappeared. Is this the case and I have to map the drives in autofs also or am I missing something and they should work together?


Unix and Linux standards for what goes in which places might be helpful.  Violate those standards at your own peril.  The short version is here: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)  and I've seldom needed to look beyond the table.  BTW, Canonical violates those standards a few places - especially with Gnome and Snaps.

MS-Windows has been lying to people since the beginning.  Nobody mounts "drives".  We mount "file systems" and those file systems are often placed into "partitions", never "drives."  This leads to confusion. You can choose to remain inaccurate and cause confusion to yourself and others, or you can be accurate and clear.

Anytime two different subsystems try to manage mounts, there is a chance for collisions. This has been an issue across at least 2 decades, if not more.  I remember using amd in the mid-1990s.  Now, since 2016, the fstab code has been completely taken over by systemd-mount, which is full of issues and removed some conveniences that admins loved.

If you want directories controlled by autofs to stay around, use the --ghost option in the auto.master.  There are good reasons to do this and there are good reasons NOT to do it.  Either method is a "feature" to someone.  For example, I generally don't use the --ghost option, but if I was mainly a GUI user, having something to click which would cause the mount to happen would be a necessity. After all, a GUI can't click on nothing. OTOH, having storage that isn't mounted show up for anyone to see would be a security issue in some situations.

---

### Post by MAFoElffen on 2023-11-28
+1 -- Amen.

I routinely (again, and again, and again...) tell people not to mount permanent mounts to /media or /mnt. Both are meant for "temporary mounts". For example: That 'routinely' causes problems when trying to use recovery tools that do need to use those folders temporarily... If things go wrong, you do want to be able to recover from a disaster, right?

It's just so easy not do that, and just to create new, empty folders wherever you feel is appropriate and easy for you to remember, and mount to those instead.

As for SMB mounts... [INDENT]Are you sure your NAS is SMB protocol version 3? I would play with that between 2.1 & 3.0
Are the clocks synced between your NAS and your client?
[/INDENT]

From the Docs:
> 
The MountCifsFstab page demonstrates how to mount a windows share with minimal fuss, but if security is worth some extra fuss to you, then you&#8217;ll need to quit using that convenient NOPERM option. NOPERM is short for &#8220;no permission checks&#8221;

I would use something similar to
```

//server/share /pathto/mountpoint cifs credentials=/etc/smbcredentials,iocharset=utf8,uid=1000,gid=1000,file_mode=0644,dir_mode=0777,_netdev   0 0

```
'noperm' option is not recommended. AFAIK, 'nounix' is a default flag with SMB, unless you explicitly set the ver=1.0.

---

