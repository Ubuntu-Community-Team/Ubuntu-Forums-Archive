---
title: "Ubuntu 14.10 on Asus g750j"
date: 2014-12-20
forum: General Help
---

### Post by k-stefanov87 on 2014-12-20
Hey guys,

I am a new ubuntu and linux overall user, and i still keep my windows 8 in case i stumble to a dead end as this is pretty new field for me.
Right now i have a issue right from the start, and i am unable to find a proper solution yet anywhere on the net.

I have just installed a fresh Ubuntu 14.10 on my pc alongside windows 8, but i used it for like 30 min tops 1h and the machine was very hot, now my machine is pretty powerful gaming rig, and it is not suppose to get hot at all with the turbo fans on the back, can you please tell me if there is a way to control the fans under ubuntu or maybe have them on default work as they are on windows 8 (never had a issue with the fans even if i was playing a high graphic game).

I would really love to find a solution to this issue and if i do i will post it here, or if some one helps me i will be very grateful for the assistance, this will make my transition to ubuntu very smooth :)


Thanks in advance for every one that helps.

---

### Post by oldfred on 2014-12-20
Did you install the correct proprietary video drivers for your system?
I normally suggest installing from Ubuntu repository, but if a very new system you may need to install from ppa to get the newer versions pre-compiled. I know newest nVidia needs that, not sure about AMD.

What chip, motherboard, RAM, and video card do you have?

---

### Post by k-stefanov87 on 2014-12-20
Hey, 
Thanks for your reply 

My machine is powered by: 
Intel Core i7-4700HQ 
8GB (1x 8192MB) - DDR3, 1600Mhz 
NVIDIA GeForce GTX 870M (3GB GDDR5) 

the full model spec of the rig is ASUS G750JS-T4046D

and no i have not installed anything additional as on the asus web page there were no drivers specified for anything else than windows 8 
How to i install from the ubuntu repository or from ppa ? And how to i find exactly what i need ?

Thank you very much!

---

### Post by oldfred on 2014-12-20
While I normally suggest installing the nVidia driver from Ubuntu's repository, it typically is a couple of versions older, depending on Ubuntu version. And your card is too new for the version in repository.
Best not to download from nVidia directly as with every kernel update you have to manually recreate initrd to use video driver as it is not in dpkg.
So then you need to use ppa, and there are several.

 Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

In some cases you need nVidia driver, support software & newest kernel. See some of the discussions in Phoronix.
Several ppa, not sure if one is better than the other, my nVidia card is older and I have not used a ppa.
Any examples with a specific version should be changed to the newest available in the ppa and they usually have very new or even beta versions. Not sure I would install the beta in my working install of Ubuntu.

 14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)
Kernel updater script - also git methods
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

You might want to create another 20 or 25GB / (root) partition and just install 15.04 or 14.10 into that. They will not be LTS and I usually keep a LTS version as my main working install and test others installs in another partition. In your case the newest version may have all the newer kernels & support software and offer a newer nVidia or the newer nVidia driver ppa may work without having to update all the other support software.

Of course good backups are always recommended. And only use Something Else if installing another copy of Ubuntu. And if UEFI backup efi partition also.

---

### Post by k-stefanov87 on 2014-12-20
Ok i will give it a shot, i will just make a fresh copy of my ubuntu and start over so i dont make anything wrong, i will let you know if that works out with the fans, hopefully that will resolve it.


ps: reading all that is like Chinese to me :D will be fun

---

### Post by oldfred on 2014-12-20
If you do another install, be sure to use Something Else to reuse existing / (root) or to create a new /. 
And of the auto installs may say it is overwriting just Ubuntu but may erase entire drive.

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

It should actually be as easy as just adding on of the ppa's that has nvidia and update. 
But I like to give lots of extra detail in case you want to know more. :)

---

### Post by k-stefanov87 on 2014-12-20
Hey,

Fresh install turned out to be much better than the older one, i still struggle with boot freezes, but i figured out a way to go around that i only have to go in to "safe mod" and go back all works fine, maybe it will go away after it fixed some files there, will see.

Figured out how to install skype and google chrome yay for me :P I do believe now the better part of the community is laughing its ass off but that's ok i am new after all :D


Anyways, installing [COLOR=#000000]14.04 drivers for Nvidia GeForce GT 730 desktop board - [/COLOR]
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702) this right now, and so far (before they are installed) the fan speed is on its normal temperature levels, i might have to find some program to check the temperature levels of the rig but so far so good, its cold outside, should be cold inside ;)


Question: do i have to install the rest of the things n the links you sent me or those are just options to chose from ? Also installing the video drives, will i not need some other drivers as well as for the processor etc. ? And will this help with the cooling system ?


Thanks allot again!

---

### Post by oldfred on 2014-12-20
Those mostly were alternative ways to install the same drivers.
Only if just installing driver does not work then installing support software or even newer kernel may be required.

Some users just like to test newer versions before they are available, or have such new hardware that they have to have only the very newest of everything.

---

### Post by k-stefanov87 on 2014-12-20
not for me, i just like things working :) the first one did not really work, trying the official drivers from the web page of nvidia

---

### Post by k-stefanov87 on 2014-12-21
Got it to work somehow, drivers are installed from the official web page! so far so good, no problems, do i need drivers for the intel core i7 ?

---

### Post by oldfred on 2014-12-21
I do not think there are any drivers. Intel has been good about getting necessary changes into the Linux kernel before widespread use of new hardware. It just is then you need newer versions of Linux as older versions usually do not have those updates.

If you installed from nVidia's page, then with every kernel update you have to reconfigure kernel to use the nVidia driver. It is not registered in dpkg for automatically updating it.

---

### Post by k-stefanov87 on 2014-12-22
So basically i have to reinstall my drivers with every ubuntu update right ? Do not think that's a problem if its that simple.


One more question, i have a new problem that occurred yesterday, right now i am testing minecraft on my system if it works property, not sure if its related at all, i even think it has nothing to do with it, but after like 5-15/20 min time on, ubuntu just crashes and the screen freezes basically i cant do anything except i to hard reset the pc, any ideas ?

---

### Post by oldfred on 2014-12-22
Is it overheating?
Hard to analyze intermittent issues. Could be heating issue, could be RAM issue, or some but in software where system gets corrupted.

Do not hard reboot unless that is only choice or that will create even more issues. Remember the Elephants:

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by k-stefanov87 on 2014-12-27
Its not overheating at all to be honest, vents are working like a baws, but it just freezes and nothing works to a point where the only chance is to hard reset it. When i log back i have few errors on my login screen and the again the same thing. Im totally lost now dont know what to do.

---

### Post by oldfred on 2014-12-27
Perhaps boot log shows possible errors or warnings.

Just saw this post, which only lists those with longer times >0.3, You can also review dmesg for errors or warnings:
 Errors over .3 sec by schragge
[http://ubuntuforums.org/showthread.php?t=2258188&p=13194859#post13194859](http://ubuntuforums.org/showthread.php?t=2258188&p=13194859#post13194859)
```
awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg
```

---

