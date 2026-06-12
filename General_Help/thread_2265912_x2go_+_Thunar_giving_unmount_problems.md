---
title: "x2go + Thunar giving unmount problems"
date: 2015-02-18
forum: General Help
---

### Post by gorellana09 on 2015-02-18
Hello folks,

Hopefully I am able to explain myself what my problem is. I run a dedicated server to which I have been using x2goclient to connect to it from my linux laptop. For many months it worked fine. However recently my main laptop died on me and I was forced to use a borrowed computer using windows only. I had to install x2go on windows so I could continue work on my server, all fine up until then. I was finally allowed to keep that laptop after some time and so I installed linux on it (dualboot windows vista + linux mint). I installed x2goclient so that I could connect to my xubunutu server. All fine for some time but now I have a problem after I had to share a folder now when I try to suspend my session x2go tells me that fuser failed to unmount something and that device is busy. Upon reconnection to my xubuntu server I now have thunar stuck for about 15 seconds each time i open it the first time, and it will launch twice (every time) then when I try to close the second instance I get an error saying device busy. Openining thunar is a pain each time, but if i leave it open i can browse files fine and quick, the problem is only when opening file manager. 

I have tried uninstalling and reinstalling x2go on both subuntu server and my laptop but that did not do the trick. I've tried force unmounting the said directory but it will only mount back again when I initiate a new session. I have rebooted my server repeatedly and problem persists. 

I should also mention that if I use windows and connect to my server with x2go I don't have the problem. Problem is only when I use linux +x2go. I am getting very frustrated and this is messing with my productivity. Any help would be greatly appreciated and will get you lots of hugs. 

my server is running Xubuntu 14.04

my laptop is running Linux Mint 17.1

---

### Post by TheFu on 2015-02-18
Is the mouted storage local or remote? 
Output from **df -h** would be helpful too.

---

### Post by gorellana09 on 2015-02-18
I am not sure but here is some output

```

desktop@ns506811:~$ sudo df -h
[sudo] password for desktop: 
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G  6.6G   12G  37% /
devtmpfs        3.9G  4.0K  3.9G   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            788M  3.6M  785M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  8.0K  3.9G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda3       1.8T   14G  1.7T   1% /home



```

and this might help notice the last mounted drive with the long string, that is the one causing the issues

```

desktop@ns506811:~$ mount
/dev/root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=4033320k,nr_inodes=1008330,mode=755)
sysfs on /sys type sysfs (rw,relatime)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/cgroup type tmpfs (rw,relatime,size=4k,mode=755)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /run type tmpfs (rw,nosuid,noexec,relatime,size=806756k,mode=755)
none on /sys/fs/pstore type pstore (rw,relatime)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /run/user type tmpfs (rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755)
/dev/sda3 on /home type ext4 (rw,relatime,data=ordered)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
geo@127.0.0.1:/home/geo/.x2go/S-desktop-50-1424283561_stDXFCE_dp24/spool on /tmp/.x2go-desktop/spool/C-desktop-50-1424283561_stDXFCE_dp24 type fuse.sshfs (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000,default_permissions)
desktop@ns506811:~$ 



```

Thank you for replying.

---

### Post by TheFu on 2015-02-18
gvfs is a terrible way to mount things, IMHO. Others disagree.  See how it doesn't show up in the df output? That's a problem with gvfs. It doesn't really mount the storage.

On which machine is the storage giving issues actually connected?  Looks like a flash drive to me but is it connected to the remote server or the desktop?

---

### Post by gorellana09 on 2015-02-18
It was a folder from my laptop which I had to share via x2go client. I have since unshared it though as you can see from the picture below.
[ATTACH=CONFIG]260074[/ATTACH]

Although when I use windows to connect to the server x2go creates a similar mount for that session however the thunar delay and lock problem is not present there.

---

### Post by TheFu on 2015-02-18
Sorry I'm so clueless. Where is the problem storage connected, exactly?  Is it mounted on the client or server before you startup x2go?

---

### Post by gorellana09 on 2015-02-18
It's mounted on the server once I connect to it with x2go. When I suspend my session it gives an error saying fuser was unable to unmount...gives the long string name posted above...device was busy.

---

### Post by TheFu on 2015-02-18
> **gorellana09 said:**
> It's mounted on the server once I connect to it with x2go. When I suspend my session it gives an error saying fuser was unable to unmount...gives the long string name posted above...device was busy.

Is the problem storage physically connected to the client or is the problem storage physically connected to the server? See the difference?

Just trying to understand where it is physically plugged in and whether it is mounted BEFORE you run x2go and connect to the server. Sorry if that hasn't been clear.

---

### Post by gorellana09 on 2015-02-18
It is physically connect to the client (my laptop) yes.

---

### Post by TheFu on 2015-02-19
So I attempted to do the same thing here with a USB flash disk physically connected to a Win7 laptop running x2go as a client.  The flash drive has portable apps on it for Windows.  It had to be mounted under Windows before it would show up in the x2go settings to be "shared."  The mount looks like this:
```
thefu@127.0.0.1:/cygdrive/I/                 962M  701M  261M  73% /tmp/.x2go-thefu/media/disk/_cygdrive_I_
```

The flash drive is formatted as NTFS, not fat32 or xfat. If that matters, i dunno.

From the remote server machine:
```
/tmp/.x2go-thefu/media/disk/_cygdrive_I_/PA$ ls
Autorun.inf*  Documents/  PortableApps/  Start.exe*
```

It will take a few more minutes to test this from a Linux machine.  Look for an update ... have to physically move to another box.

-----[update]--------
Moved to an Ubuntu 14.04 box. Used gvfs to mount the flash drive locally - actually used pcmanfm.  Started x2goclient, added the "share" + automount and saw it was there.  On the client side, I forced an eject - saw an error that bash was still keeping it mounted, confirmed. Everything seems to be working as expected here.

Tried again - used thunar ... it gvfs'd the storage, mounted it local and remote automatically.  Didn't see any errors.  Physically pulled the flash drive out on the client machine. On the remote side, the storage was removed.

My client on Linux is *X2Go Client V. 4.0.1.1 (Qt - 4.8.6)*

So it appears that I haven't been able to reproduce the issue you are seeing here. Let me re-read the OP.
So looking at the OP again ... that mount is for sharing a local printer. I don't think it is for general storage.** If you aren't using local printing support, there's a checkbox in the session settings to uncheck. ** Perhaps that will work?

Just found the /etc/x2go/x2goserver.conf file - at the bottom, there's a way to turn up the log levels - info/debug might shed some more light.

Did this solve it? If so, please mark the thread as solved.

---

