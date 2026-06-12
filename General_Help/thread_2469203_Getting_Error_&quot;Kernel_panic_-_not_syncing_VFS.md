---
title: "Getting Error &quot;Kernel panic - not syncing: VFS: Unable to mount root fs google cloud&quot;"
date: 2021-11-23
forum: General Help
---

### Post by aruneshdutta on 2021-11-23
Hello all

I am running Ubutnu in one of instance in Google Cloud, while performing upgrades it had frozen for long time and then later when I tried to connect as usual using SSH the connection couldn't be established and in the serial console also I am getting an error "Kernel panic - not syncing: VFS: Unable to mount root fs ", kindly guide what steps should I follow to rescue the instance running in Google Cloud and make it running fine again, have the storage drive earlier used with instance also intact and comfortably attached to instance

Here is the attached image of error 

[IMG]https://i.ibb.co/PhTkYW4/Untitled.png[/IMG]
[IMG]https://ibb.co/gTvY7Ww[/IMG]

---

### Post by LokiScarlet on 2021-11-24
This isn't much information. For "Unable to mount root fs", there's usually a few lines of information that show up before. For example, if the storage is failing or the VM botched it, you might get something like:
> VFS: Cannot open root device "vda" or unknown-block(0,0)
Or if grub is incorrectly configured and isn't pointing to a disk that exists anymore, you might get:
> Please append a correct "root=" boot option; here are the available partitions
In the former case, you'd want to restore from a backup if you have one. In the latter case, you'd want to edit Grub if you can.

---

### Post by aruneshdutta on 2021-11-24
have updated the main post sharing again the error output here of serial console[IMG]https://i.ibb.co/PhTkYW4/Untitled.png[/IMG]

---

