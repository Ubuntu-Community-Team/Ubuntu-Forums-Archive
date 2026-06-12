---
title: "Getting XP to recognize spare HDD with Ubuntu?"
date: 2006-12-19
forum: General Help
---

### Post by RobotChild on 2006-12-19
After having no luck with web transfers of large files to my XP box, I decided to just to put the HDD with Ubuntu into the PC with XP. I expected that it would be recognzied like any other slave drive.

Apparently not.

So now I'm stuck with 10gb worth of important files I cannot move.

I absolutley need this files.

Can anyone help?

---

### Post by meng on 2006-12-19
What sort of filesystem did you use for Ubuntu? ext3? If so, then install fs-driver
[www.fs-driver.org](www.fs-driver.org)

---

### Post by RobotChild on 2006-12-19
To tell you the truth, I don't really know.

I'm using Dapper Drake, and did no configuring during install.

---

### Post by meng on 2006-12-19
Probably ext3 then.

---

### Post by RobotChild on 2006-12-19
I installed the driver but it only showed my first 200gigger,(With XP), and not my second with Ubuntu.

---

### Post by meng on 2006-12-19
What about your jumper cables, is it a master/slave thing?

---

### Post by RobotChild on 2006-12-19
The first drive is a SATA so there is no jumpers, and I've tried the second in both slave, and master.

---

### Post by AusIV4 on 2006-12-19
This isn't going to be much help, but I've been trying to figure out the same thing. Ubuntu auto-mounts my XP partition, but XP doesn't acknowledge the existence of my Ubuntu partition, despite having ext3 drivers.

---

### Post by RobotChild on 2006-12-20
I give up.

Can anyone explain how to use gFTP?

I don't know how to set it up, with what ports to use etc.

---

### Post by hal10000 on 2006-12-20
Try this if you want access to your ubuntu-partition from within windows:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine)
You have to install the program under windows.

---

### Post by holdinout on 2006-12-20
Hm, that stinks, I didn't know you could access Ubuntus partitions from Windows...

---

### Post by etcpool on 2006-12-20
don't give up so quick, check your hardware check your motherboard configuration if your primary drive is sata then your should have at least 2 ide channel left available, then check it.

ide has all available 4 channels right? i assume that you should have at least one or two used for cd or dvd rom (maybe one for read drive one for burning drive or something like that)

check the jumper setting of your ide drive ide has two connectors one is primary one is secondary both have it's same two sub channel as primary-master & slave and secondary-master & slave if your cd-dvd drive is in primary channel and set as primary (in case of only one removable drive) then you can put your additional harddrive either as a slave in primary channel or both as master or slave as of your choice in secondary channel. 

Then your motherboard should now recognize your new added harddrive, or you have to make it recognize in your motherboard configuration menu.

once, you got your harddrive reconized then you can boot into your winxp as normal then go to [http://www.fs-driver.org](http://www.fs-driver.org) download the software install it and set the drive letter for your linux partition in your added harddrive and start browsing your files...


hope this helps, much or less


;)

etc,

---

