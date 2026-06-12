---
title: "Mounting a USB drive to a folder on another drive."
date: 2019-11-10
forum: General Help
---

### Post by iconoclast12 on 2019-11-10
Is it possible for me to mount a USB drive, such as a flash drive or external hdd, to a folder in my main storage (where the OS is) inside /home/username and then mount the usb drive to a folder there and use the storage space of my external drive and not the storage that the OS is installed to, by putting files in a folder there? Am I assuming this right? I have not experimented with this.. Can I do this? How do I go about doing this?

---

### Post by oldrocker99 on 2019-11-10
When installing, you could mount an external drive as /home, but it almost certainly will be slower than an internal drive.

It can be done otherwise, but, seriously, I'd reinstall myself. 

Also, bear in mind that your /home folder can **never, ever** be too big.

---

### Post by iconoclast12 on 2019-11-10
Okay, but if I mount my external drive to a folder on my internal drive, and I put files in the folder I mount it to, those files will take up space on the external drive and not the internal storage, correct?

---

### Post by CatKiller on 2019-11-10
> **iconoclast12 said:**
> Okay, but if I mount my external drive to a folder on my internal drive, and I put files in the folder I mount it to, those files will take up space on the external drive and not the internal storage, correct?

Some better nomenclature might help sort out your confusion.

There isn't such a thing as mounting to your internal drive: there are locations in the filesystem tree. The filesystem tree starts at / (which is why that location is sometimes confusingly called the root directory) and branches out from there, to /home, or /var, or /usr, and so on.

You likely have a partition mounted at /. Many people would also have a partition mounted at /home. If you have specific needs, you could mount partitions at /var or other places. You could mount one partition as /var and a completely different partition as /var/log. The benefit is that you can use different filesystem formats for each of these partitions: one might be best suited for teeny-tiny files, another might be best suited for fast access, another yet might be an NFS share from some other machine entirely. There are also locations in the filesystem tree, such as /sys or /proc, that are completely pretend: there are no actual files there, and they take up no space; those locations are just there so that you can do normal file-access things to, for example, read the voltage of your CPU. For my machine, as another example, writes to /var/log go to tmpfs, so they're never actually written anywhere: they're just thrown away whenever the machine is shut down or needs the RAM.

To answer your question; if you mount a partition to somewhere in your filesystem tree then writes to that location will not take up space anywhere else in the filesystem tree. If you have a partition mounted at /home, for example, writing there would take up no space on the partition that's mounted at /.

---

### Post by iconoclast12 on 2019-11-10
I see, well that does clear up a lot of confusion. What I'm trying to do, is I have a folder with emulators and roms on it, located in /home, and I wanted to mount an external drive to that folder so I can use its storage instead, because the partition that I have Lubuntu installed on (the internal storage) is almost empty and I can't fit any files on it.

---

### Post by Dennis N on 2019-11-10
> I wanted to mount an external drive to that folder so I can use its storage instead...
It's a reasonable thing to do. When I realized I didn't have space on my root partition for my music files, I put all of them them on a new separate partition, and just mounted it to my root partition on startup in /etc/fstab. This arrangement also allows me to share them with any additional OS I have installed.

---

### Post by CatKiller on 2019-11-11
The only thing to be aware of is that, because you're mounting a new partition to that location in the filesystem tree, anything that was on a *different* partition at that location will no longer be available. So if you had one partition mounted at /, and that partition had a directory called /home with a bunch of stuff in, then mounting a partition to /home will mean that all reads and writes will go to that new partition instead. All the stuff that was there before is covered up by that newly mounted partition. Unmount the partition and, hey presto, the directory is visible again.

For that reason it's common practice to mount your new partition to a temporary location first, so that you can move whatever's already at the desired mount point to the new partition, and then remount your new partition to its proper mount point.

---

