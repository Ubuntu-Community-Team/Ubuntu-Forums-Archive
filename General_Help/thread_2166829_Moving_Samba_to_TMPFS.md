---
title: "Moving Samba to TMPFS"
date: 2013-08-11
forum: General Help
---

### Post by rhombuss2 on 2013-08-11
I just setup a Ubuntu 12.04 LTS to act as a file server with Samba shares for the rest of my network.  For the sake of saving energy, I wanted the drives to spin down but apparently Samba writes to browse.dat quite frequently, which prevents the spin-down.  I saw this guide ([http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/](http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/)) which suggests moving certain parts of Samba to a temporary drive on your RAM.

I've created the TMPFS by editing /etc/fstab already by adding this:
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

Can someone elaborate on how to actually move the Samba functions to the TMPFS?  The guide above doesn't seem to apply, as I don't have /etc/init.d/samba

Thanks!

---

### Post by jpflouret on 2013-08-31
/var/run should be a symlink to /run which is a tmpfs mounted file system so /var/run/samba is already not on disk. You could make /var/cache/samba a symlink to a directory in /run as well.

First, stop the samba services:
```

sudo service nmbd stop
sudo service smbd stop

```

Make a directory in /var/run for the samba cache and add a symlink to this folder:
```

sudo mv /var/cache/samba /var/cache/samba.bak
sudo mkdir /var/run/samba-cache
sudo ln -s /var/run/samba-cache /var/cache/samba

```

You would have to create the /var/run/samba-cache directory every time you boot. You can do this by editing /etc/init/smb.conf and adding the red/bold text below to the pre-start script:
```

description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up)
stop on runlevel [!2345]

respawn

pre-start script
        RUN_MODE="daemons"

        [ -r /etc/default/samba ] && . /etc/default/samba

        [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

        install -o root -g root -m 755 -d /var/run/samba
        [COLOR=#ff0000]**install -o root -g root -m 755 -d /var/run/samba-cache**[/COLOR]
end script

exec smbd -F

```

You can start the samba services again with:
```

sudo service smbd start
sudo service nmbd start

```

If everything works fine then you can delete the backup cache folder:
```

rm -rf /var/cache/samba.bak

```

**Note: You do not need to edit /etc/fstab**

Enjoy!

---

### Post by ian38 on 2014-03-22
> **jpflouret said:**
> 
You would have to create the /var/run/samba-cache directory every time you boot. You can do this by editing /etc/init/smb.conf and adding the red/bold text below to the pre-start script:


All fine apart from one error - I'm sure you meant to say by editing /etc/init/smb**d**.conf

---

