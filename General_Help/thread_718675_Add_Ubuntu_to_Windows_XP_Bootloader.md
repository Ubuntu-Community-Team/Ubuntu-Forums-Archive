---
title: "Add Ubuntu to Windows XP Bootloader"
date: 2008-03-08
forum: General Help
---

### Post by gerfuls on 2008-03-08
I have laptop that just had Ubuntu 7.10 installed when I decided to wanted to play some windows games. So i moved the ext3 partition back and added a NTFS partition to the front of the HDD for windows. After I installed windows xp pro everything worked great but I no longer can get to Ubuntu. I know how to access the boot.ini file for windows, but what line do i need to add in order to have Ubuntu to be an option. if this isn't possilbe how do i use grub to boot into windows?

---

### Post by taurus on 2008-03-08
You need to install GRUB back to MBR to boot both OSes.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)
or
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by buntu_Geek on 2008-03-08
Boot from your live Cd

* Do the following steps 

The procedure is simple...type the following in the terminal:
```

sudo grub

```
YOu will get grub> prompt, then
```

grub> find /boot/grub/stage1

```
This command gives the partition where the stage one of your grub is (hd?,?), then use this for the following commmand(replacing the ? marks):
```

grub> root (hd?,?) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub

```

---

### Post by dabang on 2008-03-08
I guess you could add Ubuntu to the Windows bootloader, I did that a long time ago (when SuSE 7.x was new). But to do so, you would need your old MBR with grub on it an write it to file by "dd". I don't remember the details, so I think it's easier to reinstall grub. Maybe this can be of help:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ronmarley1 on 2008-03-08
The Super GRUB Disk is a bootable iso that will rstore GRUB to the MBR.
You can download it here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jake1stbase on 2008-03-08
i know there's a program for it, tyou download the program, and put your CD in (with windows running) the run the program, and it add its to the windows bootloader

---

### Post by gerfuls on 2008-03-08
ok i've got grub up but now i'm getting grub error 17. i've triend all of the normal fixes with the Super Grub Disk. it's probably because i moved the partitions around. please help!

---

### Post by gerfuls on 2008-03-08
ok i realized with grub is trying to do. its trying to boot hd(0,0) but that is now the windows ntfs partition. the ext3 is on hd(0,1). how do i tell grub this?

---

### Post by gerfuls on 2008-03-08
ahh! i saved ubuntu! but now how do i add windows to the grub list?

---

### Post by gerfuls on 2008-03-08
Ok i've i got it all fixed! Here is what I did:

First i fixed the MBR to use grub with the Super Grub Disk using the 
```
GRUB => MBR & !LINUX! (1) AUTO
```
command and followed these steps to fix the partition rearranging problem:

1. Boot from Ubuntu live Cd
2. run command in terminal:
```
sudo gedit /boot/grub/menu.lst
```
3. find and replace "0,0" with "0,1"
4. Add this line to the bottom of page:
```
title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
makeactive
chainloader +1
```
5. save file and reboot. everything worked.

---

### Post by buntu_Geek on 2008-03-08
Mark this thread as solved....

Thread tools--> mark this thread as solved....

voila...

This might help other who are having the same problems...

---

