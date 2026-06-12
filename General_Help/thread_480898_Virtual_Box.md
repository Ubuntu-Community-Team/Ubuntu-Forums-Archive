---
title: "Virtual Box"
date: 2007-06-21
forum: General Help
---

### Post by shadows85 on 2007-06-21
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root.

How do I fix this? I tried what it says but it only resulted in this:

root@------s-computer-4441:/home/----#  /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/log/vbox-install.log to find out what went wrong
root@------s-computer-4441:/home/-----# 

I'll check back on this, tomorrow, at the moment I'm going to sleep.

---

### Post by trippinnik on 2007-06-22
Ubuntu uses the sudo system.  So instead of issuing commands as root, you use the SuperUser account (probably yours) but type "sudo /etc/init.d/vboxdrv setup" then you'll need to enter your password at the prompt.  Hope this helps.  Let us know how it goes.  If it doesn't work it could be because you're running a custom kernel but I don't think so.

---

### Post by shadows85 on 2007-06-22
> **trippinnik said:**
> Ubuntu uses the sudo system.  So instead of issuing commands as root, you use the SuperUser account (probably yours) but type "sudo /etc/init.d/vboxdrv setup" then you'll need to enter your password at the prompt.  Hope this helps.  Let us know how it goes.  If it doesn't work it could be because you're running a custom kernel but I don't think so.


Hmm no difference..: 


Password:
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ]
 * Recompiling VirtualBox kernel module vboxdrv
 * Look at /var/log/vbox-install.log to find out what went wrong

Custom Kernel, I have no idea what that is, besides I never altered kernel.. and yes I'm using the superuser account.

---

### Post by shadows85 on 2007-06-22
Good God, I waste 5 days on this, and this thing is basically the only thing that will keep me with ubuntu... Im getting sick and tired of wasting my time over this.. and yes I was on different forums until I posted this.

---

### Post by AdamTheCamper on 2007-07-03
Well I have the same problem, and when I've looked into  the 

 vim  /var/log/vbox-install.log

It gave me this... 

 missing destination file operand after `/tmp/vbox.0/Module.symvers'
Try `cp --help' for more information.
Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.


So now I am looking for the kernel sources... gues I'll  have to install the kernel-headers (don't remember the exact name) package as I had to when I was installing VMware the earlyer days...

I'll post how had it gone :)

So try to post the erorcode... and maybe someone helps you more .

---

### Post by AdamTheCamper on 2007-07-03
Ok, i've installed the linux-source package,and everything works :)

Just be careful to install source coresponding to image you are using, 
I had a problem cause of 2.6.20- 15/16 version, I am using 15, but it installs the most recent.

But in synapric you can force version so everything s perfect (for now ;) )

---

### Post by martin_legion on 2007-09-05
I'm having the same problem. The strange thing is that I used virtualbox without needing to install the sources before. I had to reinstall Ubuntu and in the new installation I'm having this problem.
I'm installing the sources right now and I'll see what happens.

Another question: Once I'm done compiling the vbox module, can I uninstall the sources, right?

Thanks.

---

### Post by motin on 2007-10-22
I rolled a custom kernel and got into this problem as well. This is how I solved it:

1. Make sure linux-source is installed
2. Make a symlink to /usr/src/linux-source-2.6.20 called /usr/src/linux
```
ln -s /usr/src/linux-source-2.6.20 /usr/src/linux/
```
3. Copy the Module.symvers from your custom kernel's kernel-headers directory to /usr/src/linux
```
ln -s /usr/src/linux-headers-`uname -r`/Module.symvers /usr/src/linux/
```
4. Cd into /usr/src/linux and run (as root - sudo -s): ```
sudo -s
cd /usr/src/linux
make oldconfig && make prepare && make modules_install
```
5. Then run "make all". This normally takes hours but since it is scripts/mod/modpost that Virtual Box needs, you can quit with Ctrl + C right after:
```
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost

```
which is just in the beginning (takes about 30 seconds)
6. Now you should be able to run "sudo /etc/init.d/vboxdrv setup" without problems.

Cheers!

---

