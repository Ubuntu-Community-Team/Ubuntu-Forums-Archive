---
title: "Setting parameters for CF card"
date: 2012-11-29
forum: General Help
---

### Post by zoocat59 on 2012-11-29
I'm in deep with FDISK, CFDISK, GPARTED. I have a 1G CF card that I'm trying to partition. What is needed is Cyl=1986, Hds=16, Sec=63, Type=Dos, and bootable. So far I've gotten all these right. What's hanging me up is the starting and landing zones I need to specify. In HEX format. Head start = 0x01 and End at 0x1F Also a Sector/Cylinder Start at 0x0001 and End at 0xE0FF. Starting Sector should equal 0x3F. I'm finding I don't have the total control using  FDISK, CFDISK, or GPARTED. Can anybody point me in the right direction?
Thanks in advance, zoocat59

---

