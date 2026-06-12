---
title: "MATLAB installation - disk mount error"
date: 2008-04-07
forum: General Help
---

### Post by NS2-10 on 2008-04-07
I am trying to install MATLAB r2007b with valid license and everything. To do so I insert the disk and cd my way to the disk location, specifically:

> root@foobar:/media/cdrom0# 

There I execute:
> 
root@foobar:/media/cdrom0# bash ./install -t

Upon which the installer starts. I accept the license agreement but the suddently things halt with the message:

> 
/media/cdrom0/update/install/main.sh: line 80: /media/cdrom0/update/bin/glnx86/xsetup: Permission denied

or depending on specific command used to start installation:

> -------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/update/install/main.sh: 168: /media/cdrom0/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


Which seems to be largely the same thing.

I read the following on MathWorks webpage:

> On Linux systems, DVD drives typically mount automatically; however, the drives mount with read-only permission. You might have to change the DVD drive configuration from read-only to execute&#8212;see Problems with Your DVD Drive

Ok, so perhaps this is what has happened. They recommend I use the following command:

> mount -t iso9660 /dev/dvd /dvd

However this returns:

> 
mount: mount point /dvd does not exist

Huh? What should I do?

---

### Post by fraia on 2008-04-08
Hi

First, Check out the inst_doc.pdf in the  cd's root directory. For instance, you cannot change directory into the CD drive to run the installer. Also, make sure that you've created a directory such as /usr/local/matlab/ with your license in it.

From the PDF:
create a directory
```
sudo mkdir /usr/local/matlab
```
now move into THIS directory... and copy your license to it
```
cd /usr/local/matlab
sudo cp /from/wherever/license.lic ./license.dat
```
make sure it is executable
```
sudo chmod 755 license.dat
```
put in your disk and run the installer from your current location
```
sudo /media/cdrom/install
```

See if this helps - I actually cannot get past this point either, so i'm probably doing somethin wrong too :confused:

good luck

---

### Post by fraia on 2008-04-09
Search around the forums here... i found this thread:

[http://ubuntuforums.org/showthread.php?p=1543231#post1543231](http://ubuntuforums.org/showthread.php?p=1543231#post1543231)

that has a lot of solutions - including mine:

sudo /cdrom/install* -glnx86 -t

i think the -t option should solve your problem above

---

