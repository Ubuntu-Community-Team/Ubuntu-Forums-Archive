---
title: "how to install Amd proprietary drivers after having Nvidia drivers installed"
date: 2016-06-01
forum: General Help
---

### Post by Chelidze on 2016-06-01
So i have Nvidia pc and i am sick and tired of having good driver epxiriance under linux so now i want to install amd proprietary drivers for HD6870 (yes my nvidia card just blew up and i had this card lying around)

When i opened additional hardware it didn't showed any options to install, so what can i do here ??

I know amd drivers are prone to braking so i am ok with stable tested by canonical release but if there is no other option i will be ok if i will have to download it from the amd website.
No ppa as i understand right ?

One more thing i am using 16.04

---

### Post by deadflowr on 2016-06-01
Well, there are no AMD proprietary drivers for 16.04.

Simple as that.

They forewarned about the issue in the [Release Notes]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes"):
> fglrx

The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience.

When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)



So not much more you can do.

---

### Post by Chelidze on 2016-06-01
> **deadflowr said:**
> Well, there are no AMD proprietary drivers for 16.04.

Simple as that.

They forewarned about the issue in the [Release Notes]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes"):


So not much more you can do.

This is why AMD is going bankrupt so i can't even grab it form their website?

---

### Post by QIII on 2016-06-01
AMD is going bankrupt?

That's too bad, since fglrx is not included in 16.04 because AMD and Canonical are working very closely together to finish the AMDGPU and AMDGPU-Pro drivers to improve support.

---

### Post by Chelidze on 2016-06-01
Have you seen amd's stock price yes they are going bankrupt, so you want to tell me that i am good with amd open source drivers ?? but how do i enable them and get rid of nvidia proprietary drivers ? Or shouldn't it say that i am using open-source drivers.

---

### Post by X-RED_Tech on 2016-06-01
> **QIII said:**
> AMD and Canonical are working very closely together to finish the AMDGPU and AMDGPU-Pro drivers to improve support.

So they say... I can only attest good results in a couple of entry level AMD graphics so far, one notebook and one old desktop. Something similar to the Catalyst CC would be nice though but Intel doesn't have one either. That's probably why both always lag behind Nvidia. Both enjoy a more "equal" field in Windows and even Mac to some extend but not in linux.

---

### Post by Chelidze on 2016-06-01
Does anyone knows how to fix this, well i am not sure if it needs fixing but i have a hunch that there should be more options here

<Removed Big Image added as an Attchment>



Ok this is the command i used to remove nvidia drivers

```
sudo apt-get remove --purge nvidia-*


```

and 
```

sudo apt-get autoremove
```

So far i didn't get a blank screen or unsupported resolution that i cant change (might be because i am using xfce) however still no option to use any other drivers in options.

---

### Post by QIII on 2016-06-01
Uninstalling the NVIDIA driver is entirely independent of anything to do with AMD or its stock prices.

As far as AMD drivers go, with 16.04 the two driver choices are Radeon and AMDGPU.  Which of the two is used will be determined by the OS based on which is supported by the hardware.

---

### Post by Chelidze on 2016-06-01
> **QIII said:**
> Uninstalling the NVIDIA driver is entirely independent of anything to do with AMD or its stock prices.

As far as AMD drivers go, with 16.04 the two driver choices are Radeon and AMDGPU.  Which of the two is used will be determined by the OS based on which is supported by the hardware.

Well i am doing what windows user would do, if you don't uninstall nvidia drivers from windows system you can't install amd drivers on the system because they system can't recognize the drivers. So i though that would be the same issue but it didn't work shouldn't it show me more options in the additional drivers or in 16.04 it doesn't for amd drivers 

Here is my amd net book (15.10)

<Snip Removed big in line picture>

Here is what i see on (16.04 that nvidia drivers previously installed)

<Snip Removed big in line picture>



Is this normal ??  for 16.04

---

### Post by QIII on 2016-06-01
Linux users, like Windows users, should uninstall one OEM's driver before installing the other OEM's driver.  There is no surprise in that.

15.10 != 16.04.  Again, 16.04-will use either Radeon or AMDGPU as it determines based on which is supported by the hardware.  Fglrx is not included, so there is no additional driver to display.

You have two completely different questions here:

How do I uninstall the NVIDIA driver?

Is there another choice of drivers for AMD?

---

### Post by Chelidze on 2016-06-01
> **QIII said:**
> Linux users, like Windows users, should uninstall one OEM's driver before installing the other OEM's driver.  There is no surprise in that.

15.10 != 16.04.  Again, 16.04-will use either Radeon or AMDGPU as it determines based on which is supported by the hardware.  Fglrx is not included, so there is no additional driver to display.

You have two completely different questions here:

How do I uninstall the NVIDIA driver?

Is there another choice of drivers for AMD?

Well my original question was how to get amd proprietary drivers for my system a system which was previously running nvidia drivers. 
I had this question because from my experience on windows it is never that easy to change vendors. 
So with that knowledge and knowledge that amd drivers under linux is a freak show i thought that i should have asked this question to more experienced users.
So if there isn't amd drivers for 16.04 and it automatically reverts to open-source drivers then there is nothing i can do.

---

### Post by QDR06VV9 on 2016-06-01
@ Chelidze please use the Attachment option to post big Images it helps others that have low bandwidth or visually impaired.
Thanks

