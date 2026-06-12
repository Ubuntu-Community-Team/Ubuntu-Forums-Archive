---
title: "NFS issues"
date: 2017-07-14
forum: General Help
---

### Post by asai on 2017-07-14
Hi,

I have some issues with NFS...
Installed 2 servers - One 12.04 LTS (server1) and one 16.04 LTS (server2).

The idea is to gradually move over from the old server1 to server2.
Therefor I have set up /etc/exports like this on server1:
```

/mediadisk  192.168.1.0/24(ro,async,fsid=0)
/home	  192.168.1.0/24(rw,async,fsid=0)
/datadisk	 192.168.1.0/24(ro,async,fsid=0)
/data	 192.168.1.0/24(ro,async,fsid=0)

```

In /etc/fstab on server2:
```

192.168.1.4:/   /home   nfs4    auto  0  0
192.168.1.4:/   /mediadisk   nfs4    auto  0  0
192.168.1.4:/   /datadisk   nfs4    auto  0  0
192.168.1.4:/   /data   nfs4    auto  0  0

```

But it is only mediadisk that is mapped to all the directories.
In older versions of NFS i was used to write the lines in fstab like this:
```

192.168.1.4:/home   /home   nfs4    auto  0  0
192.168.1.4:/mediadisk   /mediadisk   nfs4    auto  0  0
192.168.1.4:/datadisk   /datadisk   nfs4    auto  0  0
192.168.1.4:/data   /data   nfs4    auto  0  0

```
This makes sense.
However I get this error when doing mount -a:
```

mount.nfs4: mounting 192.168.1.4:/home failed, reason given by server: No such file or directory
mount.nfs4: mounting 192.168.1.4:/mediadisk failed, reason given by server: No such file or directory
mount.nfs4: mounting 192.168.1.4:/datadisk failed, reason given by server: No such file or directory
mount.nfs4: mounting 192.168.1.4:/data failed, reason given by server: No such file or directory

```

How can I do this the way I want?

---

### Post by yancek on 2017-07-14
The fstab file you show on server 2 has mount points in the / (root) of your filesystem for:  /home, /mediadisk, datadisk and data.  Do those directory mount points exitst?  Exporting /home from one computer to the /home directory of the current system is going to be problematic at best.  It would make more sense to create those mount points under the /mnt directory.  Also, it shows that you are trying to mount the entire root filesystem of the other computer to each of the mount points.  Something like below should work based on your exports file:

> 192.168.1.4:/home   /mnt/home   nfs4    auto  0  0
192.168.1.4:/mediadisk   /mnt/mediadisk   nfs4    auto  0  0
192.168.1.4:/datadisk   /mnt/datadisk   nfs4    auto  0  0
192.168.1.4:/data   /mnt/data   nfs4    auto  0  0

---

### Post by SeijiSensei on 2017-07-14
I believe you can only have one file system with fsid=0.  From "man exports"
> For  NFSv4, there is a distinguished filesystem which is the root of all exported filesystem.  This is specified with fsid=root or fsid=0 both of which mean exactly the same thing.

Other  filesystems can be identified with a small integer, or a UUID  which should contain 32 hex digits and arbitrary punctuation.

Try giving each filesystem a different fsid, like fsid=1 for the mediadisk export.  I think that worked for me when I tried NFSv4.  I'm still using v3 for my home/office network.

---

### Post by asai on 2017-07-14
> **yancek said:**
> The fstab file you show on server 2 has mount points in the / (root) of your filesystem for:  /home, /mediadisk, datadisk and data.  Do those directory mount points exitst?  Exporting /home from one computer to the /home directory of the current system is going to be problematic at best.  It would make more sense to create those mount points under the /mnt directory.  Also, it shows that you are trying to mount the entire root filesystem of the other computer to each of the mount points.  Something like below should work based on your exports file:

Like I said in my post, I have already tried this. This is the way I am used to do it.

---

### Post by asai on 2017-07-14
> **SeijiSensei said:**
> I believe you can only have one file system with fsid=0.  From "man exports"


Try giving each filesystem a different fsid, like fsid=1 for the mediadisk export.  I think that worked for me when I tried NFSv4.  I'm still using v3 for my home/office network.

Tried this, but it doesn't seem to work. :(
How can I still use v3? It is v3 on server1, but v4 on the new server.
I would like it to work the same way I am used to. :)

Edit:
Tried this:
Exports
```

/home	192.168.1.0/24(rw,async,fsid=0,no_subtree_check)
/mediadisk	192.168.1.0/24(rw,async,fsid=1,no_subtree_check)

```
fstab
```

192.168.1.4:/home   /home   nfs  vers=3  auto  0  0
192.168.1.4:/mediadisk   /mediadisk   nfs  vers=3  auto  0  0

```
The error is now:
```

mount.nfs: Protocol not supported
mount.nfs: Protocol not supported

```

---

### Post by asai on 2017-07-15
I don't understand this.
I had a new look at the documentation here:
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

It is exactly the way I set it up i the first place. I can't see the problem.
Anyone have an idea?

---

### Post by asai on 2017-07-15
Gave up...
Installed 12.04 LTS server instead.
Works perfect now. :p

---

### Post by oldos2er on 2017-07-15
12.04 is no longer supported and no longer receives any updates, including security updates.

---

### Post by asai on 2017-07-17
Yes I know, and I will upgrade my server soon. I possibly wait for the next LTS. 18.04?
I have been very satisfied with my 12.04 server. Installed the system on my current server summer 2012. Have been running without any problems ever since. Therefor I am a bit careful with the upgrade. :)

---

