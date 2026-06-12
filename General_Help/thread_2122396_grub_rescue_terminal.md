---
title: "grub rescue terminal"
date: 2013-03-05
forum: General Help
---

### Post by linux spartan on 2013-03-05
having booting problems.i have windows on my primary hard disk(sda1) and had windows on my extended hard disk on a partition sda4,swapspace on sda5 and ubuntu linux on sda6 but i decided to delete the windows partition on sda4 and extend and move the linux partition using g-parted.once done,i got a grub rescue error since the grub file and its components could not be found.there is not enough internet access to burn an ubuntu live cd so i decided to use the grub rescue terminal with the following commands found from [http://superuser.com/questions/181733/how-can-i-restore-grub-without-a-live-cd](http://superuser.com/questions/181733/how-can-i-restore-grub-without-a-live-cd) as i referenced from [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) .the commands are 1.ls2.set prefix=(hdX,Y)/boot/grub3.set root=(hdX,Y)4.set5.ls /boot6.insmod /boot/grub/linux.mod7.linux /vmlinuz root=/dev/sdXY ro8.initrd /initrd.img9.boot.on my system i have to specify tghe full path name each time i.e instead of ls /boot i have to write ls (hd0,6)/boot/ .i used to dual boot so i wanted to ask if i load ubuntu via the grub rescue way and do a "grub-install /dev/sda",will it bring back dual boot where by windows loads from my primary partition sda1?or do i have to modify it?plus am using ubuntu12.04

---

### Post by linux spartan on 2013-03-05
solved!!!!!did the following commands1.set prefix=(hdX,Y)/boot/grub where my x=0 and y=62.set root=(hdX,Y)3. insmod (hdX,Y)/boot/grub/normal.mod -this loads the normal module4.normal -this executes the grub menu in normal mode as it usually does when booting.mine gave me the option of dual boot too5.loaded my ubuntu as normal and went into terminal and did the following commands6.sudo update-grub7.update grub to the drives mbr by command sudo grub-install /dev/sdX where my X=a;sdacheck if the grub.cfg file is present by running following commands...go to root dir1.cd /2cd boot/grub/check for grub.cfgproblem solved

---

### Post by audiomick on 2013-03-05
I cannot understand that at all!

Because I want to know what you did, and in case anyone else does, here is what I think you meant...

> **linux spartan said:**
> solved!!!!! I did the following commands

1.set prefix=(hdX,Y) /boot/grub where my x=0 and y=6

2.set root=(hdX,Y)

3. insmod (hdX,Y) /boot/grub/normal.mod -this loads the normal module

4.normal -this executes the grub menu in normal mode as it usually does when booting. Mine gave me the option of dual boot too

5.loaded my ubuntu as normal and went into terminal and did the following commands

6.```
sudo update-grub

```

7.update grub to the drives mbr by command 
```
sudo grub-install /dev/sdX
``` 

where my X=a;sda

check if the grub.cfg file is present by running following commands...go to root dir1.cd /2cd boot/grub/check for grub.cfg

problem solved

---

### Post by linux spartan on 2013-03-10
thats exactly what i did thank you

---

