---
title: "Configure hardware RAID array so it doesn't appear as a removable device"
date: 2020-11-09
forum: General Help
---

### Post by David_Partridge on 2020-11-09
LUbuntu 20.04.1

I've got a hardware RAID array that is shown by the Removable Media/Device Manager tool in the taskbar as being removable!

It is so not removable ... and I definitely wouldn't want to eject it!

How do I configure things to it doesn't appear as a removable device.

Thanks
David

---

### Post by SeijiSensei on 2020-11-09
Mount it permanently via an entry in /etc/fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

