---
title: "Startup Manager Ubuntu 9.10"
date: 2012-12-15
forum: General Help
---

### Post by agkq62 on 2012-12-15
My old Dell laptop runs a dual boot with Ubuntu 9.10.(I have tried the later versions but none will run my graphics card without of lot of messing about and I am quite happy with this version).

I want to reduce the dual boot timer and sometimes alter the default. I have tried to download Startup Manager with Synaptic but get an error message, presumably because no longer supported.

I there any way I can still get Startup Manager.

Thanks.

---

### Post by Rexilion on 2012-12-15
You can find these settings in a file called:

> /boot/grub/grub.conf
or
> /boot/grub/grub.cfg

I think it's the first, but I'm not sure though. If you have issue's modifying it you can post it here. But it should be pretty straightforward.

P.S. If you mess this up, then your computer won't boot anymore so be careful and keep a liveCD at hand!

---

### Post by Dennis N on 2012-12-15
> **agkq62 said:**
> 
I want to reduce the dual boot timer and sometimes alter the default. I have tried to download Startup Manager with Synaptic but get an error message, presumably because no longer supported.

I there any way I can still get Startup Manager.

Thanks.

Easy way:

Set GRUB_TIMEOUT and GRUB_DEFAULT by editing /etc/default/grub and then run sudo update-grub.

(Note: You could get a .deb file for old startup manager, but then you would have to also deal with any dependencies manually. Not worth it.)

---

### Post by Cheesemill on 2012-12-15
> **Dennis N said:**
> Easy way:

Set GRUB_TIMEOUT and GRUB_DEFAULT by editing /etc/default/grub and then run sudo update-grub.

(Note: You could get a .deb file for old startup manager, but then you would have to also deal with any dependencies manually. Not worth it.)
Those instructions are for Grub2. I believe that 9.10 still used the original Grub in which case you need to edit the menu.lst file. First hit ALT+F2 and type:
```
gksudo gedit /boot/grub/menu.lst
```Then edit the **default** and **timeout** options to your liking.

Edit - Ignore this post. 9.10 used Grub2, ***not*** Grub.

---

### Post by Dennis N on 2012-12-15
According to Distrowatch, Ubuntu 9.10 used GRUB 1.97beta4.

[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

So the menu.lst file was not used.

---

### Post by Cheesemill on 2012-12-15
So it did.

I wasn't sure where you could find that information, I just remember still having Grub in 2009 but that was obviously for 9.04,

---

### Post by agkq62 on 2012-12-15
Thanks for the replies but I am now confused, knew this would happen :)

How do I check the grub version?

---

### Post by Cheesemill on 2012-12-15
You are using Grub 2.

You can ignore all of my posts (the confusing ones) and just follow Dennis N's instructions in post #3.

Sorry for the confusion 8-[

---

### Post by agkq62 on 2012-12-15
Thanks again.

---

### Post by oldos2er on 2012-12-15
Grub Customizer should be used in place of Startup Manager, see [http://www.ubuntututorials.com/grub-customizer-startupmanager-ubuntu-12-04/](http://www.ubuntututorials.com/grub-customizer-startupmanager-ubuntu-12-04/)

---

### Post by Cheesemill on 2012-12-15
> **oldos2er said:**
> Grub Customizer should be used in place of Startup Manager, see [http://www.ubuntututorials.com/grub-customizer-startupmanager-ubuntu-12-04/](http://www.ubuntututorials.com/grub-customizer-startupmanager-ubuntu-12-04/)
Unless you're still running 9.10 like the OP.

---

### Post by agkq62 on 2012-12-16
As usual with me when I tangle with the Terminal it all goes wrong.

Tried the commands from Post 3 but no luck. 

maxwell@maxwell-laptop:~$ /etc/default/grub
bash: /etc/default/grub: Permission denied
maxwell@maxwell-laptop:~$ 

Tried the Grub Customiser, no luck again

E: Some index files failed to download, they have been ignored, or old ones used instead.
maxwell@maxwell-laptop:~$ sudo apt-get install grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hwinfo libhd16 menu
The following NEW packages will be installed
  grub-customizer hwinfo libhd16 menu
0 upgraded, 4 newly installed, 0 to remove and 244 not upgraded.
Need to get 1,195kB/1,860kB of archives.
After this operation, 6,222kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  menu libhd16 hwinfo
Install these packages without verification [y/N]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe menu 2.1.41ubuntu1
  404  Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe libhd16 16.0-1
  404  Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe hwinfo 16.0-1
  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/menu/menu_2.1.41ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/menu/menu_2.1.41ubuntu1_i386.deb)  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/h/hwinfo/libhd16_16.0-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/h/hwinfo/libhd16_16.0-1_i386.deb)  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/h/hwinfo/hwinfo_16.0-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/h/hwinfo/hwinfo_16.0-1_i386.deb)  404  Not Found [IP: 194.169.254.10 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
maxwell@maxwell-laptop:~$ maxwell
maxwell: command not found
maxwell@maxwell-laptop:~$ 

Looks like I'm stuck

---

### Post by Cheesemill on 2012-12-16
> ```
maxwell@maxwell-laptop:~$ /etc/default/grub
bash: /etc/default/grub: Permission denied
maxwell@maxwell-laptop:~$
```/etc/default/grub isn't a command, it's a file you have to edit. To do this type in a terminal:
```
gksudo gedit /etc/default/grub
```This will open the file in a text editor.
Then edit the corresponding entries before saving the file and running:
```
sudo update-grub
```More details can be found here:
[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

---

### Post by agkq62 on 2012-12-16
Great stuff, finally got there, thanks again.

---

