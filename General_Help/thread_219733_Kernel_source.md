---
title: "Kernel source"
date: 2006-07-20
forum: General Help
---

### Post by dbucky on 2006-07-20
Hi, I just began using linux and I want to get my modem setup.  I've read a lot of the modem howto articles and so far I have installed a GCC compiler and downloaded a modem driver.  I began installing the driver, but during installation it could not find the location of the kernel source files.  I don't know what these are or where to find them.  I have Breezy Badger installed fresh from an install CD I got through the mail.
Here is the output of the installation:

dbucky@ubuntu:~$ cd pctel-0.9.7-9-rht-5
bash: cd: pctel-0.9.7-9-rht-5: No such file or directory
dbucky@ubuntu:~$ cd ~/Desktop
dbucky@ubuntu:~/Desktop$ cd pctel-0.9.7-9-rht-5
dbucky@ubuntu:~/Desktop/pctel-0.9.7-9-rht-5$ ./setup
checking for running kernel version...2.6.12
./configure: line 328: make: command not found
checking for ptserial...ptserial-2.6.c
checking for gcc...3.4.5
searching for kernel includes...** error
could not find any kernel sources in /usr/src
you have either not installed your kernel sources
or your kernel sources are installed in another place then
/usr/src/
please enter your correct kernel source tree, e.g. /usr/src/linux:

I am currently dual booting with Windows and that is how I have internet access.  Please help me figure this out!!

---

### Post by tatimmer on 2006-08-14
I am in a similar position, dual boot with Windows, I have a Smarlink modem with source code drivers which I compiled successfully on Mandrake 10.1 last year, but with Mandrake the linux kernel source and compiler were already installed so this made it very easy for me.  apon compiling these on Mandrake they created "slamr" and "slmodem" which I need to connect my modem to the internet.

Now I installed ubuntu 5.10 and I like the looks, my family also likes the looks which is a main reason why I switched,  but alas no kernel source and no compiler.  

So like you I downloaded about 6 compiler related packages to get gcc running.

I  also downloaded these source tar balls (which was maybe a mistake, I should have grabbed a .deb package instead ???)  following linux-source pakage which is about 40meg and took 2.5 hours:

Download linux-source-2.6.12
File	Size (in kB)	md5sum
linux-source-2.6.12_2.6.12-10.36.dsc 	2.5 	ee4df102b9083dcf4fca13186cae05f4
linux-source-2.6.12_2.6.12.orig.tar.gz 	46071.4 	9272115d4005d4e9773a1a6170fd20cd
linux-source-2.6.12_2.6.12-10.36.diff.gz 	7798.4 	85c3387e4371de6f96e0010f001c0ce4
More Information on linux-source-2.6.12

Package: linux-source-2.6.12 (2.6.12-10.36) [security]
[http://packages.ubuntu.com/breezy/source/linux-source-2.6.12](http://packages.ubuntu.com/breezy/source/linux-source-2.6.12)

I created directory /usr/src and unpacked linux-source-2.6.12_2.6.12.orig.tar.gz 

I had to create a couple symbolic links (/usr/include/linux and /usr/include/asm) which I learned about in a book "Running Linux" .  So far I have not got the modem source to compile.  get an error like "/linux/version.h" no such file.  google tells me I have to cd /usr/src/linux and 

Is there an automated way to set up the kernel sources ? I think I dont have the sources set up correctly.  

There must be an easier way.  Im thinking I would prefer a distro that came with pre-configured kernel-source and gcc compiler ready to go.  

Any help would be appreciated.   THanks.

TomT

---

### Post by dbucky on 2006-08-14
Hello TomT,

What I finally did to install the kernel source was to go to Synaptic Package Manager under system -> administration -> Synaptic Package Manager.  I used the search field to look for **kernel** and then searched through the list.  You will need to install the linux-headers-2.6.12-9-386.  When you click that package to apply it - if I remember correctly - Synaptic will also ask you to install another linux-header package.  Just apply the changes and you should be in business!

If you need any further help please contact me again.  Thanks!

---

### Post by tatimmer on 2006-08-15
I am going to give the Synaptic a try.  Thanks for the reply.

Last eve I was poking around on the install cd and found the directory /pool which contains all kinds of extra packages including a couple versions of gcc under /g and some header stuff under /l.  Not sure what is the proper way to install this but I think you are on to it.

TomT

---

