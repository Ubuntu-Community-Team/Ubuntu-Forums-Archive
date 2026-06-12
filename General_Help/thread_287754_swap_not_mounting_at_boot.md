---
title: "swap not mounting at boot"
date: 2006-10-29
forum: General Help
---

### Post by hambone79 on 2006-10-29
I have a really weird problem since my upgrade to Edgy. For some reason, my swap will not mount when I boot my laptop. I have to manually run mkswap and swapon to use my swap partition, but I would like to have it setup to mount automatically. I also notice that during my upgrade to Edgy some changes were made to my /etc/fstab file. Here is what my fstab file looks like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=fa9396a6-6cb8-4dc6-ae58-aefc1325a397 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=eba85763-97be-4c98-8f92-7398671c918c none swap defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I would really like to get this functional because I use Hibernate on my laptop and it can't hibernate without the swap partition enabled.

---

### Post by martijndenerd on 2006-10-29
Had the same problem, check this [topic]("http://ubuntuforums.org/showthread.php?p=1681908#post1681908"), there is a solution and a bugreport about this.

---

