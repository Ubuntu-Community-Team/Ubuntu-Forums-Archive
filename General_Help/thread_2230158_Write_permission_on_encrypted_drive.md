---
title: "Write permission on encrypted drive"
date: 2014-06-17
forum: General Help
---

### Post by 0pt1cKill3r on 2014-06-17
I have been having problems with my windows OS and tried to back up my files to my 2nd HDD using ubuntu. The problem was that this HDD was encrypted with Bitlocker. I managed to mount it successfully using dislocker but now it doesnt let me copy files. I think i have write permissions but dont know what is going wrong. Please tell me what information you need to help me. (take it easy on me cause im a begginer on ubuntu)

Output from *parted -l *for the hdd (sdb1- is the drive im trying to write on) :

```
Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  448GB  448GB   primary               boot
 2      448GB   448GB  512MB   primary
 3      448GB   451GB  2574MB  primary  ext3


```

---

