---
title: "apt-get not working"
date: 2008-02-11
forum: General Help
---

### Post by rugbert on 2008-02-11
running apt-get update seems to work but then when its gets 23% done I get errors like this

```

Err http://security.ubuntu.com feisty-security/multiverse Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_source_Sources - open (28 No space left on device)

```

and running df -h shows that there is plenty of space:

```

/dev/cciss/c0d0p3     9.2G  400M  8.4G   5% /
varrun                2.0G   52K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
procbususb            2.0G  144K  2.0G   1% /proc/bus/usb
udev                  2.0G  144K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/cciss/c0d0p1     471M   31M  416M   7% /boot
/dev/mapper/vg01-home
                      9.9G  328M  9.1G   4% /home
/dev/mapper/vg01-opt  9.9G  151M  9.2G   2% /opt
/dev/mapper/vg01-tmp  9.9G  231M  9.2G   3% /tmp
/dev/mapper/vg01-usr  9.9G  601M  8.8G   7% /usr
/dev/mapper/vg01-var  9.9G  8.0G  1.5G  85% /var
/dev/sda1             688G  9.8G  643G   2% /backupmnt

```

I mean, the var partition is almost full but theres 1.5 gigs of space left which should be plenty to get the apt-get list right?

If not how can I increase /var's size? I think I need to do that anyway, we've have some issues with this server and my superior said he thinks the problems are partition related.

---

### Post by polmir on 2008-02-11
Type in terminal
```
sudo apt-get clean
```

---

### Post by rugbert on 2008-02-12
That did not work.

---

### Post by apetresc on 2008-02-12
You may have plenty of space, but be out of nodes on the filesystem. What does ```
df -i
``` return?

---

### Post by rugbert on 2008-02-12
I ran that before but must have totally missed the 100% on the partition Im concerned with...

what can I do about that? That folder contains like a trillion cached webfiles for the server so I dont think I can really delete much...

---

### Post by apetresc on 2008-02-12
> **rugbert said:**
> I ran that before but must have totally missed the 100% on the partition Im concerned with...
So I was right? This is the problem?

> what can I do about that? That folder contains like a trillion cached webfiles for the server so I dont think I can really delete much...
I don't think there's much you can do about it except find things to delete. Do those trillion cached files need to still be there?

The inode limit is a limitation of the filesystem you're using, not a configuration you can change.

---

### Post by rugbert on 2008-02-12
Can I increase the partition size? every other partition is hardly used and only like 2% full.

I would try to edit apt-get.conf but it seems its not there.

---

### Post by apetresc on 2008-02-12
> **rugbert said:**
> Can I increase the partition size? every other partition is hardly used and only like 2% full.

I would try to edit apt-get.conf but it seems its not there.
I don't think increasing the size of the partition effects its inode amount. The inode limit is a limit on the *number* of files, not their size.

What filesystem is /var partitioned with? Maybe try switching it to reiserfs, it might have higher inode limits (I'm not sure, though, you should check that).

But is there any reason why you don't want to remove the cached web files?

---

### Post by rugbert on 2008-02-12
I just picked up this web server so I dont know whats what yet.

I cant locate any of the web files and the find command pointed me to the cached directories when searching for an image I know is on the website.

---