---

### Post by Chelidze on 2016-06-01
> **runrickus said:**
> @ Chelidze please use the Attachment option to post big Images it helps others that have low bandwidth or visually impaired.
Thanks

Never!!!!!!! Sure sorry about that, "visually impaired" are you serious about this or just joking if you are serious i really feel bad about this, i apologize.


Well found this [article]("http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04") that supports this forums users statements, so there isn't any amd proprietary driver for 16.04 So guess everything is ok, if you can call using bad drivers inferior version :D even though i give up about this i can't call this problem solved.

---

### Post by QIII on 2016-06-01
The "inferior" AMDGPU driver, even without the AMDGPU-Pro overlay, demonstrates performance superior to fglrx on my R9 380X.

---

### Post by Chelidze on 2016-06-01
> **QIII said:**
> The "inferior" AMDGPU driver, even without the AMDGPU-Pro overlay, demonstrates performance superior to fglrx on my R9 380X.

Well if you look at this [benchmark]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=6") proprietary drivers are still mostly outperforming the open source drivers but it is good to know that they aren't as bad as i originally was lat to believe

---

### Post by mastablasta on 2016-06-02
> **Chelidze said:**
> Well if you look at this [benchmark]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=6") proprietary drivers are still mostly outperforming the open source drivers but it is good to know that they aren't as bad as i originally was lat to believe

that benchmark is form march. AMD is involved in development of AMDGPU and the aim is to have as good as fglrx or better by the second half of the year.onyl new GPU's are supported by this driver and older moved to legacy so fo rthem only the radeonHD driver where AMD was only slightly involved is the option. 

AMDGPU will probably move with fast pace development, since AMD wants to support Linux and there wont' be any closed soruce drivers anymore.

---

### Post by Chelidze on 2016-06-02
> **mastablasta said:**
> that benchmark is form march. AMD is involved in development of AMDGPU and the aim is to have as good as fglrx or better by the second half of the year.onyl new GPU's are supported by this driver and older moved to legacy so fo rthem only the radeonHD driver where AMD was only slightly involved is the option. 

AMDGPU will probably move with fast pace development, since AMD wants to support Linux and there wont' be any closed soruce drivers anymore.

Well if amd is getting rid of proprietary drivers and making open-source drivers as good or better then that sounds fantastic.

---

### Post by grahammechanical on 2016-06-02
To avoid confusion.

On Ubuntu the way to replace video adapters, especially if we are changing manufacturers, is to use Additional Drivers to revert to an open source video driver before replacing the video card. Then to remove the old driver (which may not support a newer video card even if it is by the same manufacturer) we run autoremove or the purge command.

Removing the proprietary video driver is not absolutely necessary. The driver is not activated/installed. It is just taking up space on the hard disk. Nothing more than that.

If we fail to revert to using an open source video driver before changing video adapters then Linux/Ubuntu will often come to our rescue by loading with an open source video driver called llvmpipe. The main purpose of llvmpipe is to give the user an approximation of Unity 3D on video adapters that are not capable of running Unity 3D. But it is also used as a fall back video driver if there are video driver conflicts.

Then if we want to use a proprietary video driver we install one through Additional Drivers. Installing a proprietary video driver will download software from the internet. Uninstalling a proprietary video driver will not delete or remove the software of the driver from the hard drive. If that was done and we want to try the proprietary driver again it would have to be downloaded again.

It just so happens that AMD is not providing proprietary video drivers for Ubuntu 16.04 at this time because Ubuntu 16.04 is using a version of the X server that the AMD proprietary video drivers are not compatible  with. And AMD does not want to do the work to bring compliance. Perhaps they are thinking that X server is going the way of the Dodo and it is better to have open source video drivers that are compatible with future Linux display servers and where Linux community developers can participate in development work.

Regards

---

### Post by Chelidze on 2016-06-03
> **grahammechanical said:**
> To avoid confusion.

On Ubuntu the way to replace video adapters, especially if we are changing manufacturers, is to use Additional Drivers to revert to an open source video driver before replacing the video card. Then to remove the old driver (which may not support a newer video card even if it is by the same manufacturer) we run autoremove or the purge command.

Removing the proprietary video driver is not absolutely necessary. The driver is not activated/installed. It is just taking up space on the hard disk. Nothing more than that.

If we fail to revert to using an open source video driver before changing video adapters then Linux/Ubuntu will often come to our rescue by loading with an open source video driver called llvmpipe. The main purpose of llvmpipe is to give the user an approximation of Unity 3D on video adapters that are not capable of running Unity 3D. But it is also used as a fall back video driver if there are video driver conflicts.

Then if we want to use a proprietary video driver we install one through Additional Drivers. Installing a proprietary video driver will download software from the internet. Uninstalling a proprietary video driver will not delete or remove the software of the driver from the hard drive. If that was done and we want to try the proprietary driver again it would have to be downloaded again.

It just so happens that AMD is not providing proprietary video drivers for Ubuntu 16.04 at this time because Ubuntu 16.04 is using a version of the X server that the AMD proprietary video drivers are not compatible  with. And AMD does not want to do the work to bring compliance. Perhaps they are thinking that X server is going the way of the Dodo and it is better to have open source video drivers that are compatible with future Linux display servers and where Linux community developers can participate in development work.

Regards


Thank you very much for providing detailed explanation

---

