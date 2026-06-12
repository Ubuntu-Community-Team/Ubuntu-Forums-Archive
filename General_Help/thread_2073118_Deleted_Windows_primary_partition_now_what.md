---
title: "Deleted Windows primary partition now what?"
date: 2012-10-19
forum: General Help
---

### Post by cdmccreary on 2012-10-19
Ok I HAD a dual boot gateway laptop with windows vista on it.

partitions
primary restore 10gb
primary windows 100gb
logical ext4 ubuntu 40gb
logical swap ubuntu 7gb

I used only ubuntu because windows was probably infected.

Ubuntu needed more space.  So I thought about deleting windows and expanding linux partitions.  I had no hd to backup...read on to see how stupid I am...  :popcorn:

Now I have deleted both windows partitions and grub says "grub rescue"  

I moved the ubuntu partition to the beginning of the drive. made it active and primary. no change and moved it back.

what have I done?
how can I just get my data off?

OR

how can I fix this.

---

### Post by carl4926 on 2012-10-19
Use the ubuntu live cd you used for install and do this:

Once at the desktop,

* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt
(yours will be sda5 or something like that)

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

    *

      When that is done you need to run update-grub to create the configuration file.

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sda

And your done

---

### Post by novafluxx on 2012-10-19
If you had moved the Ubuntu partition to the beginning of the drive where your former Windows partition was you may have not only deleted the windows partition but also overwrote them with the data from the Ubuntu partitions so you may never recover that.

If I understand correctly that is.

---

### Post by cdmccreary on 2012-10-19
Thank you this worked.  I am trying to understand the process for future reference.

Charles


> **carl4926 said:**
> Use the ubuntu live cd you used for install and do this:

Once at the desktop,

* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt
(yours will be sda5 or something like that)

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

    *

      When that is done you need to run update-grub to create the configuration file.

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sda

And your done

---

### Post by carl4926 on 2012-10-19
Well, I assumed you had the original partition table in place. The above basically mounted your original system and  took you to 'chroot', which in layman's terms, just means it was as if you were running your original install. We then re-installed grub.

It's likely though that your partitioning is a bit messy.

If you feel inclined, why not post the result of
```
sudo fdisk -l
```

---

