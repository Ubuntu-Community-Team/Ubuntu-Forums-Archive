---
title: "dev / hdxx?"
date: 2007-05-06
forum: General Help
---

### Post by sonicborg on 2007-05-06
Hi all,
    Sorry if this is a basic question, but i am fairly new to linux and having a bit of trouble understading this.

I have 3 harddrives, hda1 hda2 i understand as being my system root, and my swap area.
i then have hdc and hdd. after struggling abit to find out how to partition(cfdisk as type 83) and then mkfs.ext3 on both these drives, when i come to mount them, they are different.

I can only mount hdd as "***mount -t ext3 /dev/hdd1 /directory*** to the directory i want, but on hdc i dont need a number partition. so i just ***mount -t ext3 /dev/hdc /directory*** it wont let me mount hdc1

and i believe this is causing me some problems during boot, where i keep getting some kind of fsck error that halts the boot process until i either entre my root password and do a manual check (which i dont know how to) or just press ctrl+d  and continue booting.

is there a way which i can just make hdd1 just mount as hdd without losing the data on it ?:confused: 

Thanks 

Rob

---

### Post by rai4shu2 on 2007-05-06
You might want to post the contents of your "/etc/fstab" file and the output from "ls -o /dev/disk/by-uuid".

---

### Post by sonicborg on 2007-05-06
okay dokey, here is what i got from that command....

> 
lrwxrwxrwx 1 root  9 2007-05-06 10:30 1e7f90fc-bb53-4a32-a765-2662810b8a54 -> ../../hdc
lrwxrwxrwx 1 root 10 2007-05-06 10:30 2c1dd10d-e7c1-4875-b971-4dd56a4eac51 -> ../../hda5
lrwxrwxrwx 1 root 10 2007-05-06 10:30 90635aa3-4f60-4f31-9e39-823edd17109d -> ../../sda1
lrwxrwxrwx 1 root 10 2007-05-06 10:30 c772fa67-0c47-48a0-b872-f99377f7a17c -> ../../hda1
lrwxrwxrwx 1 root 10 2007-05-06 10:30 f7738475-d4b3-48bb-a1d8-7c2af0d61dbd -> ../../hdd1


I think i might have stopped the error's at startup now, as previously my hdc was NTFS and mounted as so, and some commands were inplace on rc.local in refference to that.   but still a little confused as to what the difference between hdc and hdc1 is, and why i get an error message trying to mount hdc1 but its fine on hdc. yet the opposite way around for hdd.

Thanks :)

---

### Post by frup on 2007-05-06
Have you checked hdc is properly formated?

---

### Post by sonicborg on 2007-05-06
i am sure it is, its operating fine, i have almost filled it up with backed up files.
Its not really a problem, just more of me being clueless and wondering why its working in this way, just seems inconsistant to me.

more concerned about another problem i am having when coming out of full screen games and my desktop res is not returning to defaul again (stuck in the res the game used).

thanks for replys though. :)

---

