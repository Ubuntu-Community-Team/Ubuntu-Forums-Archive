---
title: "Ubuntu 18.04 HWE (new kernels)"
date: 2018-05-15
forum: General Help
---

### Post by TheNighthawk on 2018-05-15
Hi,

Could anyone point me out why HWE does not seem to work on Ubuntu (MATE) 18.04 ?

Reading this:  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I would expect that below commands would give me access to more recent mainline kernels?

 sudo apt-get install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04 

What do I get wrong here?

thanks,
br, Koen.

---

### Post by deadflowr on 2018-05-15
Doesn't exist.
Wait a while.
Soon, in a few months, it'll be available first through the -proposed repository. (maybe already?)
HWE come out for all users right around point releases. Starting at the second point release 18.04.2.

---

### Post by monkeybrain20122 on 2018-05-15
You can always download and install kernels from mainline. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by QIII on 2018-05-15
It appears that the HWE kernel for Ubuntu 18.04 is [tentatively scheduled for release in April, 2019]("https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=get&target=18.04.x+Ubuntu+Kernel+Support+Schedule.svg")

I would be conservative and go with the Ubuntu HWE rather than a mainline kernel, as that will have been tested specifically for your release.  Mainline kernels can cause problems with hardware drivers for graphics cards and wireless.  Best to avoid the temptation of going to mainline kernels unless you know what you are doing and you are either testing (such as the RCs) or are very convinced a newer kernel will fix a problem you are encountering.  There is little to be gained by using a newer mainline kernel otherwise.  If security issues arise with the kernel associated with the release you are running, those will be included with your normal updates.

---

### Post by TheNighthawk on 2018-05-17
Hi,

But are HWE kernels not those from mainline Ubuntu? #gettingconfused :)

I understood that HWE is just about getting new mainline kernels from time-to-time rather than to stick with a LTS kernel version for months/years?

br, Koen.

---

### Post by deadflowr on 2018-05-17
> But are HWE kernels not those from mainline Ubuntu? 
No
HWE stacks are built from the follow-up releases of Ubuntu that come after an LTS release and end at the next LTS release.
So the HWE stack that will come next for 18.04 will be based on the default stack of 18.10 (currently TBD)
Then the next HWE stack upgrade will come from the 19.04 release and so on.
And then the last upgraded stack will be based upon whatever comes with the next LTS release 20.04.

Hope that makes sense.

---

### Post by linuxyogi on 2018-05-19
> **deadflowr said:**
> No
HWE stacks are built from the follow-up releases of Ubuntu that come after an LTS release and end at the next LTS release.
So the HWE stack that will come next for 18.04 will be based on the default stack of 18.10 (currently TBD)
Then the next HWE stack upgrade will come from the 19.04 release and so on.
And then the last upgraded stack will be based upon whatever comes with the next LTS release 20.04.

Hope that makes sense.

I am confused about HWE. I posted a thread [here]("https://ubuntuforums.org/showthread.php?t=2390859").

So my question is do I need to do anything special like installing something manually or will with the usual 

```
apt-get update && apt-get dist-upgrade
```  take me to to 18.04.1 ?

---

### Post by mc4man on 2018-05-19
> **linuxyogi said:**
> I am confused about HWE. I posted a thread [here]("https://ubuntuforums.org/showthread.php?t=2390859").

So my question is do I need to do anything special like installing something manually or will with the usual 

```
apt-get update && apt-get dist-upgrade
```  take me to to 18.04.1 ?
point releases have little to do with the lts hardware stack other than if you install from a .2 or later image.
So - 
All .2 or later installs will automatically 'enter' the rolling lts hardware stack path & get auto updated as available up to next lts versions.
Orig. release & .1 installs will not  be on the rolling  lts hardware stack path, to do so one needs to install the meta packages.

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

(early access is possible thru the -edge meta package

---

### Post by linuxyogi on 2018-05-19
@[**[COLOR=#DD4814][B]mc4man**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=320715") 	 
Thanks.

---

