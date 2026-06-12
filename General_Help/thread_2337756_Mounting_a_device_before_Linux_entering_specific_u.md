---
title: "Mounting a device before Linux entering specific user mode"
date: 2016-09-21
forum: General Help
---

### Post by HiSiskin on 2016-09-21
Let me dispense with the complicated background, but I need a device, which is other partition on other hard drive,  to be mounted before seeing the user mode Unity screen. In other word, I'd like to see some links to the directories on that device NOT disabled at the user boot-up.

Where should I have written the following:

mount -t ext4 /dev/device /media/dirA/dirB

?

TIA

---

### Post by SeijiSensei on 2016-09-21
You need to add an entry for the device in /etc/fstab.  Edit the file with "sudo nano /etc/fstab" then follow the [guide here]("https://help.ubuntu.com/community/Fstab").

---

### Post by oldfred on 2016-09-21
The link by SeijiSensei to fstab is good, but the examples in the fstab instructions are now very old.

Bit newer examples, which I still use.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by HiSiskin on 2016-09-22
Big thanks to SeijiSensei and oldfred.
By adding a most sparse entry in the fstab file, we've got some live symlinks to the device at the user boot-up.
Now our workflow is quite smooth.

Thanks again for your valuable guide.

---

