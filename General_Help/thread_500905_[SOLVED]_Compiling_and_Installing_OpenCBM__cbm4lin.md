---
title: "[SOLVED] Compiling and Installing OpenCBM / cbm4linux"
date: 2007-07-14
forum: General Help
---

### Post by myrddinemrys on 2007-07-14
On my Feisty machine, I've been trying to compile and install OpenCBM for linux according to these instructions here:

[http://opencbm.trikaliotis.net/opencbm-8.html]("http://opencbm.trikaliotis.net/opencbm-8.html")

OpenCBM is a small set of commandline utilities for transferring info from old Commodore computers/drives to a modern PC.  I've used the DOS/Windows utils successfully in the past, but now that I'm trying to be 100% Ubuntu, I need to compile/install the linux version.  It doesn't exist in the Ubuntu repos, unfortunately.

I've got 'build-essential' installed, and I've successfully compiled/installed some well-documented things in the past (ATI drivers, etc) but this app has me baffled.

I extract the downloaded 'opencbm-0.4.0.tar.gz' file to my home dir, open a terminal inside the 'opencbm-0.4.0' dir, and type:

```
make -f LINUX/Makefile
```

and I get this error:

> make[1]: Entering directory `/home/myrddin/opencbm-0.4.0/sys/linux'
ln -s LINUX/Makefile Makefile
make -C `for d in {/lib/modules/\`uname -r\`/build,/usr/src/linux}; do test -d $d && echo $d; done | head -n 1` here=`pwd` CBM4LINUX_KERNEL_FLAGS= SUBDIRS=`pwd` modules
make: Entering an unknown directory
make: *** here=/home/myrddin/opencbm-0.4.0/sys/linux: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [cbm.o] Error 2
make[1]: Leaving directory `/home/myrddin/opencbm-0.4.0/sys/linux'
make: *** [all] Error 1

I'm also attaching the entire .tar.gz source package file to assist.  The source package (751k) can also be downloaded from here:

[http://sourceforge.net/project/showfiles.php?group_id=122047]("http://sourceforge.net/project/showfiles.php?group_id=122047")

Alternatively, if you can get it compiled into a .deb file that would be cool, but ultimately I'd like to learn how to do it myself so I can 'give back' someday.

Thanks for any help you can provide.

---

### Post by pcollins74 on 2007-07-21
Hello,

i have the some problem :(
Any idea?

bye
pcollins

---

### Post by myrddinemrys on 2007-07-27
Still waiting a response.

Also, does anyone know how to maybe get Canonical to add OpenCBM to one of the Ubuntu repositories?  That would be awesome.  There are currently no Commodore transfer programs in the Ubuntu repositories that can use the popular "X1541" series of cables.

---

### Post by FrankVdb on 2007-10-22
What do you do with the Commodore files? Is there a good emulator for Linux?

---

### Post by jmail524 on 2007-11-19
Any new developments on this issue?

I also cannot compile OpenCBM / cbm4linux without errors in Ubuntu Gutsy AMD64. I would really like to backup my C64 stuff. (I'm now finding that some of my disks are starting to fail.)

As far as emulators go, V.I.C.E. seems to work pretty well.

---

### Post by myrddinemrys on 2008-01-29
I've successfully compiled the latest version OpenCBM (0.4.2a).  I haven't yet had a chance to pull out my disks and 1571 drive yet to try it, but compiling and installing worked.  Here's what I did:

First there are a few dependencies to take care of:```
sudo aptitude install build-essential linuxdoc-tools linuxdoc-tools-info linuxdoc-tools-latex linuxdoc-tools-text
```

Next, after downloading and unzipping the **opencbm-0.4.2a-src.zip** file located on [this page]("http://sourceforge.net/project/showfiles.php?group_id=122047") to a folder inside your home folder (I used ~/opencbm/), make sure that all current [patches]("http://sourceforge.net/tracker/?group_id=122047&atid=692221") are applied to your source files.

Then it's just a matter of opening up a terminal inside the folder where your source files are, and following the install instructions found [here]("http://opencbm.trikaliotis.net/opencbm-8.html"), under the heading "Compilation."  In Ubuntu-specific terms, it's basically```
make -f LINUX/Makefile
sudo make -f LINUX/Makefile dev
sudo make -f LINUX/Makefile install
```

A note for the impatient (like myself): toward the end of the 1st install command listed above, the script will issue a command that appears to hang for several minutes.  What it's actually doing is generating a PDF help file -- but it takes a while.  Don't stop it.  It'll finish.  It's got more work to do after that, so don't cut it short.

So those are the steps I took to get it to compile and install.  Like I said before, I have not yet had time to give it a test (I anticipate some problems there too).  However if you try it out before I do, be sure to let us all know any problems or successes you encounter!

Thanks

---

### Post by myrddinemrys on 2008-06-08
After following the steps in my previous post, you should have a successful install of OpenCBM.  Getting it working requires just a few more steps.  The series of commands below are from the OpenCBM [documentation]("http://opencbm.trikaliotis.net/opencbm-8.html") under **Loading the Module**, but slightly modified to be Ubuntu-specific.

First, make sure your Commodore drive is connected with whatever X1541 cable you're using, and turned on.  Then issue these commands:
```
sudo depmod
sudo modprobe parport
sudo rmmod lp
sudo modprobe cbm
```

After a few seconds (maybe 5-10) you should be ready to go.  Type```
cbmctrl detect
```to test it out.

Please understand, the new device "/dev/cbm" disappears after a shutdown or reboot.  I'm sure there's a way to make it persistent, but for my own sporadic use its behavior is fine.  Therefore, whenever you need to use OpenCBM, just do this:

1. Log in and open up a terminal.
2. Go to your OpenCBM directory (the one you installed from), i.e. Type "cd ~/opencbm"
3. Connect and turn on your Commodore drive.
4. Type the following commands:```
sudo make -f LINUX//Makefile dev
sudo rmmod lp
sudo modprobe cbm
```
5. Enjoy OpenCBM!

For the curious:

The reason I include "sudo rmmod lp" is because I discovered that the OpenCBM module would not load because it could not get exclusive access to the parallel port.  After getting an error after the "sudo modprobe cbm" step, I typed:```
dmesg
```which gave a more descriptive error:
> parport0: cannot grant exclusive access for device cbm
cbm_init: could not register with parallel portWith help from the troubleshooting section of the OpenCBM documentation, I figured out the module "lp" was tying up the port.  So issuing "sudo rmmod lp" freed up the port for OpenCBM to use exclusively.

Anyway, it feels good to take this item off my list of apps I still need Windows for!

---

### Post by jmail524 on 2008-07-13
Thanks myrddinemrys,

Your instructions worked perfectly for me.

Thanks.
Brian

---

