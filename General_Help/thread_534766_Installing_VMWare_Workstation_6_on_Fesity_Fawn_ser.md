---
title: "Installing VMWare Workstation 6 on Fesity Fawn server"
date: 2007-08-25
forum: General Help
---

### Post by grasMonst on 2007-08-25
I am trying to install VMware Workstation on Ubuntu Feisty Fawn Server.

I successfully install it, but then when I go to run it via:

/usr/bin/vmware

Nothing happens.  The console just gives me a new blank prompt.

I assume this has something to do with a graphics issue, but I am not sure.

Can anyone help (possibly even someone who has VMware Workstation running on FF server)?

Thanks,
Derek

---

### Post by ocumo on 2007-08-30
> **grasMonst said:**
> 
I successfully install it, but then when I go to run it via:

/usr/bin/vmware

Nothing happens.  The console just gives me a new blank prompt.


Hi Derek,

I like your optimistic view. Your definition of "success" is amusing. To me, when a thing doesn't work, I rather use a somewhat less polite description .... :)

I am in the process of installing VMWare Workstation 6 myself on Feisty Fawn (not a server).  I have just found this [link,]("http://levelsofdetail.kendeeter.com/2007/04/installing_vmware_workstation.html")   which seems promising and quite logic, (although it refers to VMW v5.5.3). What version of VMWare are you installing? Perhaps you would like to give that procedure a try. I will keep researching a little bit before trying it myself. I haven't yet checked this forum or others thoroughly. If I succeed, I'll post it here, if you also are willing to post your experiences.

Good luck,

Ocumo

---

### Post by scxtt on 2007-08-30
what are you trying to accomplish by running "/usr/bin/vmware"?  i use Server myself, and "vmware" is the GUI front end - if you don't have an X environment on your Feisty install, i don't think it's gonna do squat for you ... tho i would expect it to complain about the lack of X ... if you want to start already existing VMs, you should be able to use vmware-cmd - unless Workstation is **that** different ...

---

### Post by ocumo on 2007-08-30
Mmhh... Of course, I didn't think of the fact that grasMonst's Feisty server could be running without an X system.

