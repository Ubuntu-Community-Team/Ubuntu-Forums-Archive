---
title: "Upgrade 8.04 Mounting Harddisk Problems"
date: 2008-04-22
forum: General Help
---

### Post by MikeJJ on 2008-04-22
I upgraded to 8.04 beta last night and then had some trouble with my previously working fine, mounted harddisks.
The standard devices have changed names
hda -> sdd
hdb -> sde
hdc -> sdf
Which is kind of confusing. 
Makes me wonder what my DVD drive is called now (was hdd)
Also instead of them being called the mount points name, i have unhelpful names on my desktop, like 250 GB Media, 320 GB Media.

Does anybody know why the actual device names have changed from something which made perfect sense to appending onto the code categorys used by sata ?
And why the harddisks are all named after their size instead of having a name ?

---

### Post by Yellowbelly on 2008-04-25
Same problem. It seems like there should be a way to label it in the fstab but I don't know how.

---

### Post by heatblazer on 2008-04-25
Now that you mention it, I see my 2nd Drive (lately named SDA1) now is 37.7 GB MEDIA... but the separate HDD - 320 GB has not changed it`s name. I remember that before the update I forbid any write permissions using the NTFS configuration tool.

---

### Post by erginemr on 2008-05-01
> **Yellowbelly said:**
> Same problem. It seems like there should be a way to label it in the fstab but I don't know how.

Please refer to:
[http://ubuntuforums.org/showthread.php?t=766167](http://ubuntuforums.org/showthread.php?t=766167)
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

*[Disclaimer: The partition labeling scheme also bothers me in Hardy, but didn't try changing the labels myself, yet. So, use at your own risk...]*

---

