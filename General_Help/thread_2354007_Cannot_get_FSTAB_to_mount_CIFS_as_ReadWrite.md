---
title: "Cannot get FSTAB to mount CIFS as Read/Write"
date: 2017-02-27
forum: General Help
---

### Post by nexist on 2017-02-27
Hello:

I have two machines, a Windows 10 box and an Ubuntu 16.10 box. The Windows 10 box has a drobo attached where I store my music and videos. These two directories are shared as "Audio" and "Visual". When I mount them via fstab, they are visible, mounted and accessible. However, I cannot write to the directories. These directories are accessible from Mac and other Windows machines and they are able to write to these shares.

There may be extraneous stuff in my fstab, since I've been trying advice/solutions from various forums and threads. I receive no errors from mounting the fstab.

```
UUID=8449-008C  /boot/efi       vfat    utf8,umask=007,gid=46 0       1
UUID=409c2aac-5515-4120-b882-d22996b46993 none            swap    sw              0       0
//192.168.0.10/Visual /media/Visual cifs credentials=/home/nexist/.smbcredentials,iocharset=utf8,sec=ntlm,noperm, 0 0
//192.168.0.10/Audio /media/Audio cifs credentials=/home/nexist/.smbcredentials,iocharset=utf8,sec=ntlm,noperm, 0 0
```

And the output from mount:
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8130048k,nr_inodes=2032512,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1630360k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1630360k,mode=700,uid=1000,gid=1000)
/dev/sda1 on /boot/efi type vfat (rw,relatime,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro)
//192.168.0.10/Visual on /media/Visual type cifs (rw,relatime,vers=1.0,sec=ntlm,cache=strict,username=nexist,uid=0,noforceuid,gid=0,noforcegid,addr=192.168.0.10,file_mode=0755,dir_mode=0755,nounix,serverino,mapposix,noperm,rsize=61440,wsize=65536,echo_interval=60,actimeo=1)
//192.168.0.10/Audio on /media/Audio type cifs (rw,relatime,vers=1.0,sec=ntlm,cache=strict,username=nexist,uid=0,noforceuid,gid=0,noforcegid,addr=192.168.0.10,file_mode=0755,dir_mode=0755,nounix,serverino,mapposix,noperm,rsize=61440,wsize=65536,echo_interval=60,actimeo=1)
```

I did manage to get a workaround by chmod 777 to /media & the two share points, but I dislike modifying root permissions for the file structure when there should be a way to do it via mount options, since I doubt that anyone mounting a cifs partition is changing directory permissions willy-nilly.

---

### Post by HermanAB on 2017-02-27
Mounting CIFS/SMB at boot time usually doesn't work, because the network isn't ready when the fstab data is executed.

You will have more luck if you enable rc.local and put in a healthy 'sleep 10' to let the dust settle, followed by a 'mount' command for the share.

---

### Post by nexist on 2017-02-28
I've not done that before, is there a good HOWTO or step by step somewhere?

---

### Post by deadflowr on 2017-02-28
I think you can add _netdev and uid=nexist to your options list to get both the networking and user correctly set.
_netdev makes the share wait to mount until the network connection is definitely established.
(there is always the factor of the the system putting the cart before the horse and getting fstab going before the networking is set)

and the uid=nexist should set your user as the correct user.
(Currently, even though the username is nexist, the uid is 0(or root).)

so I think add those to the line(s) like this
[CODE]credentials=/home/nexist/.smbcredentials,iocharset=utf8,sec=ntlm,noperm,**_netdev,uid=nexist[**/CODE]

See if that helps.

---

### Post by nexist on 2017-02-28
Thank you very much. That worked perfectly.

> **deadflowr said:**
> I think you can add _netdev and uid=nexist to your options list to get both the networking and user correctly set.
_netdev makes the share wait to mount until the network connection is definitely established.
(there is always the factor of the the system putting the cart before the horse and getting fstab going before the networking is set)

and the uid=nexist should set your user as the correct user.
(Currently, even though the username is nexist, the uid is 0(or root).)

so I think add those to the line(s) like this
```
credentials=/home/nexist/.smbcredentials,iocharset=utf8,sec=ntlm,noperm,**_netdev,uid=nexist**
```

See if that helps.

---

