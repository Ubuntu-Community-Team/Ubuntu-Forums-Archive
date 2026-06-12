---
title: "Running a newer Kernel."
date: 2016-05-06
forum: General Help
---

### Post by izznogooood on 2016-05-06
I could imagine Canonical put serious time in testing Ubuntu´s Kernels. But they are now currently 0.2 versions below the "current". Is there any serious disadvantages of running a 4.6 Kernel (execpt the obvious.) I was running the 4.6-rc2 since release without incident until i reinstalled last week. Now that I´ve made 16.04 my primary system I feel more reluctant. 

Someone once mentioned that APT adapts to the Kernel "among other things" choosing packages accordingly. Is there any documentation on this subject (I cant find any).

---

### Post by nothingspecial on 2016-05-06
The whole point of Ubuntu is to offer a free, modern operating system that anyone can use, and that works. With that in mind you do not get rock solid stable (eg Debian Stable), nor do you get a rolling release (eg Arch). You get a tested set of packages including the kernel.

Of course this is linux, you can do what you want with it. Ubuntu includes, what can reasonably be verified by Canonical and the Ubuntu community, stable software. And they put their name on that.

If you want to run a more up-to-date kernel, go for it. It'll probably be fine. However if things break so be it. (I notice from your sig you know how to mess about with stuff :))

I can't find anything about apt "adapting" either and would be interested to know.

---

### Post by QDR06VV9 on 2016-05-06
> **nothingspecial said:**
> 
I can't find anything about apt "adapting" either and would be interested to know.
Me Too!
I saw that you had replied... hoping for that very same answer.:D

---

### Post by QIII on 2016-05-06
Moved from Ubuntu Development Version.

Xenial has been released.  Yakkety is now the development version.

Cheers!

---

### Post by izznogooood on 2016-05-06
Kernel 4.6 is not ;) (Released)

I ran Xenial from beta 1, but Yak proved to early (for me). ;)
So i know this was the right forum for the right people.  Thank you for your answers.

---

### Post by buzzingrobot on 2016-05-06
The 4.6 RC kernel at the mainline PPA is the latest 4.6 RC, i.e. rc6.  ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/))

Official Ubuntu kernels do not follow the same numbering scheme as the kernels they are based on: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Mainline_kernel_mapping_to_Ubuntu_kernel](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Mainline_kernel_mapping_to_Ubuntu_kernel)

---

### Post by jeremy31 on 2016-05-06
> **runrickus said:**
> Me Too!
I saw that you had replied... hoping for that very same answer.:D

The only time it "adapts" is when you update the HWE(hardware enblement stack)- only possible with an LTS like 12.04, 14.04, and 16.04.

With 14.04 you could update the HWE to Utopic, Vivid, and Wily after the release and then kernel updates and possibly others came from the new HWE.  

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by QDR06VV9 on 2016-05-06
> **jeremy31 said:**
> The only time it "adapts" is when you update the HWE(hardware enblement stack)- only possible with an LTS like 12.04, 14.04, and 16.04.

With 14.04 you could update the HWE to Utopic, Vivid, and Wily after the release and then kernel updates and possibly others came from the new HWE.  

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Good to know... Thanks jeremy31
Regards

---

### Post by nothingspecial on 2016-05-07
Thank you!

---

