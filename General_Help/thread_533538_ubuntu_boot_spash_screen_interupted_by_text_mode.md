---
title: "ubuntu boot spash screen interupted by text mode"
date: 2007-08-24
forum: General Help
---

### Post by cyneuron on 2007-08-24
hello there

when ubuntu boots on my system, graphical ubuntu splash ( which i really like), is interrupted in between by text mode.

it shows that /dev/sda1 (which is my windows partition), has some error , and its not automatically fixing this.

thereafter, booting goes in text mode, without any problem.

i just want it to show only graphical boot, which  i really like. 

I also think this is also slowing down my boot up time.

any help....

---

### Post by McNils on 2007-08-24
Have you tried to fix the disk by starting windows?

---

### Post by cyneuron on 2007-08-24
but there is no error on windows partition.

my windows xp boot ok.

i have pclinuxos also installed on my system. no error with that.

previously i used to install ubuntu grub to its own root partition, and then boot it from windows boot loader using bootpart. i thought this error is bcoz of this,

but this time i installed grub on master boot recored.

but still the same error.....

---

### Post by Herman on 2007-08-24
Hello ,
>  it shows that /dev/sda1 (which is my windows partition), has some error , and its not automatically fixing this. What error exactly would this be?
Would it be something like "the bootsector does not match its backup" or something like that?
Do you have Windows in a FAT32 file system or NTFS?
>  		but there is no error on windows partition.
 Windows probably isn't smart enough to know about a lot of the errors it has. :)

Regards. Herman :)

---

### Post by cyneuron on 2007-08-24
i have fat32 parttion in windows.

i also thought of possible error bcoz of non-matching of grub.... that's why intsalled grub to mbr...

but still no help...

error is something like this.

i think it is checking each sector of partition, as it shows series of no. like 1:a:... to 357:.... 

any help ?

---

### Post by Herman on 2007-08-24
No-one can really help you until you can tell us what the error message is or we can run some tests to determine the exact cause. :)

Okay then, let's see if we can spot the problem by taking a look at some of the details of your computer's file systems and partitions. :)

Can you boot your Ubuntu installation and open up a terminal and post here the output from: sudo fdisk -lu
and: blkid
and: cat /etc/fstab 
Please? :)
```
sudo fdisk -lu
```
```
blkid
```
```
cat /etc/fstab 
```
Regards, Herman :)


---

