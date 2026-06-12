---
title: "Installing Visualization Software"
date: 2007-01-17
forum: General Help
---

### Post by happybill on 2007-01-17
Following advice from Heathenx to look at VMware as an alternative to Crossover for running  programs written for Windows, I did just that.

A preliminary look at VMware left me confused, so I tried Xen-tools. They come with Ubuntu and can be loaded and installed via Synaptic.  I didn't get very far because instructions that I can understand do not seem to exist.

Next, I noticed a reference in the Official Ubuntu Book, page 240, to the installation of qemu.  I managed to create the virtual drive file, hd.img, but the next step, to boot an install CD in the virtual machine failed because the file could not be opened. The command is printed in the book as "foo@bar:~$ qemu -boot d -cdrom /dev/cdrom -hda hd.img"

By then, I had found the very helpful Howto posted by Peturrr on 27 May 2006, with good, clear, instructions for installing the free vmware server.  All seemed to be going well after running the code "sudo ./vmware-install.pl", but the process suddenly stopped - before my registration key had been requested - with the message "unable to get the access rights of the source file './vmware-vix/bin'.  Execution aborted."

Clearly, something is wrong, possibly my fault. To a large extent, I am following the instructions blindly, and if any changes are need to suit my system, I cannot see them.  Can anybody help, please?

---

### Post by bodhi.zazen on 2007-01-17
See if this helps:

[http://www.ubuntuforums.org/showthread.php?&t=183209](http://www.ubuntuforums.org/showthread.php?&t=183209)

---

### Post by happybill on 2007-01-18
Hello,

Thanks for the prompt reply.  The link you provided leads to the advice posted by Peturrr that I am already following.

Since yesterday, I have found that the first command of the procedure did not work correctly  In fact, it has an error and does not work until the dash between 'linux-headers' and ' "uname -r" 'is replaced by a space.  Running it produces a list of linux headers, with the instruction to choose one.  Mine is 2.6.15-27-386.

First I went to Synaptic and installed the two headers, then reinstalled vmware.  The process stopped with the same error about lack of access to the file ./vmware-vix/bin. I went back to Synaptic and removed the linux-headers in order to start again.

After running the first command again with the dash replaced by a space and, after getting the list, I ran the command again with 'linux-headers-2.6.15-27-386 ' in place of 'linux-headers "uname -r" '.
Quite a lot happened, for what it is worth, here is a copy of the terminal window. If there is a smiley, it is not my doing.

[COLOR="RoyalBlue"]ubill@U-DD:~$ sudo apt-get install  linux-headers-2.6.15-27-386 build-essential xinetd
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-headers-2.6.15-27 linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc libc6-dev-amd64 lib64gcc1 glibc-doc libstdc++6-4.0-doc
  stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-386 linux-kernel-headers make xinetd
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 294kB/19.9MB of archives.
After unpacking 127MB of additional disk space will be used.
Do you want to continue [Y/n]?
Media Change: Please insert the disc labelled
 ‘Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)’
