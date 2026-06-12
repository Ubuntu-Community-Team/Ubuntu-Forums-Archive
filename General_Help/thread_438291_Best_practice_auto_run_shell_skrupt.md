---
title: "Best practice: auto run shell skrupt"
date: 2007-05-09
forum: General Help
---

### Post by xterm on 2007-05-09
I have a shell skript that mounbts a samba share to a folder in my home-folder like this:
```

#!/bin/sh
smbmount //192.168.1.254/xterm /home/fredrik/fileserver/ -o username=xterm, password=mypasswd

```

The script does the job (don't know if this is the best way...?).

Now, I need to auto-run this script so it's avaliable when I have logged in. But I can't run it as root so I can't put it in /etc/rc.local (or can I?). If I run it as root I only get read access to my fileserver share. 

How do I auto-run this as 'me'?

---

### Post by mazirian on 2007-05-09
You want this to be run at login rather than on boot? (Meaning you don't want to add a new entry to /etc/fstab?)  If you want to connect to the server using your script just on login, you may simply save that script somewhere and, assuming your in a gnome environment, add it to "Sessions".  I think you may access the correct dialogue via "Preferences" > "Session"  If that doesn't work, there are other methods of having certain files execute when you log in.

---

### Post by raja on 2007-05-09
The best way to mount a samba share is to add it in the fstab. You can follow [this guide]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html").

---

### Post by lloyd_b on 2007-05-09
> Now, I need to auto-run this script so it's avaliable when I have logged in. But I can't run it as root so I can't put it in /etc/rc.local (or can I?). If I run it as root I only get read access to my fileserver share.

You should be able to do *this* from rc.local:
```
su fredrik -c "smbmount //192.168.1.254/xterm /home/fredrik/fileserver/ -o username=xterm, password=mypasswd"
```
which will switch to the user "fredrik", and then execute the command "smbmount...".

Probably the "best" way to handle this situation is via a "cron" entry.  In a terminal, run "crontab -e", and add the following entry
```
@reboot smbmount //192.168.1.254/xterm /home/fredrik/fileserver/ -o
```
This will cause the "smbmount..." command to be executed (as your user) following each reboot. This way, you don't  have to mess with system configuration files, but still have that mount available whenever you log in.

Lloyd B.

---

### Post by xterm on 2007-05-09
> **raja said:**
> The best way to mount a samba share is to add it in the fstab. You can follow [this guide]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html").

Yeh. I thought so to. But when I added my little string to fstab and rebooted I still end upp with an empty folder in my home-folder. The mount fails. If I look in my system.log I found this (don't know if it is related to my problem):

```

May  9 22:45:49 aurora ntpd_initres[5183]: ntpd returns a permission denied error!
May  9 22:45:49 aurora ntpd_initres[5183]: ntpd returns a permission denied error!
May  9 22:45:51 aurora gconfd (fredrik-5385): Failed to send buffer
May  9 22:46:49 aurora ntpd_initres[5183]: ntpd returns a permission denied error!
May  9 22:46:49 aurora ntpd_initres[5183]: ntpd returns a permission denied error!
May  9 22:47:49 aurora last message repeated 2 times

```

I'll try the rc.local with su fredrik.

---

### Post by xterm on 2007-05-09
thats odd... 

It doesn't work if I do su fredrik -c in rc.local either. But if I run the command in a terminal, logged in as fredrik it workes.

Any Ideas?

---

### Post by lloyd_b on 2007-05-09
> **xterm said:**
> thats odd... 

It doesn't work if I do su fredrik -c in rc.local either. But if I run the command in a terminal, logged in as fredrik it workes.

Any Ideas?

No clue on that.  I'm more used to the older systems where there's an actual root user, so the su -c trick may not work properly on Ubuntu.

Have you tried the crontab suggestion?  That one I'm fairly certain *will* work under Ubuntu.

Lloyd B.

---

### Post by xterm on 2007-05-10
> **lloyd_b said:**
> No clue on that.  I'm more used to the older systems where there's an actual root user, so the su -c trick may not work properly on Ubuntu.

Have you tried the crontab suggestion?  That one I'm fairly certain *will* work under Ubuntu.

Lloyd B.
Yeah. I'm also more used to systems that have an actual root user. Not saying that sudo is not a good solution. 

I havn't tried the cron tab 'thing'. I'll do that when I come home from work. 

Any ideas why fstab fails to mount my sambashare (or mounts it as root, causing it to be read-only when I logg in as fredrik?

---

### Post by mazirian on 2007-05-10
What did you try using in the fstab?  It should be something close to this:

```

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

```

(from the link provided above)

You might try also try using cifs rather than smbfs.  Google will provide you with loads of tutorials on this.

---

### Post by lloyd_b on 2007-05-10
> Any ideas why fstab fails to mount my sambashare (or mounts it as root, causing it to be read-only when I logg in as fredrik?

Could you post the exact entry you're using in fstab?  I don't know about the fail to mount issue, but the "mount as root, read only" sounds like a bad fstab entry.

What type of network do you have?  Could the "fail to mount" be a simple "race condition", where sometimes the network is ready when the system goes to mount the share, and other times it isn't?

Lloyd B.

---

