---
title: "Ubuntu 14.04.x and Kernel Updates"
date: 2015-08-07
forum: General Help
---

### Post by Graham1 on 2015-08-07
Hi All

With the release of Ubuntu 14.04.3 yesterday, will those already on 14.04.2 be able to update the kernel to 3.19 automatically (via Software Updater) or does this need to be done manually (terminal) or via a fresh install of 14.04.3?

:)

---

### Post by dino99 on 2015-08-07
there are 3 kinds of kernel: the main one, the updated one and the security one; they all are maintained/updated by the system; nothing special to do on the user side

---

### Post by Graham1 on 2015-08-07
> **dino99 said:**
> there are 3 kinds of kernel: the main one, the updated one and the security one; they all are maintained/updated by the system; nothing special to do on the user side

Hi dino99

Thanks for your reply but I'm not sure what you mean by the above :confused:.

Currently, I'm on 3.16.0-45-generic (14.04.2) and 14.04.3 will be on 3.19. So, what I am trying to say is that does the kernel automatically update on each 14.04.x release? 

I have always done a fresh install when a new 14.04.x had been released and was just wondering whether I just needed to let the system update itself for the latest available kernel version.

Thanks 

:)

---

### Post by howefield on 2015-08-07
> **Graham1 said:**
> Hi All

With the release of Ubuntu 14.04.3 yesterday, will those already on 14.04.2 be able to update the kernel to 3.19 automatically (via Software Updater) or does this need to be done manually (terminal) or via a fresh install of 14.04.3?

:)

You will stay on the kernel that you had before 14.04.3 was released. The only way to get the newer kernel is by manually installing. It won't automatically install itself.

The biggest reason for the newer kernel (and the rest of the hardware enablement stack) is to give newer hardware that perhaps needs driver support that isn't available with the original 14.04 release a chance of working, 5 years is a long time to go on the original kernel released back then.  In the main, existing 14.0.x installations would not need it.

---

### Post by Graham1 on 2015-08-07
> **howefield said:**
> You will stay on the kernel that you had before 14.04.3 was released. The only way to get the newer kernel is by manually installing. It won't automatically install itself.

The biggest reason for the newer kernel (and the rest of the hardware enablement stack) is to give newer hardware that perhaps needs driver support that isn't available with the original 14.04 release a chance of working, 5 years is a long time to go on the original kernel released back then.  In the main, existing 14.0.x installations would not need it.

Hi howefield

That makes sense. Are new features (security related) likely to be included as well as "updated" drivers for existing hardware? (allowing more features). 

:)

---

### Post by howefield on 2015-08-07
> **Graham1 said:**
> Hi howefield

That makes sense. Are new features (security related) likely to be included as well as "updated" drivers for existing hardware? (allowing more features). 

:)

If I understand you correctly, then yes new features can be included in newer kernels but couldn't tell you exactly what would be the interesting differences between the kernel that you have and the the 3.19 kernel included in 14.04.3, it's not hard to find elsewhere though :)

Eg, the one that has my attention is the forthcoming &#8203;"no reboot patching" which means a reboot won't be required after a kernel update.

---

### Post by Graham1 on 2015-08-07
> **howefield said:**
> If I understand you correctly, then yes new features can be included in newer kernels but couldn't tell you exactly what would be the interesting differences between the kernel that you have and the the 3.19 kernel included in 14.04.3, it's not hard to find elsewhere though :)

Eg, the one that has my attention is the forthcoming &#8203;"no reboot patching" which means a reboot won't be required after a kernel update.

Don't worry, I'm not asking for differences :). Just curious as to whether an LTS released kernel is more stable (less features added, better tested) than a normal release (like 14.10, 15.04, etc) or both the same.

Yes, I'm looking forward to that feature too. Roll on 16.04...

:)

---

### Post by Bashing-om on 2015-08-07
Graham1; Hello ;

My take on the HWE (HardWare Enablement ) is if it is not broke, do not fix it. I am of the opinion that there is nothing to be gained by installing later release kernels if all your hardware works with the originally installed kernel. With the updates on the later kernels there is the added possibility of a loss of support for older hardware. Then there is the overhead to maintain the short term life cycle of the 15.04/15.10 kernels and Xserver,

My system has no problems:
```

sysop@1404mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
sysop@1404mini:~$ 

sysop@1404mini:~$ uname -r
3.13.0-61-generic
sysop@1404mini:~$

```
with the 3.13 series of kernels and associated Xserver. I will remain on the 3.13 series !

[INDENT][INDENT]is the risk
[INDENT][INDENT][INDENT]worth the gain 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Graham1 on 2015-08-07
> **Bashing-om said:**
> Graham1; Hello ;

My take on the HWE (HardWare Enablement ) is if it is not broke, do not fix it. I am of the opinion that there is nothing to be gained by installing later release kernels if all your hardware works with the originally installed kernel. With the updates on the later kernels there is the added possibility of a loss of support for older hardware. Then there is the overhead to maintain the short term life cycle of the 15.04/15.10 kernels and Xserver,

My system has no problems:
```

sysop@1404mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
sysop@1404mini:~$ 

sysop@1404mini:~$ uname -r
3.13.0-61-generic
sysop@1404mini:~$

```
with the 3.13 series of kernels and associated Xserver. I will remain on the 3.13 series !

[INDENT][INDENT]is the risk
[INDENT][INDENT][INDENT]worth the gain 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Hi Bashing-om

Well, I took the gamble and installed 14.04.3 anyway (taking a backup first). The temptation was too much :grin:. TBH, the overall system does seem alot quicker, which is weird, as I wasn't expecting it to be (running on a solid state drive). 

I just can't believe how quick you can get a Ubuntu system up and running (plus take a backup prior/post installation) compared to doing the same on a Windows system. 

:)

---

### Post by Bashing-om on 2015-08-07
Graham1; :)

All to the good .

Yes ! Agreed, once you are over the learning curve hump, this OS is a joy to work with. Thousands of people constantly going over the code make it so.

Though I have some nostalgia from the old releases, 'buntu
[INDENT][INDENT][INDENT]just keeps getting better
[/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2015-08-07
BTW if all you want is a newer kernel just grab it from mainline.[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) If works, keep it. If not, log into the original kernel and delete it. I have been running mainline kernels for months in Trusty which fixed a problem with vlc freezing with vaapi.

---

