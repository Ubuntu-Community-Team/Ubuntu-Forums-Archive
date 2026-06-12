---
title: "How to update Nvidia driver?"
date: 2008-02-12
forum: General Help
---

### Post by warnec on 2008-02-12
Hello. Firstly, I wanted to say that my post is different from many others, because restricted drivers manager did not recognize my 8800 GTS 512, so I installed 169.07 driver from nVidia website. It was hard. I had to move to command line interface, install some libc6 development packages and linux headers, andi finally did it. But the driver had some serious bug. My GPU fan was at full speed all the time. Now, I see 169.09 driver is released, with this error fixed. Can I somehow update the driver, or do I have to remove 169.07 first? If so, how do I do this?

Ubuntu 7.10.

---

### Post by kpkeerthi on 2008-02-12
[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

Upgrade (remove envy and install again) to the newer version. Run envy and select the option to install nvidia driver. It should get you 169.09.

---

### Post by PmDematagoda on 2008-02-12
You can just download the driver from the Nvidia web site and install it over the older driver, no preliminary configuration is necessary.

---

### Post by warnec on 2008-02-12
Never mind, before you replied, I already reformatted the system xD. Thx for your help anyway. GPU is now really quiet.

---

