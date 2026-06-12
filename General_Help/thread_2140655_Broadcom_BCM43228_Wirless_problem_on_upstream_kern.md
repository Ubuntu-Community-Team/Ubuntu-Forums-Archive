---
title: "Broadcom BCM43228 Wirless problem on upstream kernel"
date: 2013-04-30
forum: General Help
---

### Post by MorrisseyJ on 2013-04-30
Hi, 

I have been having problems with random system freezes since upgrading to 13.04. As such i have filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1174275](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1174275)

As instructed there i installed the upstream version of the kernel (3.9.0-999-) to see if i that fixes my problem. I haven't yet been able to work in the kernel for a sufficiently long time to know whether the problem is fully resolved - although i've had no freezes yet!

What installing the upstream kernel did do however was stop my wireless from working and I now can't seem to see any of the wireless networks. Further to that, in my attempts at fixing the wireless in the upstream kernel i appear to have broken it on the current one, so i can't see any wireless networks there either. 

```
lspci | grep Network
```

gives: ```
Broadcom Corporation BCM43228 802.11a/b/g/
```

Previously, when upgrading to 12.10 i had problems with my wireless and fixed them with: 
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```

When i then upgraded to 13.04, i got the wireless working simply by enabling the Broadcom 802.11 Linux STA wireless driver, through the 'additional drivers' tab in 'software & updates'.

When my wireless stopped working when testing the upstream kernel, i saw that the Broadcom 802.11 Linux STA wireless driver was enabled, and thus tried the fix i used in 12.10.
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```

This did nothing (possibly because the headers that came down appeared to be for a 3.8 version of the kernel) and so i tried some other fixes people had suggested for broadcom cards including:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer
```

That did nothing but then i found when booting to the current kernel that my wireless was no longer working there either. 

I have tried to undo these steps but have clearly messed things up along the way. I have now tried a number of different permutations and combinations of installing, reinstalling and purging different things but to no avail. I was wondering if someone could walk me through what i need to do to get my wireless back on the current kernel, and ideally get it up and running on the upstream kernel, so that i can test that.

Currently the Broadcom 802.11 Linux STA wireless driver is enabled and i have installed on my system: 
broadcom-sta-common
 bcmwl-kernel-source 
broadcom-sta-source
 b43-fwcutter
 firmware-b43-lpphy-installer

Thanks, 

j

---

### Post by dino99 on 2013-04-30
you might try a fresh install with ext4  [http://www.zdnet.com/my-experiments-with-installing-ubuntu-13-04-pre-release-with-uefi-boot-7000014233/](http://www.zdnet.com/my-experiments-with-installing-ubuntu-13-04-pre-release-with-uefi-boot-7000014233/)

---

### Post by MorrisseyJ on 2013-05-01
Hi dino99, 

Thanks for getting back to me, but i wasn't too keen on doing a fresh install. Possibly i'll look at that link you posted when i next upgrade, updating the BIOS first. 

I have however managed to fix this. 

To do so i booted to the Live USB of 13.04, from which i knew i was able to get the wireless working by enabling the proprietary driver. I knew this would work because it had worked for the install of 13.04.

I then tethered myself to the internet, added the universe repository and installed synaptic to the live instance.

I then checked which packages were installed, via synaptic, before i enabled the proprietary wireless driver. It turns out that neither 'bcmwl-kernel-source', nor 'b43-fwcutter' were installed and 'broadcom-sta-common', 'broadcom-sta-source' and 'firmware-b43-lpphy-installer' were not even visible in the package list. 

I then enabled the proprietary driver through the additional drivers option and checked that the wireless was working - it was, the same way that it had worked during my original install.

I then went back into synaptic to see what packages were there. It turns out that only bcmwl-kernel-source was installed. 

So i booted back to my current install on the current kernel. I disabled the proprietary driver, opened synaptic and completely removed all of: 'bcmwl-kernel-source', 'b43-fwcutter', 'broadcom-sta-common', 'broadcom-sta-source' and  'firmware-b43-lpphy-installer'

I then rebooted to the same kernel and enabled the proprietary driver. Low and behold, the wireless started working. 

So it seems that all i had to do was disable the proprietary driver, which was the 'bcmwl-kernel-source' package, remove all the other packages i had installed and re-enable the proprietary driver. 

Its frustrating that that solution didn't come about in my earlier attempts at installing and un-installing different packages. It really was the most obvious one. 

So now i have wireless working on the current kernel, but have yet to get it working on the upstream one. I'll mark this as solved and take that question to the bug report as i am now thinking that it may be conflict with the wireless driver which is causing the freezes.

---

### Post by MorrisseyJ on 2013-10-17
It was a problem with the wireless driver that was causing the problem. Broadcom BCM43228 chip was freezing when the package bcmwl-kernel-source was installed, and the machine was on battery power. 

I tries a number of things to fix this, but all failed. Eventually i bought an intel centrino chip which was whitelisted for my machine and now everything works fine. 

Not really satisfactory, but i am happy to have a working machine. 

j

---

