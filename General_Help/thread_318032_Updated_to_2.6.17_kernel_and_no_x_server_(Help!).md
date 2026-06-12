---
title: "Updated to 2.6.17 kernel and no x server (Help!)"
date: 2006-12-13
forum: General Help
---

### Post by Rodneyck on 2006-12-13
Help!

I hit the update button and it updated four or five files, I believe it updated my kernel to 2.6.17-10 . This kernel must not recognize my nvidia (beta) drivers as it won't boot up the x server. I was able to boot up if I restarted and selected the "generic" option (probably safe mode.) 

Once inside, someone on the forum suggested that I switch drivers from the nvidia to nv because the new kernel does not yet support nvidia or something like that, so I did. Now it won't boot up the x server in any mode and all I get is a black screen with prompt. 

Luckily I did save a copy of my xorg.conf file on my desktop, but I do not know how to copy it to replace it with the orginal. At least this will get me back to the point where the x server works under the "generic" option. So, please, someone tell me how to copy and replace.

The next step, I guess, is to revert the kernel back or try uninstalling the drivers completely, not sure yet.  Any thoughts here would be appreciated.

Thanks.

---

### Post by Rodneyck on 2006-12-13
Ok, I figured out how to copy and replace my xorg.conf file and can now boot into the x server with "generic" mode.

Can someone tell me how to revert my kernel back?

---

### Post by Rodneyck on 2006-12-13
Well these new linux "restricted" modules I loaded and wish I had not (2.6.17.7-1) are listed in synaptic but I can't uninstall them without removing the linux-generic which is the whole linux kernel. 

I have managed to uninstall the nvidia (beta) or latest graphic drivers through Automatrix2 and I am now using the "nv" drivers and able to boot into the x server normally. So, these new kernel updates do not play well with the new nvidia drivers, be warned if you see them.

I am not sure what to do. I was using beryl, which is now uninstalled and stuck with old drivers, that s*cks. Does anyone have any thoughts on how to remove these "restricted" linux modules?  Anyone....Bueller?

---

### Post by Roque on 2006-12-13
Exactly the same happened to me. I am now booting with 2.6.15, but the nvidia driver doesn't work at all. I am stuck with the "nv" driver for now.

But I don't understand this: if I upgraded to 2.6.17 and I am using 2.6.15, everything should work normally, doesn't it?

---

### Post by Frenzy on 2006-12-13
Hi,

I also just updated to the new kernel 2.6.17 and my system will not boot.  All I get is a line saying starting or something to that effect and it just hangs.  Any good solutions as I am not sure where to go.

Thanks

---

### Post by Rodneyck on 2006-12-13
Thankfully, I see I am not the only one. I was beginning to wonder.

Here is a thread (yes, this has happened before) I am currently going through to see if I can get some help.

