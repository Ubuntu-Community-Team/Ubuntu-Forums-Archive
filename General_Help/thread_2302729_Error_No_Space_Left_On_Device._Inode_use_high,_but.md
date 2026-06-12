---
title: "Error: No Space Left On Device. Inode use high, but can't remove old kernel packages."
date: 2015-11-12
forum: General Help
---

### Post by benawhile on 2015-11-12
Hi 
This problem started with the red “no entry” error icon Error BrokenCount>0 which pointed me to package manager, and to use the "broken" filter. This identified a broken kernel package, but when I tried to reinstall, I got : 
 E: Internal Error, No file name for linux-headers-3.13.0-68-generic:i386

Details of the error revealed a disk space problem, although my system shows only 55% used.
Finally I found this similar problem which pointed me to looking at Inode use:

 [http://askubuntu.com/questions/317763/apt-get-no-space-left-on-device-12-04](http://askubuntu.com/questions/317763/apt-get-no-space-left-on-device-12-04)

 Running df -i I got:
```
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda6       1220608 1218493     2115  100% /
none             220447       2   220445    1% /sys/fs/cgroup
udev             215645     522   215123    1% /dev
tmpfs            220447     536   219911    1% /run
none             220447       3   220444    1% /run/lock
none             220447       9   220438    1% /run/shm
none             220447      30   220417    1% /run/user
/dev/sda7      19866984   10910 19856074    1% /media/sda7
```

  And then running dpkg -l linux-image-\* | grep ii 

 I got the list of all the old kernel packages, down to the broken one, 

```
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.68.74                                        i386         Generic Linux kernel image

```

 When I tried to remove the oldest using

 sudo apt-get remove linux-headers-3.13.0-58 

 I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.13.0-58-generic : Depends: linux-headers-3.13.0-58 but it is not going to be installed
 linux-headers-3.13.0-68-generic : Depends: linux-headers-3.13.0-68 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

 So I tried  
 sudo apt-get -f install 
 and got this, which is what Synaptic package Manager was also unable to complete:

 ```
Reading package lists... Done 

 Building dependency tree        
 Reading state information... Done 
 Correcting dependencies... Done 
 The following extra packages will be installed: 
   linux-headers-3.13.0-68 
 The following NEW packages will be installed 
   linux-headers-3.13.0-68 
 0 to upgrade, 1 to newly install, 0 to remove and 25 not to upgrade. 
 3 not fully installed or removed. 
 E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock directory /var/cache/apt/archives/ 

``` 

 I'm not sure if I needed to bother with the sudo apt-get -f install , 

So my question is: Am I using the correct instruction to remove the old kernels? Or have I got completely off track?

---

### Post by grahammechanical on 2015-11-12
I would like to make a couple of points. If I may.

1) At the Grub boot menu we can select Advanced Options for Ubuntu. Then select recovery mode and then at the recovery menu we can select Clean - Try to make free space. It might be useful to do that.

2) It seems to me that if an update tries to install a new kernel and fails due to lack of space, then any attempt to update packages or fix packages will also try to complete the update of the kernel. Producing error messages.

3) If we remove the linux-headers package for a certain kernel then apt-get is also going to complain about unmet dependencies for the other parts related to that kernel. You seem to be in a loop of error messages where fixing unmet dependencies reinstalls the package that you just removed.

We can use Synaptic Package Manager to find the files for a certain kernel image and then with a right click select for Complete Removal. That will remove that particular package and the packages dependant on it.

My advice? Run the Clean command from the recovery mode menu and then use Synaptic Package Manager>Complete Removal to remove each of those older kernels.

Regards.

---

### Post by mörgæs on 2015-11-13
Seeing that you have a 32 bit Buntu running on a 64 bit capable processor you could also do a fresh install of a 64 bit Buntu, erasing the old system in the process.

I would have done that anyway, also if the present system were in a good shape.

---

### Post by benawhile on 2015-11-13
Hmmm. Doesn't seem to have changed anything. although it went through the "clean" cycle.
Same error symbol, go to Synaptic to reinstall  broken package but I still get:
E: Internal Error, No file name for linux-headers-3.13.0-68-generic:i386

Running
```
dpkg -l linux-image-\* | grep ii
```
Still gives long list of old kernels. Tried another reboot but still no joy.
BTW, I may sound as though I understand things but I don't even really know what a kernel is!
As for the 32 or 64 bit, will investigate but I think I had to use 32 bit, maybe something to do with my old system, RAM only 2GB , maybe. 

Regret i have to go away now for weekend and may not be able to get back until Monday unless it's something really simple. Thanks for your responses.

---

### Post by ian-weisser on 2015-11-13
Another simple answer is to use dpkg to uninstall one or more older kernel packages, thereby freeing up the inode space for apt to complete installation of the newer packages.
Then you can easily use apt to remove/autoremove the rest of the old kernels and their dependencies.

Mark your calendar to clean out old kernels a couple times a year before you run out of space or inodes again. Sometimes a simple apt 'autoremove' will do it; sometimes you need to dig a bit.

---

### Post by benawhile on 2015-11-16
Regret things have now got worse before I could fix anything. I can't get to my desktop. When I enter my password and press "enter" I get the empty desktop screen for a second and then a black screen, which resets to the login screen again. My only resources now are Windows XP, (I have dual boot) or the page from which I select the operating system. I have already once tried a cleanup from the advanced load option, but this had no effect. There are the other options with dpkg, repair, etc, although I tried repair and that also didn't seem to work. Another option is that I have an old CD for running Ubuntu 12:04 from. There are various solutions offered using terminal, would it be safe to try these on a 14.04 system using a 12.04 CD? If so, what would you recommend?

---

### Post by eric13 on 2015-11-16
Did you try a  apt-get clean  and apt-get autoremove ??
It did clean many GB on a system I had a look at recently. I could then update the system, partially with install -f to fix all the stuff.

If it does not help, you could re install a x64 Linux as suggested.
2 reasons:
- it will run like a charm on your 2GB dual core X2, as long as you choose a quite light environment.
- you will get better support from the community since the majority is using a x64 variant these days.

Get a 14.04.3 x64 live CD of Ubuntu, or if I may suggest something even lighter and faster, get the Lubtuntu variant (with LXLE desktop).
Do you have a lot of important data or document on your Ubuntu partition?
If yes, use the live CD to create another partition and backup these data on it. 
Then or if not, use this liveCD to test it on your system and install this x64 Linux.

---

### Post by benawhile on 2015-11-16
Thank you eric13. I was hoping for a quick solution, like a fix for the kernel's that I could do from the CD or from the grub menu, but as none is forthcoming, and I appreciate your help nonetheless, I guess I will have to try a reinstall, as it looks like this is what you are suggesting ultimately. I don't remember if I tried apt-get clean, can I run it from my existing 12.04 CD? I also have lubuntu 14.04 on a USB.

---

### Post by benawhile on 2015-11-16
Update. I installed the Lubuntu 14.04 as a temporary workaround. I wonder if the old kernels will start building up again? Will never know what went wrong.

---

### Post by ian-weisser on 2015-11-16
> **benawhile said:**
> I wonder if the old kernels will start building up again? Will never know what went wrong.

The same issue seems likely to recur, unless you occasionally run autoremove. The system makes old kernel packages (and lots of others) *eligible* for autoremove, but doesn't actually run it for you...unless you have the unattended-upgrades package installed. Then it's merely a change to one setting.

---

