---
title: "LVM with disk failure"
date: 2007-06-04
forum: General Help
---

### Post by ryanc on 2007-06-04
I have a 4 disk lvm where one of the disks has died. The first symptoms were really slow reads with io error messages showing up in the logs. I tried using pvmove to remove all data from that drive but discovered I did not have enough room in the lvm to accommodate the data. At some point the drive stopped responding all together and now when I boot the lvm is deactived because it can not find all drives in the volume group. 

I have a brand new disk that is double the size of the failed disc that I will be putting in the computer. My question is how should I go about doing this? I am not all that familiar with lvm and could use some guidance for each of the two scenarios that may happen:

Option 1) The dead drive allows me to use it just one last time. In this case I assume the best action is to use pvmove to move as much of the data from that drive as possible. Is this correct?

Option 2) The dead drive is 100% dead and I can not recover any data. What do I need to do to remove it from my volume group for good?

Thanks for the help!

---

