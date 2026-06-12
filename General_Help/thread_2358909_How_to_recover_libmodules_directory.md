---
title: "How to recover /lib/modules/ directory"
date: 2017-04-18
forum: General Help
---

### Post by ubix on 2017-04-18
Hello, everyone!

During a regular update of my Ubuntu **14.04** system the *Software Updater* ran out of space on my **/ (root)** partition initially set up to 10 GB. To fix the update I removed older modules directories with names below **4.4.0-34-generic**.

Unfortunately, *VirtualBox* requires files in **/lib/modules/3.19.0-49-generic/** to function properly. I tried to reinstall the missing **3.19.0-49-generic** directory by running:
```

	apt-get install 3.19.0-49-generic 

```

However this did not work!

Can please anyone tell me how to recover **/lib/modules/3.19.0-49-generic/** directory and files in it.

---

### Post by #&amp;thj^% on 2017-04-18
Well let's see if we can get some more information here...post back the return of :
```
sudo apt autoremove -s
```
The command will not actually do anything... but give us some info.
Please use code tags when pasting back.:)

---

### Post by ubix on 2017-04-18
You must be joking. Anyway, here's the output you wanted:```
#> apt autoremove -s
E: Command line option 's' [from -s] is not known.
#> 
```What would you like to accomplish with autoremove command?

---

### Post by &amp;KyT$0P# on 2017-04-18
I think 1fallen was not joking.  Please try this command instead -
```
apt-get -s autoremove
```

As for VirtualBox, is this system the host or a guest?


* Also, please post the output of this command -
```
uname -a
```


** And, by what method did you remove the older directories in /lib/modules?

---

### Post by ubix on 2017-04-18
**halogen2**, I think you both are joking, what do you wish to accomplish with **autoremove**???. Second, already before your reply I had tried all the permutations of {{ **apt, apt-get, -s**, and **autoremove** }}, the command fails for all of them!

The **uname -a** output is implicitly stated in my original post. But if it will really make a difference, here is the missing part you need, namely my latest update I installed and I'm running is **4.4.0-70-generic** on **x86_64** platform.

---

### Post by &amp;KyT$0P# on 2017-04-18
> **ubix said:**
> **halogen2**, I think you both are joking, what do you wish to accomplish with **autoremove**???
If free space is an issue, and some packages are listed in the simulated autoremove, you can try actually purging at least some of those packages to gain more free space.  The main idea of simulating an autoremove is to check beforehand what those packages are, if any.

Further, on some 14.04 systems, old kernel packages get automatically marked as auto-removable.  If that applies to your system, the autoremove simulation will give us useful information about the kernel packages you don't want.

The command I posted should work, and does work for me.  No idea why it gives you that error.

> But if it will really make a difference, here is the missing part you need, namely my latest update I installed and I'm running is **4.4.0-70-generic** on **x86_64** platform. 
Thanks, it does make a difference.

But if you want further help, please answer the rest of the questions posed to you -
> **halogen2 said:**
> As for VirtualBox, is this system the host or a guest?

...

** And, by what method did you remove the older directories in /lib/modules?

---

### Post by deadflowr on 2017-04-18
> **ubix said:**
> Unfortunately, *VirtualBox* requires files in **/lib/modules/3.19.0-49-generic/** to function properly. I tried to reinstall the missing **3.19.0-49-generic** directory by running:
```

	apt-get install 3.19.0-49-generic 

```

However this did not work!


Not sure what you mean about virtualbox requiring something from an older kernel.
(That seems like something is off with the vbox installed on the system, but that would be another story, I guess...)

Anyway, the files in /lib/modules/kernel-number-version-here are part of the linux-image and linux-image-extra packages, so
```
apt-get install linux-image-3.19.0-49-generic linux-image-extra-3.19.0-49-generic
```
will install the /lib/module/ files.

---

### Post by ubix on 2017-04-19
> **deadflowr said:**
> Not sure what you mean about virtualbox requiring something from an older kernel.
(That seems like something is off with the vbox installed on the system, but that would be another story, I guess...)

Anyway, the files in /lib/modules/kernel-number-version-here are part of the linux-image and linux-image-extra packages, so
```
apt-get install linux-image-3.19.0-49-generic linux-image-extra-3.19.0-49-generic
```
will install the /lib/module/ files.

Thank you **deadflowr**. This seams promissing, however. I am a bit concerned should have it worked. Would it flag "**linux-image-3.19.0-49-generic**" as the active OS, overriding **4.4.0-34-generic**? I am not quite comfortable with GRUB switching different kernel image releases. As you may have guessed your suggestion also didn't exactly work, since I am way passed release **3.x.x.x**. But it is close. Following is what happened:

```
#> apt-get install linux-image-3.19.0-49-generic linux-image-extra-3.19.0-49-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-3.19.0-49-generic is already the newest version.
linux-image-extra-3.19.0-49-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up linux-signed-image-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
cp: cannot stat &#8216;/boot/vmlinuz-3.19.0-49-generic&#8217;: No such file or directory
dpkg: error processing package linux-signed-image-3.19.0-49-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-signed-image-3.19.0-49-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
#>
```

As for the '**/sbin/vboxconfig**' requiring features from some other release, this may be a nasty, hidden bug. I came to that conclusion after '**/sbin/vboxconfig**' blew up, by checking **/var/log/vbox-install.log**, which I post here for your convenience:

