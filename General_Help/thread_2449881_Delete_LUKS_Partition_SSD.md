---
title: "Delete LUKS Partition SSD"
date: 2020-09-03
forum: General Help
---

### Post by brenneke on 2020-09-03
I have a portable SSD with a LUKS partition on it. I would now like to use this drive for something else and want to remove the LUKS partition and create just one unencrypted partition. Gparted does not give me the option to delete. How can I do this? (I do have password) Thank you.

---

### Post by CelticWarrior on 2020-09-03
[https://www.thegeekdiary.com/centos-rhel-how-to-delete-luks-encrypted-device/](https://www.thegeekdiary.com/centos-rhel-how-to-delete-luks-encrypted-device/)

It's the same for Ubuntu.

---

### Post by TheFu on 2020-09-03
make sure the file system and luks container are closed.  Then just delete the partition and reformat.
Or used a Try Ubuntu flash-boot-drive and just delete the partition, create a new one and format as desired.

---

### Post by brenneke on 2020-09-03
That is where I went wrong, did not have file system closed. Partition deleted and reformatted - thank you!

---

