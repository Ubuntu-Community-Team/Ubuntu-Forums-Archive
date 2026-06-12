---
title: "I Deleted bash."
date: 2007-05-16
forum: General Help
---

### Post by jstaack on 2007-05-16
I went to change from dash to bash and instead of ```
rm -f /bin/sh
```  I typed ```
rm -f /bin/bash
```

ok, lets all laugh together. :lolflag: 

How would I get apt or dpkg to force the reinstall of the bash package?

I did some brief searching but nothing worked.  I did learn that I shouldn't do this stuff before my coffee is done.

Thanks!

---

### Post by paper0k on 2007-05-16
Can you try to reinstall the bash package from Synaptic? ;)

---

### Post by total wormage on 2007-05-16
omg, hahaha :D
i would indeed try to get synaptic running and fix your bash

---

### Post by Lucifiel on 2007-05-16
Ouch... whoa! May you get this fixed.

---

### Post by taurus on 2007-05-16
Boot from the LiveCD, mount your /, and copy /bin/bash from the CD back to your harddrive.

_Assuming_ / partition is /dev/sda1, do

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo cp /bin/bash /mnt/ubuntu/bin
```
Reboot and remove the LiveCD from the drive.

---

### Post by jstaack on 2007-05-16
Thank you very much Taurus, that did the trick.  I was trying to avoid the hour and a half drive to be next to the server.  But it's nice out and the server is in the middle of a cornfield so the drive was good.

---

