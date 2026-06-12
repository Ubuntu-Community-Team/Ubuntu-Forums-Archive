---
title: "Problems  installing ubuntu."
date: 2016-07-05
forum: General Help
---

### Post by victor-cesar-m on 2016-07-05
Hi, I was installing ubuntu on my desktop computer and the installer crashed. I didn't wrote down the error message but it was something about an error copying some file.

I thought it was a problem with the ISO file, so I downloaded and burned the iso again.Then I rebooted and tried to install Ubuntu again with no succes. I got this error: 

*The creation of swap space in partition #3 of SCSI (0,0,0)(sda)(failed)*

I tried to format the disk with gparted and i got : 

/[I]dev/sda unrecognizeed disk. label.
The driver descriptor says the physical block size is 2048 bytes , but linux says it is 512 bytes.[/I]

I tried zero filling the drive with the ubuntu's Disks utility but it changed nothing.

What should I do?

---

### Post by banceu_sergiu_ione on 2016-07-05
Are you try to install with 'Something else' ?
DO you have any other OS installed or is your disk clean ?

---

### Post by victor-cesar-m on 2016-07-05
The disk is completely clean, I formatted it with the disk utility choosing the slow method (zero filling)

---

### Post by banceu_sergiu_ione on 2016-07-05
And you get that error while install with 'Erase disk and install'  or you try to go with 'Something else' installation. 

Do you get that error also if you chose 'Erase disk and Install' and do not set for a LVM/encrypt?

---

### Post by ajgreeny on 2016-07-05
As the disk is not yet partitioned successfully try using gparted in the live system again, but this time use the Device menu to create a new partition table.  That may solve your problems.

There will be a choice of ms-dos or GPT partition tables available to you to chose from; ms-dos is possibly easiest to deal with if you are new to this but GPT has advantages, particularly as it does not have the four partition limit of ms-dos.

---

### Post by victor-cesar-m on 2016-07-05
I get the error in both installation modes ( 'Erase the disk' and 'Something Else' )
I also tried creating a new msdos partition table and I got the same error when i tried to install ubuntu.

---

### Post by banceu_sergiu_ione on 2016-07-05
Try use GParted and create a GPT partition table. After create a ext4 file system partition. 
After try run Erase disk and Install Ubuntu with out selecting encrypt and LVM.

If not work, could you put the output of ```
sudo parted -l
```
and your pc specs.?

---

