---
title: "Mounting a partition twice, in two places"
date: 2007-06-25
forum: General Help
---

### Post by steve.horsley on 2007-06-25
I discovered by mistake that you can mount a partition twice, in two separate places at the same time. 

I have never found how to tar the root partition without tar also wandering off into the /home partition and archiving all of that too.

It occurs to me that putting these two facts together, I might be able to mount the root partition on say /mnt/root and then tar up this directory as a backup of a running system. I did it, I've got a nice tar file, and everything looked right as tar was running, but does anyone know if this is a good idea or not?

Steve

---

### Post by mbeierl on 2007-06-25
I generally think it won't work.  You can't reliably back up files that are changing.  Typically, though, your OS doesn't change all that much.  Why not just have reliable backups for your data and only periodically backup your OS with something like partimage?

---

### Post by HermanAB on 2007-06-25
Hmm, no, it would be better to read up a bit on tar.  It is an immensely powerful program.  What you are looking for is the '--exclude=/home' parameter.

Cheers,

Herman

---

### Post by steve.horsley on 2007-06-26
mbeierl:
Yes, shutting down and backing up the system from a live CD or another OS on the disk is what I normally do. But I wondered if this might be a way to avoid the shutdown. I'm sure most data centre servers don't shut down for backups - I've never heard of such a thing.

HermanAB:
--exclude=/home means the /home directory/mount point won't be created on restore, doesn't it?
Can you do --exclude=/home/* and --exclude=/media/* etc?

---

