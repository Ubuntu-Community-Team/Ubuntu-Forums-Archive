---
title: "Mounting Ext 3 partitions"
date: 2007-02-25
forum: General Help
---

### Post by Chake99 on 2007-02-25
I bought a 300 gb IDE hard drive today (and installed it despite the fact my computer is only supposed to carry one hard drive. Anyways its been formatted and I'm trying to use a partition for cross OS use.

I can: sudo mount -t ext3 /dev/hda3 /media/data

but in /media/data I can only find a locked "lost & found" folder and I am unable to put any files there. What do I have to do to make it accessible?

Thanks in advance

---

### Post by Azakus on 2007-02-25
try changing the owner of the files to your username
```
sudo chown Chake99: /media/data
```

---

### Post by AllanP on 2007-03-17
> **Chake99 said:**
> I bought a 300 gb IDE hard drive today (and installed it despite the fact my computer is only supposed to carry one hard drive. Anyways its been formatted and I'm trying to use a partition for cross OS use.

I can: sudo mount -t ext3 /dev/hda3 /media/data

but in /media/data I can only find a locked "lost & found" folder and I am unable to put any files there. What do I have to do to make it accessible?

Thanks in advance

The following worked well for me: Change the hd id to what you want.
sudo fdisk -l (Will show actual disks)

cp /etc/fstab /etc/fstab.bak

sudo gedit /etc/fstab

add to the end of the file:
/dev/hda2   /media/hda2   ext3   defaults   0   1 (whatever disk you want to mount eg hda2, hdb4 etc.)


Save it. Then, create a new mount point and mount it.


Code:

sudo mkdir /media/hda2

sudo mount -a

df -h  

You should see /dev/hda2 mounted to /media/hda2 at the bottom of the output.

Now, if you want to write to /media/hda2, you can change the ownership from root to your login name. Therefore, do the following:

Code:

sudo chown -R allan:allan /media/hda2    (Obviously change allan to your login name)

ls -la /media

---

