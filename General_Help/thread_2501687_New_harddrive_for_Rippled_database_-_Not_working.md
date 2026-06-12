---
title: "New harddrive for Rippled database - Not working"
date: 2024-10-17
forum: General Help
---

### Post by doe-1992 on 2024-10-17
I have installed "Rippled" on my server (Ubuntu 24.04) on the main drive "/". With the original settings, Rippled runs fine.

Now I want the Rippled database running on another drive. Rippled config file "rippled.cfg" provides the following method to do excactly that:

```
**[node_db]**
type=RocksDB
path=/media/nodes/ripple/db/nudb

**[database_path]**
/media/nodes/ripple/db
```

But when I restart the Rippled service:

```
sudo systemctl daemon-reload
sudo systemctl restart rippled.service
sudo systemctl status rippled.service
```

I get this error:

```
[...] systemd[1]: Started rippled.service - Ripple Daemon.
[...] rippled[16375]: terminate called after throwing an instance of 'std::runtime_error'
[...] rippled[16375]:   what():  Can not create "/media/nodes/ripple/db"
```

I have created all the necessary directories and changed their ownership. The 600GB SAS drive has a speed of 10K RPM, but I keep encountering this error. Somehow, Rippled does not have access to the drive.

PS: I am an absolute beginner to Ubuntu and Rippled.

...help...

---

### Post by TheFu on 2024-10-17
Please show the /etc/fstab line that mounts the new storage.  Placing system mounted storage under /media/ isn't the best idea, BTW.

---

### Post by doe-1992 on 2024-10-18
**Thank you! **This was driving me mad for two days. The drive was not in the file at all. I added it (with the help of ChatGPT), and I've changed /media/ to /mnt/. RIPPLED is running now and storing the blockchain on the new second drive :)

Again, thanks for the correct solution :)

---