in the drive ‘/cdrom/’ and press enter

Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main dpkg-dev 1.13.11ubuntu7 [163kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main xinetd 1:2.3.14-0ubuntu1 [131kB]
Fetched 294kB in 41s (7075B/s)
Selecting previously deselected package binutils.
(Reading database ... 72563 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27.
Unpacking linux-headers-2.6.15-27 (from .../linux-headers-2.6.15-27_2.6.15-27.50_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27-386.
Unpacking linux-headers-2.6.15-27-386 (from .../linux-headers-2.6.15-27-386_2.6.15-27.50_i386.deb) ...Selecting previously deselected package xinetd.
Unpacking xinetd (from .../xinetd_1%3a2.3.14-0ubuntu1_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu7) ...
Setting up linux-headers-2.6.15-27 (2.6.15-27.50) ...

Setting up linux-headers-2.6.15-27-386 (2.6.15-27.50) ...
Setting up xinetd (2.3.14-0ubuntu1) ...
Stopping internet superserver: xinetd.
Adding `diversion of /etc/init.d/inetd to /etc/init.d/inetd.real by xinetd'
Starting internet superserver: xinetd.

Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
ubill@U-DD:~$ [/COLOR]

Despite all this, the next attempt to install vmware was aborted as before.  Have I simply made things worse?  I would never have guessed that preparation of a fully updated copy of Dapper Drake  for the installation of vmware was so complex

---

### Post by Jimlas53 on 2007-01-18
It sounds more like file permissions related to the vmware files.  Did you run the install script as sudo?   sudo ./vmware-install.pl
Usually access permissions problems show up when the system thinks you don't have the correct level of permissions to do what you are trying to do.

Hope this helps!

---

### Post by bodhi.zazen on 2007-01-18
> **happybill said:**
> Hello,

Thanks for the prompt reply.  The link you provided leads to the advice posted by Peturrr that I am already following.

Since yesterday, I have found that the first command of the procedure did not work correctly  In fact, it has an error and does not work until the dash between 'linux-headers' and ' "uname -r" 'is replaced by a space.  Running it produces a list of linux headers, with the instruction to choose one.  Mine is 2.6.15-27-386.

First I went to Synaptic and installed the two headers, then reinstalled vmware.  The process stopped with the same error about lack of access to the file ./vmware-vix/bin. I went back to Synaptic and removed the linux-headers in order to start again.

After running the first command again with the dash replaced by a space and, after getting the list, I ran the command again with 'linux-headers-2.6.15-27-386 ' in place of 'linux-headers "uname -r" '.
Quite a lot happened, for what it is worth, here is a copy of the terminal window. If there is a smiley, it is not my doing.

...



I do not see any errors in your output.

I liked the suggestion of Jimlas53

Last, when you post, look down ;)

There is a "Disable smiles in text" option that is helpful for these situations.

Otherwise, perhaps post your problem/question in the thread I gave you as you may have better luck there :p

---

### Post by happybill on 2007-01-19
Hello, thanks to you both.

to complete the description of my problem, I ahve attempted another installation. The Terminal text is reproduced below.

ubill@U-DD:~$ cd ~/temp
ubill@U-DD:~/temp$ cd vmware-server-distrib
ubill@U-DD:~/temp/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/home/ubill/vmware]

The path "/home/ubill/vmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/ubill/sbin]

The path "/home/ubill/sbin" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/ubill/lib/vmware]

The path "/home/ubill/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/home/ubill/man]

The path "/home/ubill/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/ubill/doc/vmware]

The path "/home/ubill/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

ubill@U-DD:~/temp/vmware-server-distrib$

---

### Post by ramjet_1953 on 2007-01-19
Hi there!

Why not give Innotel's VirtualBox a try?

I found it installed easily and the only tweaking required was to set-up permissions for USB devices, which is covered in the user manual.

Regards,
Roger 8)

---

### Post by ramjet_1953 on 2007-01-19
Sorry, the company is InnoTek.

Roger

---

### Post by enopepsoo on 2007-01-19
virtual box only runs on 32 bit.  qemu is quite slow because it does full emulation.  To get decent speed out of it, you will need to install kqemu (the kernel extension) or use the new kvm stuff (which I have not tried, but I think it may be in feisty???:confused: )

your trouble installing vmware was probably because you had some packages missing.  I remember needing build-essential and xinetd (there was probably more).

---

### Post by happybill on 2007-01-22
I am still struggling, and failing, to install vmware and virtualbox.  Did Ramjet_1953 install virtualbox in Ubuntu Dapper Drake?  All my attempts start with a fresh install of Ubuntu 6.06 fully updated.   Thank goodness for drive image backup and restoration!

---

### Post by happybill on 2007-01-25
How do I build a kernel?  
In my attempts to install VirtualBox, I have sought help from [email]info@innotek.de[/email].  They have patiently. but firmly, referred me back to the FAQs on [www.virtualbox.org](www.virtualbox.org) and the downloadable manual.  By implication, they have agreed that I have done nothing wrong, except that I have not built the kernel as advised in the manual. I thought that, by installing the linux-headers for kernel 2.6.15-27-386, that was what I was doing, but apparently not.  There is no other advice about kernel buiding.

---

