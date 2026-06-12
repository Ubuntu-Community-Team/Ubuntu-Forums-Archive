---
title: "Can someone translate these installation instructions (from computerspeak to"
date: 2008-04-03
forum: General Help
---

### Post by Redrazor39 on 2008-04-03
[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

when you scroll down to "Installation", there are some instructions I don't understand. I have the driver I need, r5u870_1835.fw as well as a folder called r5u870-0.0+svn50 in my home folder that has a whole bunch of drivers and other stuff. I don't really know how to install the stuff because it doesn't give the exact commands for the terminal. Can someone please help me by posting exact commands to type in the terminal from the instructions below? I have the driver r5u870_1835.fw as the driver I need for my webcam but I don't know what to put in the terminal.

[edit] Installation

This section describes the steps required to install the driver from source, so you can get up and running with your favorite webcam-utilising applications!
[edit] Packages

If you're looking on installation instructions from packages, please see r5u870/Packages.
[edit] Prerequisites

You will need:

* Either kernel headers, or complete kernel source for your target kernel. Your kernel must be version 2.6.17 or newer.
* Tools to compile the driver - normally in the build-essentials package or similar. This includes gcc, make, autotools, etc.
* A webcam supported by the driver (see above).
* A brain.

[edit] Compiling

Change the current working directory into the directory in which you have placed the module sources, and execute:
Code:

$ make

You can pass KDIR=<path> to specify a specific kernel location, as such:

Code:

$ make KDIR=/usr/linux-2.6.23-rc1/

[edit] Installing

To install the driver onto the system, simply run:

Code:

# make install

If you ran make with a different kernel path, you should specify it on the command line when installing, too.

Installed modules will be automatically probed for supported devices by the udev coldplug component at boot, and the driver should be automatically loaded on subsequent reboots.

If this is not the case, just add the modulename into a file inside of /etc/modules.d, to load the device on boot.
[edit] Loading the driver

If you installed the driver, you can just run:

Code:

modprobe r5u870

If you wish to load the driver without installing it, you must load the prerequisite modules:

Code:

modprobe usbcam
modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32		(on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:
Code:

insmod r5u870.ko



For extra important information, I am running Ubuntu 7.10 32 bit

If you need the results of posting lspci or lsusb just ask

---

### Post by alexforcefive on 2008-04-03
*EDIT* hang on hang on, I just went on the website. They have a Debian/Ubuntu package. Follow these instructions instead:

> $ sudo apt-get install fakeroot
$ dget -x [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc)
$ cd r5u870-0.0+svn50
$ dpkg-buildpackage -rfakeroot
$ cd ..
$ sudo dpkg -i *.deb
$ sudo m-a a-i r5u870

Just open a terminal, and type each line individually, minus the $

---

### Post by Slushdoot on 2008-04-03
They're all commands to enter into a terminal window.

To begin, you'll need the compiler and associated tools.  Run
sudo apt-get update
then run
sudo apt-get install build-essentials

Download the tarball from the link they provide, right click it when it's done, and select Extract Here

In the terminal type
cd Desktop/r5u870-0.11.0

This will change the working directory to the one you just extracted.

Enter the commands they specify.  Ones preceeded by $ are run as your user, so just paste them in.  Commands prefaced by # have to be preceeded by sudo like so:
sudo make install

---

### Post by Shazaam on 2008-04-03
This will get you what you need using the terminal (Applications>Accessories>Terminal)......
First we need to update apt.....
```
sudo apt-get update
```
When it asks for a password enter your Ubuntu login (user) password (don't worry if you don't see the password, it's there) and hit enter.
```
sudo apt-get install build-essential
```
This code will use apt to get (find and download) and install "build-essential" which has various apps that you need to build from source such as gcc.
Then we will get the dependencies for your app......
```
sudo apt-get install linux-kernel-headers-$(uname -r)
```
This will install the correct kernel headers for your installed kernel (uname-r),
Then cd (change directory) to the location of the makefile. I like to unpack files to my desktop so for me the command would be this....
```
cd /home/myusername/Desktop
```
You probably have the file in a different location so find out where it is and cd to that folder(directory),  then list the contents of that directory to see if the makefile is there by using this command....
```
ls
```
Once you are in the right place execute the required commands....
```
make
```
and then.....
```
make install
```
If it complains about the make install command add sudo to the front of it...
```
sudo make install
```
A few links for you.....

[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.linuxcommand.org/learning_the_shell.php#contents](http://www.linuxcommand.org/learning_the_shell.php#contents)

---

### Post by Slushdoot on 2008-04-03
You win the prize, Shazaam. :D

---

### Post by Redrazor39 on 2008-04-03
wow, thanks! Also, when following Shazaam's instructions, I navigated to the desktop and my file r5u870_1835.fw is listed, I type "make" into the terminal and it says this:

make: *** No targets specified and no makefile found.  Stop.

What do I do now?

---

### Post by Shazaam on 2008-04-03
Redrazor39......
Try the other file (directory)....
```
r5u870-0.0+svn50
```

---

### Post by Shazaam on 2008-04-03
I might have missed a step sorry. Have you cd'd inside the correct file (directory)? When you did the ls command and that listed the directory you were looking for you need to then cd "inside" that one too to get to the makefile. Like drilling down into the file system....
```
cd /home/yourusername/Desktop
ls
cd r5u870_1835.fw
ls
```
Then you should find the file.

---

### Post by Redrazor39 on 2008-04-03
Oh gosh, I'm so sorry, but I still don't have that file. I just went to the download page on the site at this link:

[http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT/](http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT/)

and I clicked on r5u870_1835.fw because my webcam model is the 05ca:1835 one.

Where can I get that file?

---

### Post by Redrazor39 on 2008-04-03
nvm! I found it!
yay!

---

### Post by Shazaam on 2008-04-03
Here is a shorcut to get to directories in your home folder....
```
cd ~/yourdirectory
```
or...
```
cd ~/Desktop
```
that's a tilde.

P.S. I have to go do some chores but I will be back.

---

### Post by Redrazor39 on 2008-04-03
ok

This is what's going on:

I downloaded r5u870_1835.fw, but a long time ago I tried but couldn't figure it out so I still had r5u870-0.0+svn50 and I tried make  and make installing that. I thought it worked, but then I fired up cheese, camorama, and ekiga and none of them worked. I think I installed the driver wrong :(

Ok, what should I download to the desktop from this website [http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT/](http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT/)

to then follow Shazaam's instructions?



Thanks to everyone for their great help and especially to Shazaam for continuing to get me through this :)

---

### Post by Redrazor39 on 2008-04-03
Omg I Got My Webcam Working In Linux Hoooray!!!!!

Thank You So Much Everyone!!!!

---

### Post by Redrazor39 on 2008-04-03
aw man, it works in cheese but not in camorama or cameroid (online)... :(

I wonder if there are any better drivers or if this is the best one in development

---

