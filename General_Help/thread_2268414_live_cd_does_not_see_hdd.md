---
title: "live cd does not see hdd"
date: 2015-03-08
forum: General Help
---

### Post by matt18 on 2015-03-08
Ello all. I am having issues installing lubuntu 14.04 on a sata drive. The installer has a red x next to the requirment stating i need y amounts of space. Ok cool so i reboot into live cd and go to term, type fdisk -l

No errors or anything are returned, just take me back to the standard prompt. Haha.

Gparted sees nothing. I have tried mount sda0 commands and term says it cant see any devices with specified name. 

So how do i find my drive?

Thank you

---

### Post by matt18 on 2015-03-08
I made sure mount commands were complete and had all required infi. I just dont know why fdisk doesnt see my drive. So i jave no idea what the lable is so i cant mount it to makesure i have room on it. Thanks

---

### Post by yancek on 2015-03-08
You need to preface the fdisk command with sudo to get necessary privileges:  sudo fdisk -l
You might have a lot of space on the drive but do you have any unallocated space?  That is likely why the red x.

>  I have tried mount sda0 commands and term says it cant see any devices with specified name

The naming conventions with sda, sdb, etc start with the number one (1) not zero.  I'm surprised there is no output from GParted.  How many drives/partitions do you have?

---

### Post by matt18 on 2015-03-08
Oh snap, did not know that sudo was required for fdisk. I knee it was for mount. Yeah i tried numbers 0 to 10 haha and no go. It is just one drive

Thanks

---

