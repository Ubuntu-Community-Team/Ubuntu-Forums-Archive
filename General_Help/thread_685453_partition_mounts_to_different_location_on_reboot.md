---
title: "partition mounts to different location on reboot"
date: 2008-02-02
forum: General Help
---

### Post by jledhead on 2008-02-02
I am using Gutsy

as the subject says, I have 2 partitions mounted to 2 locations, sometimes when I reboot they reverse them selves and mount to the wrong mount point.  the partitions are on seperate physical drives.  I think I know what the problem is but I don't know how to solve it.  My main drive is a sata drive with a / partition and another data partition, I have a ide raid controller that I use only because I don't have any ide connections on this mobo.  So I have noticed that not only do the partitions change but the dev labels actually change after a reboot and sda1 becomes sdb1.  

I am assuming its because of the funky raid card but I want to continue to use it, so is there a way to change the way or order that device gets detected so it doesn't mess with my current drive?

Unless someone has another idea for what the problem might be.

---

### Post by fjgaude on 2008-02-02
Well, half the problem is with Linux; Ubuntu has an issue with re-naming drives after reboots. Likely this may be fixed in Hardy 8.04.

You way I live with this is to use UUIDs for the drives instead of their /dev names in the /etc/fstab file.

You get the UUID for a device with vol_id /dev/sd[nn] used at the command line:

```
sudo vol_id /dev/sda1
```

You may need to install that little program, vol_id, using Synaptic. I can't remember if it is there by default.

Then use that UUID string instead of the /dev/sda1 in fstab:

```
#dev/sda1
UUID=4863b139-cec4-4956-83e3-c33935b7ddb1 /media/sda1    ext3    defaults   0    0
```

Of course, use your UUID and mount point.

Let us know how you do.

---

### Post by jledhead on 2008-02-04
this worked for me, many thanks.

And vol_id was installed already.

---

### Post by heatblazer on 2008-02-04
I`ve encountered such a problem 1 year ago on LTS 6.06. I remember that it was fixed in 7.04...

---

### Post by ~LoKe on 2008-02-04
> **heatblazer said:**
> I`ve encountered such a problem 1 year ago on LTS 6.06. I remember that it was fixed in 7.04...

Nope.  If memory serves, 6.06 -> 6.10/7.04 was the change from hdc to sda, or something.

---

### Post by dcstar on 2008-02-04
> **jledhead said:**
> I am using Gutsy

as the subject says, I have 2 partitions mounted to 2 locations, sometimes when I reboot they reverse them selves and mount to the wrong mount point.  the partitions are on seperate physical drives.  I think I know what the problem is but I don't know how to solve it.  My main drive is a sata drive with a / partition and another data partition, I have a ide raid controller that I use only because I don't have any ide connections on this mobo.  So I have noticed that not only do the partitions change but the dev labels actually change after a reboot and sda1 becomes sdb1.  
........

You can get around the issue with the UUIDs, or you can label the partitions and then they always will be mounted using the label names.

Partition labelling is very handy for external USB drives and other devices that can be assigned available /dev/sdx designations.

---

### Post by fjgaude on 2008-02-04
David, I've never used labels. Could you tell us how you label a partition? Thanks!

---

### Post by fjgaude on 2008-02-05
Never mind, found two ways!

**e2label** and **tune2fs -L**

Easy, now to find out if this is better than using UUIDs.

---

