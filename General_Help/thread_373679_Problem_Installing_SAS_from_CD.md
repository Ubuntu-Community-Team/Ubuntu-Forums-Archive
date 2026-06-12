---
title: "Problem Installing SAS from CD"
date: 2007-03-01
forum: General Help
---

### Post by spryangue on 2007-03-01
Hello,

I'm new to Ubuntu and Linux in general.  I have the SAS statistical software for Linux on CD that I would like to install and I'm having problems.  I am trying to follow the instructions from the company located here: 

[http://support.sas.com/documentation/installcenter/unix/v9/unix9_install.pdf](http://support.sas.com/documentation/installcenter/unix/v9/unix9_install.pdf)

The CD mounts without any problems.  I'm on page 13 of the pdf which says to start the install using the following command:

$ /cdrom/SASSETUP

I open the terminal and type that command and get the following:

spryangue@spryangue-laptop:~$ /cdrom/SASSETUP
bash: /cdrom/SASSETUP: /bin/sh: bad interpreter: Permission denied

After that I try the following with the same result:

spryangue@spryangue-laptop:~$ sudo /cdrom/SASSETUP
Password:
sudo: unable to execute /cdrom/SASSETUP: Permission denied
spryangue@spryangue-laptop:~$

So, I'm stuck.  Any ideas related to this specific problem (i.e. I'm not looking for any alternative stat packages that I can install, I want to install this exact package from these CDs)?  Thanks for any help you can provide.

---

### Post by mbw on 2007-11-06
Your problem is likely that the CD was automounted with the "noexec" mount option -
preventing you from running the SAS installation script.

use the command "mount" to list the mount options with the cdrom volume (/media/cdrom0) 

unmount ("umount /media/cdrom0") the cd and remount with regular options or the defaults and you should be able to proceed with the install.  

Other fun SAS 9.1.3 linux install gotchas:

You'll need the SID (SAS Installation Data file) with your license in in before
being allowed to continue the install

You'll need to find and download the correct JRE  ( 1.4.2_09 ) in order to proceed with
the install past the first cd.

Try:
[http://java.sun.com/products/archive/j2se/1.4.2_09/index.html](http://java.sun.com/products/archive/j2se/1.4.2_09/index.html)

Get This one:
Linux Platform - Java(TM) 2 Runtime Environment, Standard Edition 1.4.2_09
	Download Now! self-extracting file 	j2re-1_4_2_09-linux-i586.bin

extract somewhere, then specify option "2" to tell the installer where to find it.

Then enter the path to the JRE directory

Good luck!

Matt

---

