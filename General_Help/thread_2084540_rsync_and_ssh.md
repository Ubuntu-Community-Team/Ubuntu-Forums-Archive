---
title: "rsync and ssh"
date: 2012-11-15
forum: General Help
---

### Post by ptmuldoon on 2012-11-15
I have an existing headless Ubuntu Server setup with no GUI being used as a nasbox.  I normally access the machine via ssh, but also have webmin installed.

I have recently setup/upgraded to a bigger machine, and am now looking to transfer the ~ 2TB of data off it.  Mostly movies, etc.

The new build is setup with a samba share and has the disk space for the transfer.

On the 'old' machine, I logged in via ssh and mounted the samba share of the new machine.  I than started rysnch with the following command:
```

sudo rsync -azvv /old/server/path/ /tmp/new/server/path/

```

Now my question becomes.  If I close my ssh connection, will the file transfer stop?

---

### Post by dannyboy79 on 2012-11-15
yes it will stop. you should have ran the screen command after you ssh'd in. then you can detach from that "screen" so that the command would still run, then you can close the ssh connection.

---

