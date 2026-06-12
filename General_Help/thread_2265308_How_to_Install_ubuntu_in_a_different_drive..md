---
title: "How to Install ubuntu in a different drive."
date: 2015-02-14
forum: General Help
---

### Post by krishfrz on 2015-02-14
Hello,I want to install ubuntu after installing windows 8.1 in a different drive.when i tried it first time in ubuntu there is only a single HDD shown.but when i use fixparts /dev /sda the partition were shown and i finally select the drive in which i want to install ubuntu but after the installation is complete there is no GRUB bootloader to switch from windows then i google this problem and i found that the solution is fdisk /dev /sda then press w then type two commands $ sudo grub-installer --boot-directory=/boot /dev/sda then $ sudo update-grub ok done but then i reboot my laptop all drives became in one allocated 931gb and i lost my all data but by luck i got my data back by using testdisk but some files are not found ok,no problem,but again i want to install ubuntu after windows 8.1 installation without loosing my data so can please anybody help me out i am a computer science engineering student.Thanks in advanced.

---

### Post by nerdtron on 2015-02-14
OK just to be clear. You have two separate physical hard drives? Or just two separate partitions on a single hard drive?

If you have two separate drives. It's better to remove the windows 8 drive. Install Ubuntu with only one drive connected so that you won't have any danger of overwriting any files on the windows 8.

After you are sure that you installed ubuntu correctly, connect the windows 8 drive. Now the two OS are independent of each other, you just choose which OS to boot from the BIOS screen.

---

### Post by oldfred on 2015-02-14
Best to see details to confirm configuration:

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Also what brand/model computer & what video card/chip?

---

### Post by oldos2er on 2015-02-14
> **krishfrz said:**
>  i want to install ubuntu after windows 8.1 installation without loosing my data

Make backups, which is much easier to do than using testdisk.

---

### Post by krishfrz on 2015-02-16
Thanx you all for your valuable replies and my problem is fixed and i have single HDD with two partition and now i finally dual boot my Laptop.again thanks):P):P

---

### Post by Bashing-om on 2015-02-16
krishfrz; Great !

Pleased you are up and running.
Please provide the means you employed to arrive at your dual-boot system ( install ubuntu along side option ?) ; as it will help others and add to our data base.


Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

