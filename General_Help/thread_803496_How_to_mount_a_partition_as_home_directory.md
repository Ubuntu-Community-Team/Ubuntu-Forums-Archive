---
title: "How to mount a partition as home directory?"
date: 2008-05-22
forum: General Help
---

### Post by Iteria on 2008-05-22
I ended up having to install Ubuntu again. everything works as expected, except I make a typo when I was setting up the partitions. I set my main 100gig partition to mount to "/Home" instead of "/home" the result is that my home directory is sharing space with my 10gig root partition. 

I don't know much about mounting, but I was wondering if there was a way to change my home directory to that partition without a reinstall?

---

### Post by sisco311 on 2008-05-22
edit the fstab:
```
gksu gedit /etc/fstab
```Change the mount point of the partition from /Home to /home.
Remount the partition.
```
sudo umount /Home
sudo mount -a
```

If you need to move your home folder from the root partition, then Press Ctrl+Alt+F1 log in and:
```
sudo mv /home/* /Home
```
and use nano to edit the fstab:
```
sudo nano /etc/fstab
```
(Crtl+o Enter to save, Ctrl+x to exit)

---

### Post by Irony on 2008-05-22
Here's an example of what your fstab file would look like;

```
/dev/hda2 none swap sw 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 1 2
```

In this case root is hda3 but home is hda5. You can simply rename Home as home.

Note once you've done this /home will still contain data in hda3 but you won't see it because you are now linking straight to hda5 - you can delete this data as it simply takes up space - you can delete it by booting up to the live CD and mounting hda3 and navigating to /home and deleting its contents.

I'm assuming you already have /home properly set up in your 100 gig partition and root in the 10 gig partition just that you've linked incorrectly.

---