Well, just in case there is an X, I just would like to contribute to this thread with this additional info, that I found in [this]("http://ubuntuforums.org/showthread.php?t=532553&highlight=vmware+workstation") thread: [http://ubuntuforums.org/showthread.php?t=532553&highlight=vmware+workstation](http://ubuntuforums.org/showthread.php?t=532553&highlight=vmware+workstation)

1.- VMWare Workstation 6 installation on Ubuntu Feisty seems to be pacific, by just running the ./vmware-install.pl script as root, and then when it asks you if you want to configure, say yes - or else you'll need to run later anyway the configure script vmware-configure.pl (also as root).

2.- After this, you should only have to rerun the configure script when your kernel gets updated again. Everytime the kernel is updated, you have to reconfigure.

Now, it is important to mention the two pre-requisites that the VMWare Workstation 6 user guide mentions:

a.- "The real&#8208;time clock function must be compiled into your Linux kernel. "

Which you can easily check with

```
$ grep 'CONFIG_RTC=' /boot/config-$(uname -r)
```

(by the way, as most people know, the $(uname -r) bit will automatically be replaced by the version of the current kernel: in my case, that would be "2.6.20-16-generic")
Which in my case gives this:

```
$ grep 'CONFIG_RTC=' /boot/config-$(uname -r)
CONFIG_RTC=y
```

Since "y" stands here for "yes", it means the real time clock function is included. Another way to check it quickly, is to check if the file /dev/rtc exists, for example like this:

```
$ ls -l /dev/rtc
crw-rw---- 1 root audio 10, 135 2007-08-30 13:50 /dev/rtc
```

So this condition is met (else, you would see a "No such file or directory" kind of message.

b.- "Workstation for Linux requires that the parallel port PC&#8208;style hardware option (CONFIG_PARPORT_PC) be built and loaded as a kernel module (that is, it must be set to m when the kernel is compiled). "

Which you can easily check with
```
$ grep 'CONFIG_PARPORT_PC=' /boot/config-$(uname -r)

```

Here is what I got when I type that command:

```
$ grep 'CONFIG_PARPORT_PC=' /boot/config-$(uname -r)
CONFIG_PARPORT_PC=m
```

So this condition is clearly met too (because the "m" here, means "built as kernel module").

Does anybody else have experience installing Workstation 6 on Feisty? Any caveats or additional advice than the above lines that would be worth mentioning here?

Thanks,

Ocumo

---

### Post by ocumo on 2007-08-30
OK, since no one else has added any information, here I am posting the result of my own successful experience installing VMWare Workstation 6 on Ubuntu Feisty (actually, it was on Kubuntu Feisty).

Obviously, make sure that you read the installation instructions on the VMWare Workstation 6 User Guide.

**But** there are some very important notes that are NOT documented in the instructions, that I have to highlight, if you want to have a smooth and successful installation.

1.- First of all, make sure that your system is compliant with the requirements that I indicated in my previous post ([#4]("http://ubuntuforums.org/showpost.php?p=3279675&postcount=4") above). Use the procedures above if you are not sure, but a standard Ubuntu/Kubuntu Feisty Fawn 7.04 should have the real time clock function compiled in the kernel, which also should have been compiled with the CONFIG_PARPORT_PC=m option.

2.-   The installation script will try to find a suitable pre-compiled vmmon module for your running kernel. **Be aware that if it doesn't find any pre-built module, it will need to compile one. **This was the case for my kernel, (2.6.20-16-generic). But this can ONLY be done successfully if you have installed this two requisites:

[INDENT]a.- The kernel headers
b.- gcc and make[/INDENT]

Let's see in detail these how to fill those gaps:

For the **kernel headers,** you can install them if necessary like this:

1.- Enter the following command:

```
sudo apt-get install linux-source-`uname -r` linux-headers-`uname -r`
```

2.- Decompress the linux-source-2.6.xx.tar.bz2 file, where xx is specific version of your kernel. In this example, in my case it is 2.6.20, but just replace this part with your own version.

```
cd /usr/src/
sudo tar xvjf linux-source-2.6.20.tar.bz2
```

3.- Create a symbolic link to the linux sources. This will ensure that the build process will use the correct sources, minimizing the possibilities of mistakes.

```
sudo ln -s linux-source-2.6.20 linux
```

**Remember:** replace the 2.6.20 part of that command for your own version number, if different.

Now, for the **C compiler (gcc) and make**: you can quickly check if you have them by entering these commands (if the programs are installed, you'll see information about their versions):

```

make --version
gcc --version
```

Make sure you are using the right version of gcc. In order to the script compile the module, you must have the same gcc version that was used to compile your kernel. Currently (Feisty), the Linux kernel is compiled with gcc version 4.1.2, but if you don't know, do this:

```
cat /proc/version
```

That command will tell you which version of gcc was used for compiling your kernel. From that information, you know which version of gcc you need to install (if you need).  If both versions match, then nothing else is necessary. If you simply don't have gcc installed, then install it with 
```

sudo apt-get install gcc-x.y.z
```

where x.y.z is the version number of the gcc used to compile the kernel, per above.

Now, if they don't match, then you need to install gcc-x.y , where x.y are the first two digits from the gcc version used for the kernel, and that is different than your current one, and then tell the system to switch to use that particular gcc version instead of the previously existing one, like this:

[INDENT]/************************************* Example *************************************/

Example: your kernel was compiled with gcc-3.4.x and your gcc is another one
Then, you should do:

```
sudo apt-get install gcc-3.4
export CC=gcc-3.4
```

The last command ensures that from that moment on, any compiling done in this particular
terminal (shell) will use this version of gcc. Remember: only valid for this shell.

/*********************************  End of Example *********************************/[/INDENT]

Now, as long as you have all those pre-requisites fulfilled, then you can proceed with the installation instructions. Just follow them carefully, they are very easy. Remember to accept the defaults for all the questions that have one. If the scrip needs to compile the module and if you have installed things per my above instructions, then it should work fine, it will find the headers and just do the job.

Finally, make sure you take note of all the services that the installer will set up and start. This information is given at the very end of the installation script. You may want to (later) create some script that enables/disables this block of services, for example when you will not be running VMWare workstation, you don't need any of those services running (yes, they are **10** services: it is a lot of useless overhead stuff to your system when not running VMWare).

Good luck,

Ocumo

---

