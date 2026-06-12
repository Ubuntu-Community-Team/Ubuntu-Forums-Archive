---
title: "Trusty 14.04.1 ISO versus 14.04.2 ISO what you need to know if you don't already."
date: 2015-04-12
forum: General Help
---

### Post by Cavsfan on 2015-04-12
I just thought I'd throw this out there so maybe it might save someone else the trouble I went through. I cleaned my hard drive up and formatted my 14.04 final release ISO and downloaded the 14.04.2 ISO.

The mistake I made was not in re-installing 14.04, _it was in formatting my original 14.04 DVD_ and downloading the 14.04.2 one.

Since my original install had upgraded to 14.04.2 and had the 3.13 kernel I didn't give it a thought. 

But when I installed 14.04.2 from ISO it didn't come with the 3.13  kernel but the 3.16 kernel which makes it only good until 2016. :shock:

[Here is some information.]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support") Kansasnoob had pointed this out to me but it didn't sink in until I actually installed the 14.04.2 ISO and noticed it had the 3.16 kernel.

So, for 2 or more hours I searched high and low for the 14.04.1 ISO and finally found it. Trust me _that ISO is hard to find_! 
I kept seeing 14.04.1 ISOs only to lead to the download of a 14.04.2 ISO.

I Could NOT find anything other than the Ubuntu ISO so I installed Flashback with Compiz (gotta have the eye candy of course) :lol:

I installed it and got the 3.13 kernel back and it's good until 2019! :guitar:

I found the place to download the 14.04.1 ISO if any one is interested right [here]("http://old-releases.ubuntu.com/releases/trusty/").

---

### Post by Keith_Helms on 2015-04-12
What happens when the software updater runs on your 14.04.1 version.   Doesn't it try to install all the updates, including the 3.16 kernel, that would bring you up to the 14.04.2 level anyway?

---

### Post by Cavsfan on 2015-04-12
> **Keith_Helms said:**
> What happens when the software updater runs on your 14.04.1 version.   Doesn't it try to install all the updates, including the 3.16 kernel, that would bring you up to the 14.04.2 level anyway?

No that's the whole point. I was at release 14.04.2 before and am now but have the 3.13 kernel.

As you can see from this link [Here is some information]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support") if you installed from the 14.04.0 or 14.04.1 ISO you will retain the 3.13 kernel and be good to go until 2019.

Besides I never use update-mangler, that's what a friend on this forum used to call it. :p
I put in the ~/.bashrc file these three aliases for all of my updating and do it via CLI every time.
Once you add them you just have to logout and back in.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'
```

**ud** gets me updates, **ud2** gets me kernels and anything else that needs to install new packages along with updated packages 
and **ud3** will remove stuff when I see something that is no longer needed in the output of the other commands.

---

### Post by ajgreeny on 2015-04-12
Cavsfan is quite correct that the 14.04.1 will update uto the 14.04.2 but will not use the 3.16 kernel series unless you manually add the utopic hardware enablement stack packages.

There could be good reasons for doing that if you have some new hardware that is only partly supported by the 3.13 kernel but if your hardware works fine with 3.13 it may be better to avoid the potential for repeat hardware enablement updates again next year.  Unfortunately Cavsfan's link did not work but what I think he was wanting to link to was either [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support) or [http://ubuntuforums.org/showthread.php?t=2267071](http://ubuntuforums.org/showthread.php?t=2267071)

---

### Post by Keith_Helms on 2015-04-12
Should new users be automatically "enrolled" for hardware enablement updates just by downloading the current LTS version?  This sounds like it should be an option when you download Ubuntu.

---

### Post by Cavsfan on 2015-04-12
> **ajgreeny said:**
> Cavsfan is quite correct that the 14.04.1 will update uto the 14.04.2 but will not use the 3.16 kernel series unless you manually add the utopic hardware enablement stack packages.

There could be good reasons for doing that if you have some new hardware that is only partly supported by the 3.13 kernel but if your hardware works fine with 3.13 it may be better to avoid the potential for repeat hardware enablement updates again next year.  Unfortunately Cavsfan's link did not work but what I think he was wanting to link to was either [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support) or [http://ubuntuforums.org/showthread.php?t=2267071](http://ubuntuforums.org/showthread.php?t=2267071)

That's odd both links opened for me to the exact same place. Unless you meant the link in my second post which I just made orange and mentioned that it was in the 1st post.
But I fixed it and both now point to the same spot as your post does.

> **Keith_Helms said:**
> Should new users be automatically "enrolled" for hardware enablement updates just by downloading the current LTS version?  This sounds like it should be an option when you download Ubuntu.

I wouldn't have a clue myself. I have a 6 year old system as you can tell by my signature. But when I installed the 14.04.1 ISO it came with the 3.13.0-32-generic kernel. 

There was a ton of updates and the 3.13.0-49-generic kernel was also in the updates. So I have those two:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"
ii  linux-generic                                         3.13.0.49.56                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.81                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.81                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.49.56                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.81                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.81                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel image

```

---

