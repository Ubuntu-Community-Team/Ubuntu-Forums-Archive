---
title: "/etc/systemd/system shutdown script"
date: 2017-09-26
forum: General Help
---

### Post by datube999 on 2017-09-26
Hi, 

Please forgive me if this is already asked a lot of times, but I can't seem to figure this one out by myself.
I'm not a linux guru, nor a newbie, but any help regarding this issue would be very much appreciated.

I'm trying to run a systemd shutdown script, which should do some `rsync` on a yet already mounted `user.img`.

Note: user.img is mounted (fstab) on /home/user

/etc/systemd/system/setup-overlay.service
```

[Unit]
Description=overlay setup (initialize)
After=local-fs.target

[Service]
Type=oneshot
ExecStart=/usr/local/sbin/overlay-setup.sh

[Install]
RequiredBy=getty.target

```

/usr/local/sbin/overlay-setup.sh
```

HOME=/home/user
mkdir -p ${HOME}.tmp
mount -t tmpfs -o size=128M,mode=750,uid=1000,gid=1000 tmpfs ${HOME}.tmp > /dev/null 2>&1
mkdir -p ${HOME}.tmp/.work
mkdir -p ${HOME}.tmp/.upper
mount -t overlay overlay -o lowerdir=${HOME},upperdir=${HOME}.tmp/.upper,workdir=${HOME}.tmp/.work ${HOME} > /dev/null 2>&1
chown 1000:1000 ${HOME} 

```

The above code/stuff seems to work, because `/home/user.tmp/.upper` is filled up after some work.

But how do one make a systemd shutdown service which could do the following?:

/usr/local/sbin/overlay-store.sh
```

HOME=/home/user
# move overlayfs out of the way  
umount ${HOME}
# now ${HOME}.tmp/.upper contains changes
rsync -av ${HOME}.tmp/.upper/ ${HOME}/
# sync stuff
umount ${HOME}

```

So far i have tried:

/etc/systemd/system/overlay-store.service
```

[Unit]
Description=overlay setup (store)
Before=shutdown.target reboot.target halt.target

[Service]
ExecStart=/bin/true
ExecStop=/usr/local/sbin/overlay-store.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

```

Again, thank you very much for any help/pointers into the right direction.

---

