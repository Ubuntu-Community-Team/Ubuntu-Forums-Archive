---
title: "Black Screen After..."
date: 2007-09-02
forum: General Help
---

### Post by Shoot3r101 on 2007-09-02
OK I installed wubi and everything went PERFECT then when I selected ubuntu from the boot menu my screen just goes black pure black and just stays that way. I did try CTRL+ALT+F1 then it comes to a screen with a message like Can't display 1152x864. Sooo... 
System Specs:
---------Basics-----------
Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
BIOS: Phoenix ROM BIOS PLUS Version 1.10 A01
Processor: Intel(R) Celeron(R) CPU 2.53GHz
Memory: 254MB RAM
---------Display-----------
DirectX Version: DirectX 9.0c (4.09.0000.0904)
Card name: Intel(R) 82865G Graphics Controller
Manufacturer: Intel Corporation
Chip type: Intel(R) 82865G Graphics Controller
Display Memory: 96.0 MB
Current Mode: 1024 x 768 (32 bit) (75Hz)
---------HDD-----------
Drive: C:
Free Space: 60.6 GB
Total Space: 73.2 GB
File System: NTFS
Model: ST380011A

---

### Post by Shoot3r101 on 2007-09-03
Come on someone must have had this problem before?

---

### Post by abhilash82 on 2007-09-03
I also run Ubuntu on a similar system spec. and have run it using Wubi and the standalone install and have had no problems. I think you should try the recovery console option while booting. You have to reconfigure xorg.conf file through your terminal window.

Navigate to /etc/X11/

```

sudo gedit xorg.conf 

```

Check if in the Devices section the following is there or else replace it with the one below..
> 
Section "Device"
	Identifier	"Intel Corporation 82865G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection


Save the file and reboot the system. It should work now.

---

### Post by Shoot3r101 on 2007-09-03
Thanks for help I really appriciate but how do I get to recovery console? When I boot into ubuntu I just get a black screen and if I press CTRL+ALT+F1 the error message pops up.
Ps: it also allows me to type.

---

### Post by abhilash82 on 2007-09-03
> **Shoot3r101 said:**
> Thanks for help I really appriciate but how do I get to recovery console? When I boot into ubuntu I just get a black screen and if I press CTRL+ALT+F1 the error message pops up.
Ps: it also allows me to type.

Right after you select the Ubuntu entry on the menu, press ESC, that'll get you to a grub menu, there find the "Ubuntu (Original Kernel)" entry and press "e", that'll get you to another menu, find the "kernel ... " line and press "e", and at the end of the line, remove the "splash" and "quiet" options, press enter, then press b; it should give you more details

Also, go into Windows, and post the contents of the C:\wubi\logs directory (there should be 2 files in there)

---

### Post by Shoot3r101 on 2007-09-03
thank you thank you I have been up all night working on ubuntu and this just made my day =D!

---

### Post by Shoot3r101 on 2007-09-03
Well I went through everything that you said and then an error comes up

```

Begin: Waiting for root file system... ...
Done.

Check root= Bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules Is /dev
ALERT! does not exist. Dropping to a shell!

BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initrafs)    (<-Here is where I am able to type.)
```
Comes up after the press b part.

---

### Post by abhilash82 on 2007-09-03
I think your installation is corrupted. I suggest you go to Windows(Add/Remove Programs) and uninstall wubi and if you have the Live CD boot it from it to ensure that Ubuntu recognizes your hardware. Then you can install directly from the Live CD by following this procedure here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It is always better to have a standalone installation of Ubuntu as the disk access is very slow using Wubi and you are also dependant on your windows installation.

---

### Post by Shoot3r101 on 2007-09-03
I don't believe thats possible but oh well. And I can't install off cd because my "drive" is "defected" supposivly... So im using the wubi way of installing ubuntu.

---

### Post by abhilash82 on 2007-09-03
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT!
You need to run chkdsk for the partition in which you have wubi folder.

---

### Post by Shoot3r101 on 2007-09-03
Well after re-installing wubi I am successfully in ubuntu and when I edit the xorg file the file is blank... *oh man im a newbie the linux*

---

### Post by abhilash82 on 2007-09-03
> **Shoot3r101 said:**
> Well after re-installing wubi I am successfully in ubuntu and when I edit the xorg file the file is blank... *oh man im a newbie the linux*

> **abhilash82 said:**
> I also run Ubuntu on a similar system spec. and have run it using Wubi and the standalone install and have had no problems. I think you should try the recovery console option while booting. You have to reconfigure xorg.conf file through your terminal window.

Navigate to /etc/X11/

```

sudo gedit xorg.conf 

```

Check if in the Devices section the following is there or else replace it with the one below..


Save the file and reboot the system. It should work now.

Type the following in the terminal window.
```

sudo dpkg-reconfigure xserver-xorg

```

you will get a blue screen in your terminal for the xorg configuration and you just have to select the respective parameters of your graphics card as quoted above.

---

### Post by Shoot3r101 on 2007-09-03
eh im stuck on a part. It says "Ammount of memory (kb) used by the video card" can someone please help me. How much do I enter?

---

### Post by abhilash82 on 2007-09-03
> **Shoot3r101 said:**
> OK I installed wubi and everything went PERFECT then when I selected ubuntu from the boot menu my screen just goes black pure black and just stays that way. I did try CTRL+ALT+F1 then it comes to a screen with a message like Can't display 1152x864. Sooo... 
System Specs:
---------Basics-----------
Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
BIOS: Phoenix ROM BIOS PLUS Version 1.10 A01
Processor: Intel(R) Celeron(R) CPU 2.53GHz
Memory: 254MB RAM
---------Display-----------
DirectX Version: DirectX 9.0c (4.09.0000.0904)
Card name: Intel(R) 82865G Graphics Controller
Manufacturer: Intel Corporation
Chip type: Intel(R) 82865G Graphics Controller
Display Memory: 96.0 MB
Current Mode: 1024 x 768 (32 bit) (75Hz)
---------HDD-----------
Drive: C:
Free Space: 60.6 GB
Total Space: 73.2 GB
File System: NTFS
Model: ST380011A

As mentioned in your system specs your Display memory must be 96MB.

---

