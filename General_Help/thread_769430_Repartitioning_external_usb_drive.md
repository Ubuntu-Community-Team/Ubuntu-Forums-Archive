---
title: "Repartitioning external usb drive"
date: 2008-04-26
forum: General Help
---

### Post by RetiredInMaine on 2008-04-26
I have an external usb drive that has three partitions. It came fron an old window machine. I can mount and unmount the 2 non boot partitions fine. However I want to repartition them into a single non boot partition for use with my linux system but do not know how to mount the physical drive. sudo fdisk -l shows the entire (physical) drive as /dev/sdc and then shows the 3 partions as sdc1, sdc2, and sdc5. When I try to mount sdc I get a message that says "mount: can't find /dev/sdc in /etc/fstab or /etc/mtab" 

I assume I'm missing something but have no idea what it is.

Thanks in advance for any help.

---

### Post by ryanhaigh on 2008-04-27
You can't mount the device as it is not a partition, if I understand correctly you want to combine the three partitions into one. You can do this by deleting the partitions and then recreating them using gparted, however this will delete all data so you will need to backup everything first.

You could also move everthing to the first partion, delete the others and resize the first to fill the whole disk. Or you could do this incrementally, copying the data from 2nd to 1st then deleting 2nd and resizin 1st to use the free space, then do the same with 3rd.

Of course when messing with partitions its very easy to lose data if you make a mistake and very difficult to recover once you have made it. Show due care.

---

### Post by RetiredInMaine on 2008-04-27
Thank you ryan. Worked just like you said. I used parted to delete all three partitions and create a new single partition, then did a mkfs on it, and when I rebooted it showed up automatically.

---

