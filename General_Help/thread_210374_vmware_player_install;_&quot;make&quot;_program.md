---
title: "vmware player install; &quot;make&quot; program"
date: 2006-07-06
forum: General Help
---

### Post by el_ricardo on 2006-07-06
hello, I have just embarked on trying to get my windows install running under vmware, i had a go at using qemu, but i don't want to have to install ANOTHER copy of windows, i just want to boot an existing copy off an existing partition!

my problem lies in the installation of vmware player, i get to a stage in the installation where i am told:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] 
```

so i go with "yes", and i'm given this:

```
Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes] y

What is the location of the "make" program on your machine?
ricardo@ricardo-desktop:/tmp/vmware-player-distrib$

```

where the hell is my "make" program?

I installed the vmware player kernal modules from the synaptic package manager, so i'm guessing they're out of date, or the wrong thing completely, or i've missed something crucial, i am afterall still quite new to the world of linux

---

### Post by mlind on 2006-07-06
```

sudo aptitude install build-essential

```

?

---

### Post by el_ricardo on 2006-07-07
ok, got a little further with the help of an older thread on the forum, got a new error message now:

```
Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in
the "/tmp/vmware-config2" directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

this is getting ridiculous

---

### Post by Hallavej on 2006-07-07
Strange that that the kernel modules from synaptic does not work. They worked for me. To build your own I think you need kernel header:

sudo apt-get install linux-headers-`uname -r`

---

### Post by el_ricardo on 2006-07-07
yeah i got the necessary modules using that, i've got a bit further now, because i realised it was trying to untar the wrong file, because there was a seperate vmware directory as well as the vmware-**player** directory where there was the same file (vmmon.tar) so i copied that file to the correct directory and the install completed no problem, but i still can't open vmware player! i open it from the terminal and it tells me i have to run the config script again (the one that just completed having fixed the errors!) so i have no idea what to do!

---