```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/5.0.14/source ->
                 /usr/src/vboxhost-5.0.14

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.19.0-49-generic -C /lib/modules/3.19.0-49-generic/build M=/var/lib/dkms/vboxhost/5.0.14/build..........
cleaning build area....

DKMS: build completed.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-49-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-49-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-49-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-49-generic/updates/dkms/

depmod....

DKMS: install completed.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

PS: have no idea why quotes do not show up normally and in italics?  :o

---

### Post by &amp;KyT$0P# on 2017-04-19
That VirtualBox error could be due to missing kernel headers.  Please post the output of this command -
```
dpkg-query -W | grep -P -i '^linux'
```

And again, how did you remove the older directories in [FONT=Courier New]/lib/modules/[/FONT]?  Did you use [FONT=Courier New]apt-get purge[/FONT], [FONT=Courier New]rm[/FONT], or...?

---

### Post by deadflowr on 2017-04-19
> I am a bit concerned should have it worked. Would it flag "linux-image-3.19.0-49-generic" as the active OS, overriding 4.4.0-34-generic? I am not quite comfortable with GRUB switching different kernel image releases. 
It won't.
Grub handles kernels in numerical order, so 4.4 will always be a head of 3.19.
You would have to go to advanced in the grub menu to select the older kernel version, or set grub to default boot into it.

That said you seem to already have the 3.19.0-49 kernel image installed, sans the signed image.
(Not sure what that's about, but you can reinstall kernels with the --reinstall option in apt; ala  *apt-get install --reinstall packagenamehere*)
You might see if running a reinstall pulls everything in properly.

I also see we forgot about the headers package for 3.19.0-49, you need that as well:
```
apt-get install linux-headers-3.19.0-49-generic
```
It's usually what causes those pesky makefile errors seen in the dkms output.

>  have no idea why quotes do not show up normally and in italics?
Use code tags whenever posting the output from a terminal, as code tags retains the formatting.


Personally, not sure how helpful any of this will be.
Good luck, anyway

---

### Post by ubix on 2017-04-20
Thank you to both of you, **halogen2** and **deadflowr**. I managed to install everything I thought was missing. However, **/sbin/vboxconfig ** keeps blowing up with some erratic error messages. I may have damaged kernel-updates-DB by first using regular Unix **rm -fr /lib/modules/3.***, and **apt-get purge [...]** only after I discovered  kernel-updates-DB was out of wack. 

After talking to you guys, I was able to start making some real progress, but it would take much more time I currently have for this. Since I had been planning to upgrade to Ubuntu 16.04 already for a while now, I may just do that instead, and install vBox from scratch trying to preserve my VMs, and indeed change my partitioning scheme doubling space for my root partition.

Thank you guys again for your help, I learned quite a few things from all of you.

---

