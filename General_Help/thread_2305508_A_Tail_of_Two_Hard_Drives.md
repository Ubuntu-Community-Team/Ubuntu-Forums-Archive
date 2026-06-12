---
title: "A Tail of Two Hard Drives"
date: 2015-12-06
forum: General Help
---

### Post by JL_B on 2015-12-06
A Tail of Two Hard Drives

 I have two hard drives Drive A shall be Windows 10 Drive B shall be Ubuntu 14.04. They both work. How do I boot from one to the other without using the BIOS boot menu. I attempted EasyBDU  and gave up.  I do not see any posts about computers using two hard drives  the problem is either very simple or extremely rare.

                        

What forum could I find details on how to use the Terminal? Language etc.

  

 My very first post forgive me  and thank you


 Jerry

---

### Post by TheFu on 2015-12-06
Hi Jerry, Welcome to the forums.

Grub is the tool that most people use to select which OS they want to boot. I don't have Win10, so don't know how well supported that is, or isn't.

"Terminal" isn't a program (regardless of what Ubuntu says), it is an interface type.  There are many different terminal types and hence, there are many different terminal programs. Today, that doesn't matter too much to most users, but if you were connecting to a Vax, then you'd want to use an xterm to get a true, 100% compatible vt-102 terminal emulation. The new-fangled, fancy terminal programs used today do NOT properly emulate a vt-102 completely.

However, for your needs at this level today, you can probably use 

* terminal  (lxterm, lxterminal, xterm, rvxterm, and 20+ others_
* CLI (non-GUI interface)
* shell (the program you normally type into when inside a terminal) bash is the default "shell" - analogous to cmd.exe on Windows. On Unix, there are 15+ different shells and different users will choose different shells.

interchangeably.

help.ubuntu.com - has guides that should help you learn what you seek.  There's also a free PDF file (or you can buy this book at any bookstore): [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - do yourself a favor and read the first 200 pgs this week if you want to understand Unix/Linux and the shell.

If you just want to point-n-click as an end user, that book will still be helpful, but you probably want to begin with the [http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) or [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) for servers.

---

### Post by grahammechanical on 2015-12-06
Is Ubuntu installed already? If not then when you run the live session open the Disks Utility and see what labels has been given to the Windows drive and the soon to be Ubuntu drive. You want to find out if the Windows drive is sda and the Ubuntu drive is sdb or sata drive a & sata drive b or the other way around.

This is important because the Ubuntu installer defaults to installing the Linux boot loader (Grub) into sda and if that is the Windows drive then you will loose the Windows boot loader. With Windows & Ubuntu on separate hard drives it is not necessary to lose the Windows boot loader.

So, if Ubuntu is on sdb direct the install to put Grub onto sdb. And then select the Ubuntu drive in the BIOS/UEFI to be the drive to load from. Then you should see a Grub boot menu which will let you choose between Windows & Ubuntu.

If Ubuntu is already installed, and it is installed on sdb then load Ubuntu & run

```
sudo update-grub
sudo grub-install /dev/sdb
```

If Ubuntu is on sda then the second command becomes

```
sudo grub-install /dev/sda
```

Regards.

---

