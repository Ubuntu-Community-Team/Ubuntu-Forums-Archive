---
title: "Trying to install ntfs-3g and I get Fuse &gt;=2.6.0 not found."
date: 2007-12-28
forum: General Help
---

### Post by ksinc on 2007-12-28
Hopefully somebody can help me with this. I am trying to install ntfs-3g- on a 6.06 LTS server and when I run sudo ./configure it tells me that Fuse 2.6.0 was not found. I downloaded Fuse 2.7.2 and when I run ./configure fuse-2.7.2 it tells me that Fuse is already present and I need to use --enable-kernel-module. When I run sudo ./configure --enable-kernel-module it tells me to specify the location of the kernel source using --with-kernel=SRCDIR. I'm not sure where the kernel source files are, can somebody help me out?


Thanks 

Kevin

---

### Post by p_quarles on 2007-12-28
To enable the fuse module, you would use:
```
sudo modprobe fuse
```
To add it to the list of modules that are automatically loaded:
```
sudo sh -c "echo 'fuse' >> /etc/modules"
```
(note: be careful here to use the double arrow signs; using one will *overwrite *your modules file and bork the system).

That said, I don't think this is going to work, because the version of fuse that comes with 6.06 is older than the one specified by the ntfs-3g makefile.

---

### Post by ksinc on 2007-12-28
I appreciate the suggestion but as you suspected, it didn't work. Any thoughts on how I can get Fuse 2.7.2 installed? It still give me an error  when I run ./configure fuse-2.7.2. It tells me that Fuse is already present and I need to use --enable-kernel-module. When I run sudo ./configure --enable-kernel-module it tells me to specify the location of the kernel source using --with-kernel=SRCDIR.

Or should I just consider installing 7.1 server?

Thanks

Kevin

---

### Post by p_quarles on 2007-12-28
I could be wrong, but I think that updating fuse would require you to recompile the entire kernel. There are many how-tos on that subject around here, if you want to give that a go.

Personally, I would just upgrade to 6.10, since that's the first Ubuntu that has ntfs-3g in the repos, and it wouldn't require a complete reinstallation.

---

### Post by ksinc on 2007-12-28
Thanks for the help. I think I'll try 7.1. So far I have just been doing some testing before I do a final install at home so I can blow the system away as often as I need until I get it right and learn what I am doing :)

Kevin

---

