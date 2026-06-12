---
title: "Minor update failed, can't finish because not enough disk space"
date: 2016-01-15
forum: General Help
---

### Post by altesk on 2016-01-15
I have Ubuntu 14.04 LTS and my kernel is 3.13.0.74.80. My system appears to want to update to 3.13.0.74.118. My guess is that I ran Software Updater and it failed to complete this minor update.

At the top of my computer's screen, in that status bar, there is an icon (red circle with white horizontal line inside). Clicking the red circle shows a message, An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies

When I run either Ubuntu Software Center or Synaptic Package Manager, it won't let me remove software or packages (to free some hard drive space) because it insists that the kernel update be completed. But I can't complete the update, apparently because I need more free hard drive space.

I still have this problem even when booting in recovery mode or in the previous kernel version (3.13.0.73).

I tried this in Terminal:
```
sudo apt-get autoremove
```
but it said:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-74-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

I also tried this:
```
sudo apt-get install -f
but it said:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libdb5.1 libmpdec2 libquvi-scripts libquvi7
  libupstart1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.13.0-74-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-74-generic
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
2 not fully installed or removed.
Need to get 690 kB of archives.
After this operation, 13.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-74-generic i386 3.13.0-74.118 [690 kB]
Fetched 690 kB in 0s (911 kB/s)                     
(Reading database ... 805830 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-74-generic_3.13.0-74.118_i386.deb ...
Unpacking linux-headers-3.13.0-74-generic (3.13.0-74.118) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-74-generic_3.13.0-74.118_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-74-generic/include/config/sensors/adt7310.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-74-generic/include/config/sensors/adt7310.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-74-generic_3.13.0-74.118_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I escape from this trap? Thank you very much for your guidance.

---

### Post by Dreamer Fithp Apprentice on 2016-01-15
I'd boot from another partition or a live disk, and look for some files that can be deleted or moved to some other partition or media, or even uploaded to some some online storage facility. But remember to delete them, not just send them to the trash. I don't know what you use for a graphical file browser but I think they pretty much all follow the convention that highlighting the file, holding down, shift, and pressing del, will delete the file. Or you can use "rm filename" or "rm -r directoryname" from the command line. Be careful. You could just delete the trash bins themselves, if you have trouble doing it the "right" way. That may cause minor problems later, but nothing serious or unfixable. Then reboot and proceed.

---

### Post by grahammechanical on 2016-01-15
You can try at the boot menu to select Advanced options for Ubuntu and then load a recovery mode kernel. At the recovery menu select Clean. That will run 2 commands - clean & autoremove. The second command may remove at least one old kernel and thus allow the updated kernel to be installed.

Do you have a boot partition? It you do, then you should run autoremove regularly.

Regards.

---

### Post by ian-weisser on 2016-01-15
This seems like bug [LP #1357093]("https://bugs.launchpad.net/bugs/1357093").

There is a [simple process to workaround the bug]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels") and get your system working again.
After you are up and running again, you must do [easy periodic maintenance]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Regular_Maintenance") to keep the problem from recurring.

---

### Post by Bucky Ball on 2016-01-16
*Thread moved to **General Help**.*

Open a terminal. 

> uname -a

Make a note of the kernel you are using. Open Synaptic Package Manager. Search for 'linux-image'. Hit the 'installed' tab a couple of times to check what linux-images you have installed. Apart from the current kernel number and the one before it, 'completely remove' the other linux-images (right click the image and you'll see that option). When finished, run the 'sudo apt-get autoremove' command in the terminal.

Reboot and try and update.

---

### Post by altesk on 2016-01-16
> **ian-weisser said:**
> This seems like bug [LP #1357093]("https://bugs.launchpad.net/bugs/1357093").

There is a [simple process to workaround the bug]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels") and get your system working again.
After you are up and running again, you must do [easy periodic maintenance]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Regular_Maintenance") to keep the problem from recurring.

That workaround, that you linked to, worked great. I used that remove command for a bunch of old kernel packages, hoping to free up enough hard disk space.

Then I launched Synaptic Package Manager. The failed Ubuntu system update was already selected, so I simply clicked the Apply button, and the update appears to have installed. While in Synaptic, I looked for more old kernel files, marked them for removal, and again clicked the Apply button.

Some documentation I saw seemed to suggest that removing old kernels can be automated. But I fear it wouldn't be useful because I want to save the previous two versions of kernel also; I wish Ubuntu would provide a way to automate that.

Thanks very much to Ian Weisser for that hint.

---

### Post by mörgæs on 2016-01-16
Good, please mark the thread 'solved'.

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
> **altesk said:**
> I want to save the previous two versions of kernel also; I wish Ubuntu would provide a way to automate that.It does. I'm hazy on the details. I use a script I cobbled together from commands I mostly got here. I forget now whether I started doing it that way because there was something I didn't like about the standard mechanism (possibly it depended on things I didn't want to install) or if maybe it hadn't been invented yet. But I'm pretty sure I've read that it HAS been automated now and that how many kernels and associated files are retained is configurable. Furthermore, I THINK I've read that the default number of old kernels to retain is 2. A little time with a search engine (I suggest startpage.com - like google minus the evil) and you'll probably find the details.

BTW, if you do this manually, and all you remove is the old kernels, you might be leaving useless companion files. It may get them automatically, but if it doesn't - get everything with the same version number - the easiest way to do this with synaptic is to right click on the one you're going to remove, click properties, copy the version number (like "3.13.0-73"), close properties, click search, make sure the "look in" field is set to either "name" or "name and description", and search that number. Look at the results closely, because it is never good policy to uninstall something blindly following instructions. But I think you'll find all the results are dead weight if you are removing that kernel. You'll find a set of files with the same version number somewhat like this:

linux-headers-3.13.0-73
linux-headers-3.13.0-73-generic
linux-headers-3.13.0-73-lowlatency
linux-image-3.13.0-73-generic
linux-image-3.13.0-73-lowlatency
linux-image-extra-3.13.0-73-generic
linux-tools-3.13.0-73
linux-tools-3.13.0-73-generic
linux-tools-3.13.0-73-lowlatency

If you are removing the kernel with that version number, AFAIK, there is no reason not to remove all of them.  DO, I repeat, DO make sure you don't uninstall the kernel you are actually running.

You might also take a look at the packages Bleachbit & Fslint.

---

