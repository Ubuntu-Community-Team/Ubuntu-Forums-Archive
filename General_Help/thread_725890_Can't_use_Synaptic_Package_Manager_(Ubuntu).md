---
title: "Can't use Synaptic Package Manager (Ubuntu)"
date: 2008-03-16
forum: General Help
---

### Post by revbluejeans on 2008-03-16
When I try to open package manager I get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Also when I try to install it says it can't because there is another package manager open even though there isn't.  Please help!

---

### Post by Hazed on 2008-03-16
Did you try what it suggested and run

```
dpkg --configure -a
```

in a terminal?

---

### Post by sandysandy on 2008-03-16
how r u opening package manager

  is it  

system --->  admin ---> synaptic package manager

or thru command line

regards

---

### Post by revbluejeans on 2008-03-16
Yes sorry should have said, when I do it says I need super user privileges.  As I set the thing up and have administrator rights I can't work out why it won't let me do this

---

### Post by revbluejeans on 2008-03-16
Sandy - through

system ---> admin ---> synaptic package manager

---

### Post by Hazed on 2008-03-16
Try

```
sudo dpkg --configure -a
```

---

### Post by sandysandy on 2008-03-16
have u tried Application ---> Add / Remove

also does the problem persist after rebooting.

regards

---

### Post by revbluejeans on 2008-03-16
Hazed - have done as suggested, it let me do this but it hasn't fixed problem

Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by revbluejeans on 2008-03-16
Sandy - tried add/remove and it said that I had one broken application and to use the broken filter, where would I fiond this?

---

### Post by sandysandy on 2008-03-16
> **revbluejeans said:**
> Sandy - tried add/remove and it said that I had one broken application and to use the broken filter, where would I fiond this?


have a look at this link

[http://users.bigpond.net.au/hermanzone/p5.htm#Fix_Broken_Packages](http://users.bigpond.net.au/hermanzone/p5.htm#Fix_Broken_Packages)

regards

---

### Post by crocd on 2008-03-17
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Killed
dpkg: subprocess post-installation script returned error exit status 137   

My resolution to get around this was after trying dpkg --configure -a and a whole host of other fixes and dpkg commands and even trying to manually use dpkg to isntall the libc6.deb file is to remove the following files.

cd /var/lib/dpkg/info

ls -l libc6*
-rw-r--r-- 1 root root   126 2007-10-25 03:10 libc6.conffiles
-rw-r--r-- 1 root root  8322 2008-03-15 21:49 libc6-i386.list
-rw-r--r-- 1 root root 16544 2007-10-25 03:11 libc6-i386.md5sums
-rwxr-xr-x 1 root root   135 2007-10-25 03:11 libc6-i386.postinst
-rwxr-xr-x 1 root root   132 2007-10-25 03:11 libc6-i386.postrm
-rw-r--r-- 1 root root   678 2007-10-25 03:11 libc6-i386.shlibs
-rw-r--r-- 1 root root  8643 2008-03-17 20:09 libc6.list
-rw-r--r-- 1 root root 18285 2007-10-25 03:10 libc6.md5sums
-rwxr-xr-x 1 root root 11267 2007-10-25 03:10 libc6.postinst
-rwxr-xr-x 1 root root  1413 2007-10-25 03:10 libc6.postrm
-rwxr-xr-x 1 root root 13490 2007-10-25 03:10 libc6.preinst
-rw-r--r-- 1 root root   585 2007-10-25 03:10 libc6.shlibs
-rw-r--r-- 1 root root    18 2007-10-25 03:10 libc6.triggers
-rw-r--r-- 1 root root   363 2008-03-17 21:02 libc6-udeb.list

 sudo rm -rf libc6*

I ran ls again and got this 

ls: libc6*: No such file or directory

I then ran sudo apt-get update 

followed by sudo apt-get upgrade

because I forced a dselect package install using dpkg this was my upgrade output

The following packages will be upgraded:
  dselect
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/134kB of archives.
After unpacking 57.3kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up libc6 (2.6.1-1ubuntu10) ...
(Reading database ...
dpkg: serious warning: files list file for package `libc6-i386' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libc6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libc6-udeb' missing, assuming package has no files currently installed.
86605 files and directories currently installed.)
Preparing to replace dselect 1.13.24ubuntu6 (using .../dselect_1.14.5ubuntu16_amd64.deb) ...
Unpacking replacement dselect ...
Setting up dselect (1.14.5ubuntu16) ...

Note the error message!"

As a test I ran 

sudo dpkg --configure -a and sudo apt-get update/upgrade again. I was then able to install any package after that.:)

---

### Post by revbluejeans on 2008-03-26
Thank you for help, it was a problem with the installation of a seperate program that just needed reinstalling.

---

