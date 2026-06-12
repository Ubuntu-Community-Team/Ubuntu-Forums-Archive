---
title: "Chroot, Program (Smartboard Notebook) installed to /opt cannot open easily"
date: 2013-03-31
forum: General Help
---

### Post by aarthurn on 2013-03-31
Hello All,

Rather complicated problem.  I will describe what I did in steps so maybe someone can catch my screwup or lead me in the right direction.

Problem:  I have an ASUS X202 laptop (touchscreen near-ultrabook) which came with windows 8.  First thing I did was install ubuntu (32 bit) in a dual boot environment.  HATED! Windows 8 which in my opinion is completely broken and unusable for everyday use.  So I formatted and installed ubuntu on the entire disk.  The wireless did not work at all in ubuntu and there was no 32 bit deb file for my card but there was a 64 bit deb file.  So I installed the 64 bit ubuntu and everything was working great.  Unfortunately I need to use Smart Technologies Notebook Software which is only 32 bit.  

Solution:

1.  I followed this excellent chroot guide: [http://mparusinski.blogspot.ca/2012/10/the-art-of-chroot-running-quantal.html](http://mparusinski.blogspot.ca/2012/10/the-art-of-chroot-running-quantal.html) and got the program installed inside a 32bit chroot environment.  Now I have binaries in /opt/Smart which I can run the programs from. 

2.  now normally I run a command in the chroot environment by "schroot -c quantal -d notebook" which runs the script I made in the chroot that with change to the /opt/Smart directory and run ./command

3.  I made a script "notebook" in the main system (64 bit) which runs the command in step 2. and used "Main Menu" to add it to unity.  Now I can open the software as if it is a normal 64 bit program.  

Problems with my approach:

1.  To connect a smartboard and have it work as expected I need to have the SmartService running in the background.  I do not know how to have a service from a chroot running in the background other than doing exactly the same thing I did above.  This seems really buggy since my computer crashes constantly if I run the service as a regular command.  This is what I am currently doing with a startup script "gksudo smartservice"

2.  This "Smartservice" needs to be run as root or the smartboard is not picked up as a smartboard (only as a pointing device)

3.  It would be so much better if all the binaries in the /opt/Smart/.../bin directory were exucutable from anywhere in the chroot.

4.  This solution is really messy...

Any suggestions? 

I was also wondering if a cleaner solution would be to install a 32 bit ubuntu and somehow install the driver for my wireless card in a 64 bit chroot?

Thanks for reading my complicated mess of a problem.

---

### Post by schragge on 2013-03-31
Quantal supports [Multiarch]("http://wiki.debian.org/Multiarch"), so maybe this could work out for you better than chroot jail. See also [uwiki]MultiarchSpec[/uwiki].

---

### Post by aarthurn on 2013-04-01
I can't believe how easy that was.  Your suggestion was a lifesaver!

---

