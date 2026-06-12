---
title: "Failed to install Nvidia-304"
date: 2018-07-06
forum: General Help
---

### Post by orangebai on 2018-07-06
Hi, I am new to Ubuntu.
My version is 18.0.4.
I try to install Nvidia drivers for my computer. And here are my graphics card info:```

 	 		 			 			 				 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev a1) 
```

 	
 
and I have added repository:
```

sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
sudo apt-get upgrade
```
	
 
I can install Nvidia-390 by:
```
sudo apt-get install nvidia-390 
```
but when I run 
```
nvidia-smi
```

 	
 
it shows "not supported".
I searched and find that my graphic card can only supported by nvidia-304 cause it is a hybrid gpu.
And then I run
```

sudo apt-get install nvidia-304

```
get
```
  	 		 			 			 				Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gvfs : Depends: gvfs-daemons (>= 1.36.1-0ubuntu1)
        Depends: gvfs-daemons (< 1.36.1-0ubuntu1.1~)
 libgtk-3-0 : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                       libwayland-egl1
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. 			 		

```

 	
 
I tried several days but failed to fix it.
Can anyone help me?
Thanks a lot

---

### Post by oldfred on 2018-07-06
Where did you get the info on which nVidia driver.
The 304 is only for older cards/chips.

       Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
This says your card still uses the newest drivers:
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

    
Since you installed incorrect driver, you must totally purge that. Installing a new driver, does not remove old driver and you get conflicts.
       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by wildmanne39 on 2018-07-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by orangebai on 2018-07-06
Sorry for using bad format. I will pay more attention on that!Thx!

---

### Post by orangebai on 2018-07-06
I cannot remember where did I get that info. But I tried nvidia-390 and nvidia-340, both failed and get "not supported" info. So I try to use 304 instead

---

### Post by NM5TF on 2018-07-06
do what oldfred said.....then reboot...

if that doesn't fix it,, try using nouveau instead of nvidia....

---

### Post by enigma9o7 on 2018-07-13
I'm trying to install 304 and having exact same issue.  In my case my video is old, and using nouveau is causing video glitches, which is why I want to try nvidia.

---

### Post by deadflowr on 2018-07-13
nvidia-304 is unmaintained so trying to install it on bionic is a crapshoot.
(They pulled it from the repos, and the ppa version is quite old in relation to the kernel and X server bionic uses:
see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1748000]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1748000") )

My take is if the card really requires the 304 driver then best working bet would be to run a release with a better support stack such as 16.04 (or 16.04.1)
(Do not install from the 16.04.2, or .3, or .4 or .5 point releases of Ubuntu as those will all eventually move up to the current 18.04 kernel and X server stacks which are probably problematic.
Where to get the Ubuntu 16.04.1 release: [http://old-releases.ubuntu.com/releases/16.04.1/]("http://old-releases.ubuntu.com/releases/16.04.1/")

Perhaps, if you're lucky, you can find a mythical kernel patch as mentioned over here: [https://devtalk.nvidia.com/default/topic/1032541/linux/304-137-doesn-t-install-in-ubuntu-18-04-got-removed-from-ubuntu-repositories-/]("https://devtalk.nvidia.com/default/topic/1032541/linux/304-137-doesn-t-install-in-ubuntu-18-04-got-removed-from-ubuntu-repositories-/")
Here's one patch: [https://devtalk.nvidia.com/default/topic/1026876/patch-for-387-34-and-linux-4-15-0-rc1/]("https://devtalk.nvidia.com/default/topic/1026876/patch-for-387-34-and-linux-4-15-0-rc1/")
Which i found through this bug report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1751147]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1751147")
So take it with a large rock of salt.

My rambling two cents.

---

### Post by enigma9o7 on 2018-07-17
Thanks.  This procedure worked for me:
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)

---

### Post by mike.lm on 2019-01-22
> **enigma9o7 said:**
> Thanks.  This procedure worked for me:
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)

I tryed it also. But video file become unable to play.

---

