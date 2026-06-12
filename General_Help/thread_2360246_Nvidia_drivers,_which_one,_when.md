---
title: "Nvidia drivers, which one, when?"
date: 2017-05-02
forum: General Help
---

### Post by russkyca on 2017-05-02
I am always confused or unsure (a better word) of which video driver to use and when in the lifetime of th OS and kernel upgrades.   Some video drivers work 'better' than others with certain/various kernels.

I use a web search (for e.g. google) of nvidia drivers and the Ubuntu version I have installed:  for e.g. 'nvidia driver + Ubuntu 17.04' but of course it's a bit vague and unspecific so every video driver version under the sun comes up in hits

So, I was wondering if there is any thread or section on here that has a discussion or experience discussion about the latest nvidia driver(s).   Notice, I used it in plural form. ;)   For e.g. the last three drivers so for instance:

375.39, 378.13 and current latest stable (beta) driver, 381.   I read that some of these drivers need patches with the 3.10 kernel but which ones?  I am a bit confused.   

Currently, I use nvidia driver version 375.39 with Ubuntu 17.04 and my kernel is 4.10.0-20-generic (uname -r output).  

Besides, some insight and info on what to use with which Ubuntu versions and kernel versions is a 'HOW-TO' for upgrading the nvidia driver.   I think there are a few out there but I don't recall them using instructions to uninstall the current nvidia driver.  I thought you needed to do that.   Also, Nouveau is installed via default on every Ubuntu OS now so is it okay?   As long as it's 'not in use' - you can switch with 'Additional Drivers', there won't be a conflict?   I don't ever see any info or topic about that.   The manual way used to be so complicated.... you would have to type up config lines in the associated config files disabling it but now it seems you can run a few commands to install the nvidia driver of your choice?

E.g.
[http://www.askmetutorials.com/2017/04/install-uninstall-nvidia-driver-38109.html](http://www.askmetutorials.com/2017/04/install-uninstall-nvidia-driver-38109.html)

The one comment so far:  "It didn't work for me."    I think a more elaborate and organized effort to explain how to upgrade drivers and to combine 'what works' (video driver/Ubuntu OS ver./kernel ver.) would benefit everyone and avoid a lot of problems and maybe lessen posts on the forum of so and so drivers didn't work or did this.   I am sure everyone wants 'testers' but this is not organized well.   If I'm wrong, say so but I think you will eventually concede that this is true.   

So, what do you think?

---

### Post by oldfred on 2017-05-02
What video card/chip do you have?
That is the most important requirement, that driver matches card.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Best to install from repository. If you have a very new nVidia card, you may need the newest nVidia driver. Then use the ppa.
       
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
    
 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 


You must uninstall old version before attempting to install a new one. Only one is integrated into the kernel.

I have an old nVidia 640GT and the open source driver seems to work just about as well as nVidia. But I do not game nor push drivers/card to limit. New system now use just the internal Intel video as that is good enough for Internet and most desktop use.

---

### Post by russkyca on 2017-05-02
> **oldfred said:**
> What video card/chip do you have?
That is the most important requirement, that driver matches card.

Best to install from repository. If you have a very new nVidia card, you may need the newest nVidia driver. Then use the ppa.
       
Currently, I have a EVGA GTX 750.   There is support for proprietary drivers with this card.   The question is, what are the steps for trying a 'newer' driver than what is in the repo by default?   The drivers in the Ubuntu-provided repo are often 'older' just for the reason that Nvidia usually provides 'newer' drivers after the release of the newest Ubuntu edition.   Or one might read in the Nvidia dev forum or somewhere else saying try X driver because this bug was fixed or whatever.   Of course, you might read roll back to a previous driver because there's a bug in the X driver.   So, the cycle of removing/uninstalling one driver so you can re-install/install another is required.   So, thus, the question, what is the steps or what is the best way?

I usually notice these web pages or steps or something along this idea:

[http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html](http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html)
[http://tipsonubuntu.com/2017/01/19/new-linux-driver-series-nvidia-378-09-beta-released/](http://tipsonubuntu.com/2017/01/19/new-linux-driver-series-nvidia-378-09-beta-released/)
[www.askmetutorials.com/2016/12/install-uninstall-nvidia-driver-37526.html]("http://www.askmetutorials.com/2016/12/install-uninstall-nvidia-driver-37526.html")
[http://www.askmetutorials.com/2017/04/install-uninstall-nvidia-driver-38109.html](http://www.askmetutorials.com/2017/04/install-uninstall-nvidia-driver-38109.html)

Anyway, are there any universal steps for removal or uninstalling (nvidia) drivers?

It seems these suggested steps keep popping up:
sudo apt-get purge nvidia-current

[https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

There doesn't seem to be as many 'up-to-date' instructions on removal/uninstalling.  There is also two methods for acquiring or installing the driver - from the ppa and from the Nvidia website?  But, Ubuntu, imho, does a great job in having very recent drivers so I am totally satisfied with using the 'ppa method.'  But, if something goes wrong or one encounters a bug or for whatever reason, you want to remove/uninstall the driver - 1) you want to use a newer driver so you need to uninstall a previous driver version; 2) installed driver didn't work or there's a bug or something went wrong in the installation process - maybe you're experiencing the dreading 'black screen' problem.... so you want to remove the driver and 'start over.'

Edit:  I used to have notes for various installation methods...easy ones and the more difficult (manual) method. ;)   They might be outdated now, though.

---

### Post by oldfred on 2017-05-02
Do not use nVidia website. While it has usable drivers they are not reconfigured for use with Ubuntu.
If you use that driver, you have to in effect reinstall with every kernel update as it is not part of dpkg.

 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

Then if you enable ppa, you get a slightly different list as the very newest will be included.
Often almost all the fixes in newest driver are to support the newer cards. So The version released with you card and a few after that are good. Then newer ones may only sometimes help as updates are just for newer cards.
Eventually the driver for your card will be frozen and installing a newer driver may cause issues.  All the features your card supports are in the older driver. Only occasionally a security or other fix may be released to the older version.

---

### Post by mastablasta on 2017-05-03
there is a PPA available for various versions of nvidia drivers. but easiest way is to install a version offered by the application. see if it all works and just leave it at that. the newer version usually contain some specific fixes for certain games. read their release notes, and you will see that for the most part they won't be fixing any major bugs overall, but bugs in certain games, improvements etc.

---

