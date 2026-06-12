---
title: "Keys: continue to wait etc on boot problem"
date: 2014-05-29
forum: General Help
---

### Post by su:bhatta on 2014-05-29
I have read about this in posts dating back to 2010 and hence I am putting up a new thread.
Getting the 'Keys: Continue to wait, press S to skip or M for manual ' on every boot.

Details :
```
sudo blkid -c /dev/null
[sudo] password for tres-bhatta: 
/dev/sda1: LABEL="ate" UUID="10E08476E08463B6" TYPE="ntfs" 
/dev/sda5: LABEL="whatknot" UUID="01CE8A05F5DACD70" TYPE="ntfs" 
/dev/sda6: LABEL="studio" UUID="7c9dc3d1-e768-4eda-82a9-48cd9dcc5b51" TYPE="ext4" 
/dev/sda7: LABEL="wheezy" UUID="6b440bb5-ff84-4a44-a083-d5600dd5f93b" TYPE="ext4" 
/dev/sda8: UUID="102d94bc-e9cc-4508-8915-04469f6b708b" TYPE="swap" 
/dev/sda9: LABEL="musix" UUID="21fec8b9-4212-42e7-9f33-9143e837efb4" TYPE="ext4" 
```

```
GNU nano 2.2.6                                      File: /etc/fstab                                                                                   

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=7c9dc3d1-e768-4eda-82a9-48cd9dcc5b51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=76c5553c-5640-4ffb-b7e4-c980d8ca329a none            swap    sw              0       0

```

Just changing the fstab file, by uncommenting the swap line and putting the right UUID , and saving it will solve the problem?

---

### Post by netgooroo on 2014-06-04
This is caused because when you installed whatever version you have, you selected to have your home folder encrypted. I experienced this when I installed 12.04 before my current install. 

Far as I know, there's not a work around. I could be mistaken though.

---

### Post by su:bhatta on 2014-06-04
> **netgooroo said:**
> This is caused because when you installed whatever version you have, you selected to have your home folder encrypted. I experienced this when I installed 12.04 before my current install. 

Far as I know, there's not a work around. I could be mistaken though.

Thank you for your reply netgooroo.

I have Ubuntu 14.04 installed. And no, i did not encrypt my home folder.

---

