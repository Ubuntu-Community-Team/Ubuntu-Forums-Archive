---
title: "_netdev fstab option being ignored"
date: 2013-04-01
forum: General Help
---

### Post by javiribera on 2013-04-01
Hi all,

I had Debian installed before and the same fstab line worked, so I assume this is an Ubuntu specific issue:

```
javiribera@server:/home/javiribera/server /home/javiribera/server fuse.sshfs 
rw,auto,user,noexec,umask=007,uid=1000,gid=1000,allow_other,follow_symlinks,_netdev 0 0
```

I just mount a remote ssh folder using sshfs package into /home/javiribera/server.

[As far as I'm concerned]("http://linux.die.net/man/8/mount"), _netdev option means that *The filesystem resides on a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system). *

At boot, the folder is not mounted, and I think it is _netdev option's fault because when I type *sudo mount -a* it does mount properly.

Any idea?

---

### Post by Morbius1 on 2013-04-01
I have used it with a samba share and it worked just as you described it --- until one Ubuntu release where it stopped working . 

Not sure what happened but at the time I gave in and created a file at: /etc/network/if-up.d/fstab

With this content:
```
#!/bin/sh
mount -a
```

And made it executable.

Any script you place in if-up.d will only be run after the network is up. It's just automating the workaround you are doing manually.

---

### Post by javiribera on 2013-04-01
mm good to know. I wonder whether it is a bug or why someone decided to remove this feature (_netdev option)

Thanks :D

---

### Post by rkillcrazy on 2013-05-15
> **Morbius1 said:**
> I have used it with a samba share and it worked just as you described it --- until one Ubuntu release where it stopped working . 

Not sure what happened but at the time I gave in and created a file at: /etc/network/if-up.d/fstab

With this content:
```
#!/bin/sh
mount -a
```

And made it executable.

Any script you place in if-up.d will only be run after the network is up. It's just automating the workaround you are doing manually.

A little help on this, please....  I recently ran into this issue on an 12.04.2 server.  FSTAB is set to mount 2 NFS shares and it used to work fine.  A few updates and a reboot changed all that.  I've since created **/etc/network/if-up.d/fstab/mount.sh**, set it so that the owner (root) can execute it (-rwxr--r-- 1 root root 19 May 15 09:45 mount.sh).  The file has your exact code in it but it didn't seem to work.  What step did I miss?

---

### Post by Morbius1 on 2013-05-15
Take a look at the contents of /etc/network/if-up.d

They are all single files with no extensions and no subdirectories. You don't want:
[B]/etc/network/if-up.d/fstab/mount.sh
[/B]
You want:[B]
/etc/network/if-up.d/fstab[/B]

Where **fstab** is the file containing the script not a directory.

---

### Post by rkillcrazy on 2013-05-16
> **Morbius1 said:**
> Take a look at the contents of /etc/network/if-up.d

They are all single files with no extensions and no subdirectories. You don't want:
[B]/etc/network/if-up.d/fstab/mount.sh
[/B]
You want:[B]
/etc/network/if-up.d/fstab[/B]

Where **fstab** is the file containing the script not a directory.

Ahhhhhhhhh, I see.  Okay, I've made the change and set the permissions to mimic the others in that directory.  I'll see how this works on my next reboot during our maintenance window.  Thanks for the clarification.

---

