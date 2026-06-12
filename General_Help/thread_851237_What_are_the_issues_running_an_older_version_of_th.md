---
title: "What are the issues running an older version of the kernel"
date: 2008-07-06
forum: General Help
---

### Post by TonyGould on 2008-07-06
Hi,

It seems like I can edit menu.list to boot to an older kernel version if I have trouble with a new one. For example, on one machine I am booting with  2.6.24-18 rather than 2.6.24-19 due to instability in the latter.

However just because it works, doesn't mean it's a good idea! Is it OK to keep on downloading all the updates but to stick with a particular kernel version pretty much indefinitely? I'm guessing that the interface to the kernel used by user space programs is constant across 2.6.24, which explains why I've been OK so far, but is there anything else that's likely to go wrong as I update non-user space programs, drivers for example?

If it's safer to simply lock down my machine apart from possibly security updates, I'm happy to do that as I don't *ever* want to be tearing my hair out again over random hangs. Not much left :).

Tony.

---

### Post by kuja on 2008-07-06
It won't be changing from 2.6.24 until Intrepid is released, so you'll be okay there. The only problems you might run into with the older kernel is that if you need restricted modules from the related linux-restricted-modules package, and perhaps closely related things, they'll be upgraded and follow along with the rest of the kernel stuffs. If you need this what you can do is re-intall the old version from your /etc/apt/cache/archives if you still have it cached, you can also force apt to hold any and all such packages back.

---

### Post by TonyGould on 2008-07-06
> **kuja said:**
> It won't be changing from 2.6.24 until Intrepid is released, so you'll be okay there. The only problems you might run into with the older kernel is that if you need restricted modules from the related linux-restricted-modules package, and perhaps closely related things, they'll be upgraded and follow along with the rest of the kernel stuffs. If you need this what you can do is re-intall the old version from your /etc/apt/cache/archives if you still have it cached, you can also force apt to hold any and all such packages back.

thanks. If I understand you rightly, you're saying that restricted drivers associated with an older kernel, -16, say, might get overwritten when drivers are updated to work with the latest kernel, -19 say.

I'm sorry to be a little slow but I'm quite new at this -- just 6-9 months or so on 7.10 before I'm upgraded, and I've never had to think about doing something different from the default. Looking at Synaptic on the machine I'm typing this no, I have both
[LIST]
[*]linux-image-2.6.24-16-generic; and
[*]linux-image-2.6.24-19-generic
[/LIST]installed. As they're both marked as installed, isn't apt going to keep all the dependencies for both of them around forever until I tell apt to remove -16?

Please do tell me to RTFM if you know where a suitable M is!

Tony.

---

### Post by kuja on 2008-07-06
Wait, it looks like it very well may keep the l-r-m packages too, other things, if needed, probably not. Then again, if everything is working for you now then what is there to worry about (unless some piece of hardware isn't working and was before, or something)

---

### Post by BatPenguin on 2008-07-06
> **TonyGould said:**
> thanks. If I understand you rightly, you're saying that restricted drivers associated with an older kernel, -16, say, might get overwritten when drivers are updated to work with the latest kernel, -19 say.

I'm sorry to be a little slow but I'm quite new at this -- just 6-9 months or so on 7.10 before I'm upgraded, and I've never had to think about doing something different from the default. Looking at Synaptic on the machine I'm typing this no, I have both
[LIST]
[*]linux-image-2.6.24-16-generic; and
[*]linux-image-2.6.24-19-generic
[/LIST]installed. As they're both marked as installed, isn't apt going to keep all the dependencies for both of them around forever until I tell apt to remove -16?

Please do tell me to RTFM if you know where a suitable M is!

Tony.

Just jumping in here, since I'd actually be really interested in various issues related to this too...my "problem" is that I have two modules that need to be recompiled whenever the kernel changes. These are lirc (I have to use a pvr-150-specific hacked module to get my Mythtv's IR transmitter to work) and my DVB-tv module for my other tv card. Both of these I've had to recompile, copy the new modules over the updates ones etc. every time there's a kernel update. So basically whenever I install all available updates and there happens to be a slight kernel change, my Mythtv breaks :)

It's getting to be really old to recompile the modules once every few weeks for, frankly, no apparent benefit at all (as far as I can see), so I'd really like to know how to best keep the kernel at a certain version and whether I'm risking some bad problems by doing this but still having "install security updates automatically" on and installing all other updates. What packages should I lock to current version in Synaptic? I update every time there's a new Ubuntu version, anyway, so at the most I'd be running a six-month old kernel, doesn't sound too bad.

---

### Post by kuja on 2008-07-06
BatPenguin: I'd say lock linux-image, linux-image-generic, linux, linux-restricted-modules-common, and linux-restricted-modules-generic at the least.

---

