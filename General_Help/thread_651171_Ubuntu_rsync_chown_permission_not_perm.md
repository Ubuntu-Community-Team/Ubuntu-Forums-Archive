---
title: "Ubuntu rsync chown permission not perm"
date: 2007-12-27
forum: General Help
---

### Post by Walter_Crankite on 2007-12-27
Dear, 

Following problem

**Mount as**
sudo smbmount //192.168.20.20/NetHDD /mnt/NAS -o username=guest,password=Sucar1


**Command**
rsync -avru --delete /home/ /mnt/NAS/BU_Server_NAS/


**Output**
rsync: chown "/mnt/NAS/BU_Server_NAS/shares/Casius/Aklanten/Studio100/Rotsen/C/Spruce18/.C14B.dxf.4WzdZP" failed: Operation not permitted (1)
rsync: chown "/mnt/NAS/BU_Server_NAS/shares/Casius/Aklanten/Studio100/Rotsen/C/Spruce18/.C15B.dxf.VTuSNl" failed: Operation not permitted (1)
rsync: chown "/mnt/NAS/BU_Server_NAS/shares/Casius/Aklanten/Studio100/Rotsen/C/Spruce18/.C16B.dxf.S3GtJR" failed: Operation not permitted (1)



It is not on all files, only a smart part.
I copy from ubuntu server to a NAS which is mounted on the ubuntu server.
Please help, can't stand this.




BR,
Walter

---

