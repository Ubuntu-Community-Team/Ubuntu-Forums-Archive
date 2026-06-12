---
title: "Compressing a dd image in a way that allows direct mounting"
date: 2016-07-04
forum: General Help
---

### Post by ako673de on 2016-07-04
Hi,

I have written a tool on my NAS, that automatically creates images from all disks in all computers on my LAN. It runs in a cron job and it does really sophisticated things, like clearing swap files and unused space, remounting the filesystems readonly before creating images, afm.

My problem: I want to be able to restore just a few files from these images, and because they can become VERY big it's quite likely that there is not enough space for uncompressing. So what I'm looking for is a solution to access the images without needing to uncompress.

So far I found two possible solutions on the internet:
- Archivemount. But: Works only with tars, often stalls (maybe because of the filesize?), is not natively available on all target systems, and is extremely slow (general problem with seeking in regular archives)
- Squashfs. Perfect for how it works AFTER having created the images, But: File size is 1.5x of a regularly xz-packed archive, and mksquashfs doesn't seem to have an option to write it's output to stdout which makes it much more complicated to bring the output to the NAS: the script first has to establish a mountpoint to the NAS on the source computer - while it's filesystem is mounted Readonly! - and additionally it therefore has to pass credentials over the network.

Any ideas of how it could work better?

best regards
ako673de

---

### Post by sudodus on 2016-07-04
I think all alternatives with huge compressed files will be very slow compared to reading from uncompressed systems. Storage is relatively cheap now (compared to some years ago). If speed and convenience are important, I think you should consider a backup method without compression, at least for the parts of the system (including your personal files) that are most likely to need restoring.

It means that ***dd*** may not be tool for you, but rather a backup tool, for example ***rdiff*** or some tool with a graphical user interface. Maybe a simple shellscript with ***rsync*** will do for you.

---

### Post by ako673de on 2016-07-04
I need to emphasize that my tool is already working perfectly with packed images. With all the sophisticated stuff inside it is currently generating packed images of less than 800MB from a 1TB large filesystem (with Ubuntu and some recordings on it - it is a media server)! The only thing I cannot do with these packed images is extracting single files from them without unpacking to at least some temp storage, and 1TB of temp storage is rare, even on bloated systems...

Speed is of no importance, well, of almost no importance. If it takes days or even weeks then it becomes of at least some importance :-).

---

### Post by ako673de on 2016-07-18
I finally implemented the following "dirty" solution:
- Used sshfs on the target host to establish the mount point to the archive host
    => no need for credentials if ssh-key authentication is setup
- Used /var/lock as temporary mount point
    => I hope, that this folder is available by default on every linux installation
    => I hope, that this folder is not in use and will not be written to while backup is in progress
Correct me if I'm wrong...

---

### Post by sudodus on 2016-07-18
I would suggest that you create a dedicated directory, for example as a subdirectory in **/mnt**, and save your backup in that directory.

/mnt is available in all linux versions and flavours, and its main purpose is to provide mount points for partitions.

I don't know how /var/lock is used, but I think that it is used for writing, storing and checking 'lock' files, that are used to keep programs from overwriting shared files for each other.

---

