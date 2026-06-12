---
title: "Problem with mount"
date: 2008-04-03
forum: General Help
---

### Post by mzar on 2008-04-03
HI all,

I using feisty as my primary os. Now i have problem with mount. I have two hdd sata, 160gb seagate and 320 gb hitachi.

My problem is each time i boot my box, i have to mount manually my hitachi hdd. When it booted before entering window, it show unknown 'ntfs-3g' fail. I have to do mount manual.
How to fix this kind of error?

---

### Post by ryanhaigh on 2008-04-04
It is possible that your hard drive was not unmounted cleanly or there are errors on the drive. In this case ntfs-3g will not want to mount the drive, to solve this issue you can simply reboot into windows and run checkdisk on the drive, then boot back into ubuntu, there are ways to make ntfs-3g ignore the errors as well by adding the force option in /etc/fstab as discussed here: [http://ubuntuforums.org/archive/index.php/t-484566.html](http://ubuntuforums.org/archive/index.php/t-484566.html)

---

### Post by mzar on 2008-04-05
> **ryanhaigh said:**
> It is possible that your hard drive was not unmounted cleanly or there are errors on the drive. In this case ntfs-3g will not want to mount the drive, to solve this issue you can simply reboot into windows and run checkdisk on the drive, then boot back into ubuntu, there are ways to make ntfs-3g ignore the errors as well by adding the force option in /etc/fstab as discussed here: [http://ubuntuforums.org/archive/index.php/t-484566.html](http://ubuntuforums.org/archive/index.php/t-484566.html)

I use only ubuntu. No other os..

---

### Post by ryanhaigh on 2008-04-05
Well in that case you will have to use the force option although if you have no intentions of going back to windows you might want to consider changing to a native linux filesystem such as ext3 for all your partitions at some point. Running ntfs is not only pointless if your not using windows but actually slows down file access as ntfs-3g is a userspace driver. Check your cpu usage during a ntfs file transfer to see what I am talking about here.

---

### Post by vanadium on 2008-04-05
I suggest to try the "ntfsfix" command to check the ntfs drive. THis will probably manage to allow the disk to mount automatically again. However, I second ryanhaigh's suggestion: if you are not anymore using Windows, you should strongly considering to reformat the drive to a native linux file system such as ext3.

---

