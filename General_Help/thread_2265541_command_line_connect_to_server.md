---
title: "command line connect to server"
date: 2015-02-16
forum: General Help
---

### Post by dieter-erich on 2015-02-16
Hi, 
   how can I connect via command line to a server and where are the parameters stored?

In gnome I usually go to 'Places' > 'Connect to server' where I have to enter a line like: "smb://share;name@x.y.z/xyz/uvw/etc". I did set a bookmark and so it works just by clicking on it 

BUT: where is this line stored and how could I simply copy it from one PC to another? It is difficult to remember this text when it is long and only displayed when mousing over the button. I have not found a way to copy it....

Thanks, D-E

---

### Post by TheFu on 2015-02-16
Accessing files is one thing. Having a remote shell is another. There are many different ways to connect.
* nfs
* cifs
* ssh (sftp/scp/sshfs)
are the most popular.
Most GUI tools appear to use gvfs for file connections. I don't know how that is stored - think they use a library directly - no CLI command used.  The ways to connect to cifs or nfs shares are a few.  NFS is faster and provides full file permissions/owner/groups. cifs handles poor networks better - especially wifi.  A few different ways to mount remote storage, if that is really all you want.
* Manually run a **mount** command.  sudo mount -t cifs source-device mount-point / or with nfs as the "type"
* Alter the /etc/fstab to mount it
* Use autofs ... 
Just remember that if you manually mount storage, you need to umount it later - that is important for laptops. Shutting down a system will close these mounts. Picking up the laptop and leaving the network will not.  cifs and nfs mounts shouldn't be used over an internet connection. They are not secure enough without a VPN.  Using sshfs or sftp or scp can overcome this lack of security - providing secure, remote, file access. There are many different sftp or scp clients. I tend to just use a terminal.  It is possible to script this stuff ... **thunar sftp://userid@server/**. If the userid on both systems is the same, it doesn't need to be in the connection line. If ssh-keys have been shared between the 2 systems, the connection will "just happen".

Of course, the remote system needs to allow whatever sort of file sharing or run an openssh-server process.

ssh is amazingly flexible and generally considered secure when used with keys (not passwords). With keys, it is also extremely convenient - connections "just work."

Of course, you can leave the files on the other system and just ssh into to access/modify/work-on those files too. This is how Linux / Unix administrators around the world do their jobs on servers from 1-20,000 miles away.  Open a terminal and run **ssh userid@remote-server-name**.  Poof - you're on the other machine inside a terminal that is just like being on the local machine - with an encrypted connection.

If you want to know a few other ways to run remote applications: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

---

### Post by Morbius1 on 2015-02-16
> I did set a bookmark and so it works just by clicking on it 

BUT: where is this line stored and how could I simply copy it from one PC to another?
```
/home/dieter-erich/.config/gtk-3.0/bookmarks
```

---

### Post by dieter-erich on 2015-02-16
Thanks for the long and the short explanation! The short one solved my question immediately

---

### Post by TheFu on 2015-02-17
> **dieter-erich said:**
> Thanks for the long and the short explanation! The short one solved my question immediately

That's the important part.
Plus realizing there are multiple ways to solve most things in Linux.

---