[http://www.ubuntuforums.org/showthread.php?p=1881932#post1881932](http://www.ubuntuforums.org/showthread.php?p=1881932#post1881932)

---

### Post by Roque on 2006-12-13
I guess you'll still have the other kernels sitting around. Are you using grub for boot switch?

---

### Post by jdong on 2006-12-13
try running 'sudo depmod -ae' and rebooting. See if that does anything to resolve your problems.

Please also post any errors when you issue a **sudo modprobe nvidia.ko**

---

### Post by Rodneyck on 2006-12-13
> **Roque said:**
> I guess you'll still have the other kernels sitting around. Are you using grub for boot switch?

I am using grub for boot switch. You mean using the "generic" setting? Yes.

However, if you switch the xorg.conf from "nvidia" to "nv", then I can boot in normal fashion.

---

### Post by igknighted on 2006-12-13
What are the kernels you can boot from?  Edgy's default should be 2.6.17-10-generic.  This is the standard kernel that comes with Edgy.  The nvidia drivers from what I can tell (the 9xxx series ones at least) make you install the i386 kernel.  You are probably running into an issue with something missing out out the headers/restricted-modules/nvidia-glx drivers.  Do you know what kernel the NVIDIA installer built against?

generic isnt a setting, its a kernel (the default one).  As is i386.

---

### Post by Rodneyck on 2006-12-13
> **igknighted said:**
> What are the kernels you can boot from?  Edgy's default should be 2.6.17-10-generic.  This is the standard kernel that comes with Edgy.  The nvidia drivers from what I can tell (the 9xxx series ones at least) make you install the i386 kernel.  You are probably running into an issue with something missing out out the headers/restricted-modules/nvidia-glx drivers.  Do you know what kernel the NVIDIA installer built against?

generic isnt a setting, its a kernel (the default one).  As is i386.

When I say "generic" I mean the option during the boot up grub, so whatever that is, gets me into x server.

I looked on my second computer which has the updates (not installing them on that one) and they say..

linux-headers 2.6.17-10
From version 2.6.17-10.33 to 2.6.17-10.34

There are three of those and one...
linux-libc-dev update fo rthe save version switch as above.

BTW... The Beryl team has identified this problem and I guess they are working on it...

[http://www.ubuntuforums.org/showthread.php?t=263851&page=130](http://www.ubuntuforums.org/showthread.php?t=263851&page=130)

---

### Post by igknighted on 2006-12-13
hmm, note to self, don't update...

---

### Post by xabbott on 2006-12-13
If you use binary drivers and update your kernel you just reinstall the binary drivers.

---

### Post by Rodneyck on 2006-12-13
> **xabbott said:**
> If you use binary drivers and update your kernel you just reinstall the binary drivers.

Well they are apparently looking into the matter, but out of curiosity, how does one go about reinstalling binary drivers?

---

### Post by jdong on 2006-12-13
Thanks to lupine_85 in #ubuntu-xgl, I've narrowed down that the update makes the following files disappear:
```

usr/lib/xorg/modules/drivers/nvidia_drv.o
usr/lib/xorg/modules/libglx.so

```

Which in turn causes nvidia to not load. However, a reinstall of nvidia drivers should restore those.

What exactly is causing them to disappear is still a mystery at this point.

---

### Post by Rodneyck on 2006-12-13
Funny, because I did reinstall the nvidia drivers through automatrix2 the update worked, but still could not boot into the x server.

I will try bypassing automatrix and install them by hand to see if that works.

---

### Post by xabbott on 2006-12-13
> **Rodneyck said:**
> Well they are apparently looking into the matter, but out of curiosity, how does one go about reinstalling binary drivers?

Actually I was mistaken. You would only need to reinstall if you compiled the module yourself. If I was in your situation though I would just do it anyway. As to how you do it, just do whatever you did to install them...again.

---

### Post by Azakus on 2006-12-13
Try this repo for nvidia drivers. It contains the restricted driver module that has the newest nvidia drivers.
(64-bit)
deb [http://ubuntu.lupine.me.uk/](http://ubuntu.lupine.me.uk/) edgy lrm-amd64
(32-bit)
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
Then apt-get update and upgrade and it will replace nvidia-glx with the 1.09269 drivers.

---

### Post by Rodneyck on 2006-12-13
> **Azakus said:**
> Try this repo for nvidia drivers. It contains the restricted driver module that has the newest nvidia drivers.
(64-bit)
deb [http://ubuntu.lupine.me.uk/](http://ubuntu.lupine.me.uk/) edgy lrm-amd64
(32-bit)
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
Then apt-get update and upgrade and it will replace nvidia-glx with the 1.09269 drivers.

Thanks!!!  I just tried updating using the beta drivers and it did not work, so I will try this.

---

### Post by PriceChild on 2006-12-13
Important sticky for those with breakage, please refer to the following sticky: [http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by Rodneyck on 2006-12-13
Well I tried reinstalling and updating the nvidia drivers as mentioned above, but still could not boot into x server.

two questions, how do you uninstall the nvidia drivers (I usually use automatrix, but I don't really think that actually uninstalls them)?

The other question, is there a command to type in Terminal that lets you know what version (graphic drivers) you are using?

---

### Post by Roque on 2006-12-13
> **Rodneyck said:**
> Well they are apparently looking into the matter, but out of curiosity, how does one go about reinstalling binary drivers?
> **jdong said:**
> Thanks to lupine_85 in #ubuntu-xgl, I've narrowed down that the update makes the following files disappear:
```

usr/lib/xorg/modules/drivers/nvidia_drv.o
usr/lib/xorg/modules/libglx.so

```

Which in turn causes nvidia to not load. However, a reinstall of nvidia drivers should restore those.

What exactly is causing them to disappear is still a mystery at this point.
I reinstalled the drivers with apt-get install --reinstall to no avail

---

