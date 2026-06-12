---
title: "RSync wants to copy everything"
date: 2007-11-06
forum: General Help
---

### Post by hinge on 2007-11-06
I sync my music files from my file server to an external HD and to an xbox (running xdsl) - I use rsync for this.

My problem is that when I want to do the sync - rsync wants to copy all my music files - not only the ones that have changed or new ones. I have approx 40 gb so this is time consuming.

This is what I do when I sync between the fileserver and the xbox.
on the xbox the rsync.cfg reads:

```
cat /etc/rsyncd.conf
[media]
        comment = ftp area
        path = /mnt/hda55
        read only = no
        list = yes
        gid = root
        uid = root

```

I start the rsync daemon:

```
rsync --daemon
```

On the filederver I execute:

```
rsync -avn --size-only /media/store/audio/music 192.168.2.5::media/Music/MP3
```

As you see I run it in dryrun mode, to check if it works - it doesn't it gives me a complete list of all files, though 99% of them are the same..

What am I missing ?

---

