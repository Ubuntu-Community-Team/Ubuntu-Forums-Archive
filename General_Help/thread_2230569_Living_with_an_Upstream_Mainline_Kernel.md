---
title: "Living with an Upstream Mainline Kernel"
date: 2014-06-19
forum: General Help
---

### Post by Peter_Brandon on 2014-06-19
So, I moved to 14.04, but have been having problems with 'suspend,' including system crashes, spontaneous suspending, and waking spontaneously after I try to put it into suspend.  I've tried the latest mainline kernel, and it seems to have stopped these problems.  So, I'm wondering how feasible it is to actually use the mainline kernel.  Anyone running off a mainline kernel?  Some issues & ruminations:

When I try to use VirtualBox, I get an error msg that the required modules aren't present (not surprising).  Am guessing the way to fix this is to install the kernel headers and then re-install VB (hopefully without erasing the OS I have currently in it)?

There are over 100 updates that want to get put in place with the new kernel.  If I apply these updates, however, won't they conflict with my non-upstream kernel?  Maybe I should want to keep the non-upstream kernel handy in case, well, software like VirtualBox won't work?  If I don't apply the updates, however, won't that leave security vulnerabilities?  And what about getting security fixes for the kernel itself?

Perhaps I should not get the most spanking new upstream kernel, but the one with the change needed to prevent my bug?  With something closer to what I'm currently running, hopefully it won't take as long before I can get back to the standard kernel.  I believe I know the source of the bug--it's in the MEI driver.  I wonder if there's some way to find out when the MEI driver was changed in upstream kernel versions.

Or perhaps there's some way of patching my kernel so it has the latest MEI driver?  Looks to me like running an upstream kernel for other than testing isn't so easy.

---

### Post by The Spectre on 2014-06-20
To get VirtualBox working again after a Linux Kernel Update just run the following command in Terminal...
 ```
sudo /etc/init.d/vboxdrv setup
```
Ubuntu 14.04 probably will not get a major Linux Kernel Update until the next point release 14.04.1 due at the end of July 2014.

 You could just run the Mainline Kernel you installed until the next point release.

 As fare as getting security updates and improvements that where added to the Linux Kernel you would just have to install the new Kernel. 
So if you installed Linux Kernel v3.15.1 you would need to install v3.15.2 when it is released.

 I always run the latest Mainline Kernel and other then having to run “sudo /etc/init.d/vboxdrv setup” to get VirtualBox running again I haven't had any problems.  
 In fact it straitened out a intermittent issue I was having with the Wi-Fi Card in my Laptop.  

 Some people have problems with their computer booting to a black screen if they are running a Proprietary Video Card Driver after a Kernel Update.
 
 And as for the “ 100 updates” you saw after your Kernel Update I have never had that happen to me.

 Maybe the updates where already available even before the Kernel Update but by coincidence did not show up until after the Kernel Update.

---

### Post by Peter_Brandon on 2014-06-21
Hi The Spectre:

Thank you, thank you, thank you!  You've just clarified how to use a mainline kernel that will solve some big headaches for me--nothing like your computer freezing regularly for the system and / or hard disk to get corrupted.  Incidentally, you were also right that the 100+ updates appeared in the old kernel as well.  Just never have seen that many at one time, so assumed it had something to do w/ upgrading to a kernel that's for the post-14.04 version of Ubuntu.

Very much appreciated.

---

### Post by Peter_Brandon on 2014-06-28
Well, that seemed a bit too easy.  /etc/init.d/vboxdrv doesn't exist on my system, so that doesn't work.  I installed VirtualBox (VB) from synaptic, so perhaps, Spectre, you have a different version?

I tried, as indicated in other posts, sudo apt-get remove/install virtualbox-dkms.  When install runs, I get an error msg that there isn't software for my kernel version.

Am guessing that the solution here would perhaps be to remove the VB I have now and put in a more up to date download from Oracle (assuming that will be ok for the kernel).  But, would prefer to not have to reinstall Windows in VB.  Is there any way for me to, say, save the file used as a drive by VB and put it into a newer instance of VB?

---

### Post by The Spectre on 2014-06-29
> **Peter_Brandon said:**
> Well, that seemed a bit too easy.  /etc/init.d/vboxdrv doesn't exist on my system, so that doesn't work.  I installed VirtualBox (VB) from synaptic, so perhaps, Spectre, you have a different version?

I tried, as indicated in other posts, sudo apt-get remove/install virtualbox-dkms.  When install runs, I get an error msg that there isn't software for my kernel version.

Am guessing that the solution here would perhaps be to remove the VB I have now and put in a more up to date download from Oracle (assuming that will be ok for the kernel).  But, would prefer to not have to reinstall Windows in VB.  Is there any way for me to, say, save the file used as a drive by VB and put it into a newer instance of VB?
I am running the latest version available at the VirtualBox website...
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
 
And the VirtualBox 4.3.12 Oracle VM VirtualBox Extension Pack...
[http://download.virtualbox.org/virtualbox/4.3.12/Oracle_VM_VirtualBox_Extension_Pack-4.3.12-93733.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.12/Oracle_VM_VirtualBox_Extension_Pack-4.3.12-93733.vbox-extpack)

It is only slightly newer 4.3.12 vs. 4.3.10 that is in the Ubuntu Software Center for 14.04 but does have quite a few fixes and changes...
[https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog)

I just updated to Linux Kernel v3.15.2 a couple of days ago and I had to run...
```
sudo /etc/init.d/vboxdrv setup
```
like usual to get VirtualBox working again.
I don't know why it isn't working for you.

Try installing VirtualBox 4.3.12 along with the VirtualBox Extension Pack to see if that straitens it out.
And if needed run this in Terminal again...
```
sudo /etc/init.d/vboxdrv setup
```

You can reuse a VirtualBox .vdi file so you don't have to start from scratch...
[ATTACH=CONFIG]254327[/ATTACH]

---

