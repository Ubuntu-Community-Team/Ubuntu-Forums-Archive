---
title: "Virtualbox 4.3 start error"
date: 2014-08-02
forum: General Help
---

### Post by Domgoa on 2014-08-02
Greetings,

I am receiving this error whenever i try to start virtualbox 4.3.14:

 Kernel receivingdriver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I have googled and have not found a solution, please help.

I am runing Ubuntu 12.04 LTS on Acer C710 using Crouton. could Crouton be the problem? otherwis i can install Chrubuntu.

---

### Post by monkeybrain20122 on 2014-08-02
It tells you exactly what to do, open the terminal and type
```
sudo /etc/init.d/vboxdrv setup
```
press enter, that's it.

---

### Post by Domgoa on 2014-08-02
This is what i get when i enter that command.
$ sudo /etc/init.d/vboxdrv setup

Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

---

### Post by westie457 on 2014-08-02
```
sudo apt-get install dkms
``` followed by ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo /etc/init.d/vboxdrv setup
``` should fix things.[/FONT][/COLOR]

---

### Post by Domgoa on 2014-08-02
Nope, its still failing. 

I already had the dkms installed. Could be that its because im runing 64bit and its installing i386? Thats the way it apppears to me.
This is what i got after entering those commands.

The following packages were automatically installed and are no longer required:
  libgconf-2-4:i386 libatk1.0-0:i386 libunistring0:i386 libidn11:i386
  libnss3:i386 libcairo-gobject2:i386 libcap2:i386 libdbus-glib-1-2:i386
  libgomp1:i386 libcairo2:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libcurl3:i386 libdbusmenu-glib4:i386 libgtk-3-0:i386 libxft2:i386
  libcroco3:i386 libdbusmenu-gtk4:i386 libdbusmenu-gtk3-4:i386 libnspr4:i386
  rpm librpmbuild2 libgettextpo0:i386 libjasper1:i386 libxtst6:i386
  libpango1.0-0:i386 librpmsign0 libxcb-render0:i386 librtmp0:i386
  libxcb-shm0:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(precise)elohim@localhost:~/Desktop$ sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

---

### Post by ajgreeny on 2014-08-02
Which architecture version of VirtualBox have you got; I presume it must be the 64 bit?

---

### Post by Domgoa on 2014-08-02
It dosnt say, i installed virtualbox 4.3 through terminal so i presume that it is 64bit (x86_64), since the previouse version i had installed was 64bit according to the terminal and it still gave me the same problem. When i installed virtualbox 4.3 via the terminal it was not a total sucess either. I tried to install virtualbox 4.3 through the ubuntu 
software center but it did not work. I just tried GDebi Package Installer on virtualbox-4.3_4.3.14-95030~Ubuntu~precise_amd64.deb and it was a sucess. I am now positive its 64bit.

---

### Post by SeijiSensei on 2014-08-02
First, I recommend you follow the installation [procedure described on the VirtualBox site ]("https://www.virtualbox.org/wiki/Linux_Downloads")for "Debian-based" Linux distributions.  This will install VB and all required dependencies.  It will also keep VB in sync with future kernel upgrades without any intervention on your part.

---

### Post by Domgoa on 2014-08-02
I followed the instructions in this video [Install/Upgrade Oracle VirtualBox 4.3+ in Ubuntu 12.04]("https://www.youtube.com/watch?v=2DfbUP2LDTk&index=1&list=FL-IPouSLg_b9fyLVc-XFvhg"),but to no complete avail. 

When i update through the terminal there are duplicate source list entries.

When i enter /etc/apt/sources.list into terminal, permission is denied.

Entering:  '/etc/init.d/vboxdrv setup' into terminal, i get:  bash: /etc/init.d/vboxdrv setup: No such file or directory
   [COLOR=#0000ff]
[/COLOR]

---

### Post by Dennis on 2014-08-02
Do you have the correct headers?

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Domgoa on 2014-08-02
when i run the code: 
sudo apt-get install linux-headers-$(uname -r)

This is what i get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.4.0
E: Couldn't find any package by regex 'linux-headers-3.4.0'

I tried finding the linux header 3.4 in synaptic package manerger,without success, its the header i think is required by virtualbox.

Is there any other way to obtain this header?

---

### Post by Domgoa on 2014-08-02
Here are some futher details on the error: 

 [TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] Machine
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}
[/TD]
[/TR]
[/TABLE]

---

### Post by Domgoa on 2014-08-02
I manged to find the linux header 3.4 online by download the package at this [site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/"). 

The package that i manged to install is, linux-headers-3.4.0-030400_3.4.0-030400.201205210521_all.deb

This site may also be of use: [http://ubuntuguide.net/how-to-install-linux-kernel-3-4-0-on-ubuntu-12-0411-10](http://ubuntuguide.net/how-to-install-linux-kernel-3-4-0-on-ubuntu-12-0411-10)

---

### Post by Domgoa on 2014-08-03
It is possible to get it running on a Acer C7 Chromebook. 

[https://www.youtube.com/watch?v=yZpMHnHve5g](https://www.youtube.com/watch?v=yZpMHnHve5g)

[https://www.youtube.com/watch?v=ykfQVqQsFfU&list=UUr-wRRYprB5J9dZbN56z6WQ](https://www.youtube.com/watch?v=ykfQVqQsFfU&list=UUr-wRRYprB5J9dZbN56z6WQ)

---

