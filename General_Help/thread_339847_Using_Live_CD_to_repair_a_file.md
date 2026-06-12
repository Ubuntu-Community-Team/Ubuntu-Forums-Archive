---
title: "Using Live CD to repair a file"
date: 2007-01-16
forum: General Help
---

### Post by Mithrilhall on 2007-01-16
I edited "/etc/environment" and now I can't boot into Kubuntu or Console properly.

I've booted off the Live CD but how do I mount my hard drive so I can restore the file to the way it was (I know what needs to come out of the file). ](*,) 


TIA

---

### Post by taurus on 2007-01-16
Assuming your / is on /dev/hda1, open a terminal and do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
sudo cp /etc/environment /mnt/ubuntu/etc/environment
sudo umount /mnt/ubuntu
```
Then reboot.

---

### Post by Mithrilhall on 2007-01-16
Worked like a charm.....thank you.

---

