---
title: "Kernel Updates."
date: 2016-11-28
forum: General Help
---

### Post by gabers2004 on 2016-11-28
I've noticed that whilist updating via apt-get update & apt-get upgrade. Whilist other operating systems are running kernel 4.8.x and 4.9.xRC, I am stuck on kernel 4.4? Is there another upgrading command, or do I manually have to pull in the kernel via PPA? Thanks a lot


-Scarce
(get the meme... csgo players)

---

### Post by Bashing-om on 2016-11-28
gabers2004l Hello; Welcome to the forum ,

The booting kernel depends on the release .
kernel 4.4 belongs to xenial (16.04)
> 
 linux-image-generic (source: linux-meta): Generic Linux kernel image. In component main, is optional. Version 4.4.0.47.50 (xenial), package size 2 kB, installed size 12 kB


where as for instance in trusty (14.04) :
> 
sysop@1404mini:~$ uname -r
3.13.0-101-generic
sysop@1404mini:~$


So, what release are you running :
One can tell from:
```

lsb_release -a

```

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-11-28
What release of Ubuntu are you running?

As of today (it changes frequently):
  16.04 runs kernel 4.4,
  16.10 and 17.04 run kernel 4.8.
  4.9 is in zesty-proposed - beware, be lots of breakage there.

---

### Post by gabers2004 on 2016-11-28
I mean like updating current kernel from 4.4--> to 4.8. Is there a way to do so? Or will ubuntu come to me and tell me when an kernel update is availiable via Update-manager?

Thanks once again!

---

### Post by ian-weisser on 2016-11-28
A release of Ubuntu does not upgrade the kernel (or any other software). Each, upon release, is a snapshot - forever frozen in time. Security and bugpatch upgrades only.
So Software Upgrader will not say to you "try the new 4.8.3 kernel!"
One exception (below).


There are three ways to upgrade your 4.xx kernel to a new 4.yy release. Each has advantages and disadvantages that you must weigh.
We don't know why you want the latest kernel, so cannot advise better.

1) Upgrade to the next release of Ubuntu. If you are running 16.04, upgrading to 16.10 will jump you from kernel 4.4 to 4.8...along with upgraded applications. This puts you on the must-upgrade-every-six-months treadmill, which some users welcome and others find annoying. This option is fully-supported. Release-upgrades cannot be reverted - if you wish to return to 16.04, you must reinstall.

2) If you are using an LTS Release of Ubuntu (12.04, 14.04, 16.04), you can jump to a newer kernel by using [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) . This replaces the linux-image-generic metapackage with a release-specific kernel metapackage. You must remember to update the metapackage every six months - Ubuntu will not remind you. None of your applications change or upgrade, which is generally the purpose of an LTS release. This option is fully-supported. Kernel upgrades can be reverted with a bit of (supported) apt voodoo.

3) You can use the Ubuntu Kernel Team PPA. The Kernel Team PPA is intended for testing and bug reporting, not distributing stable upgrades. Since it's a PPA, it's not supported - the best advice you may get from support channels is to revert to a stable, supported kernel. Kernel upgrades can be reverted with a bit of (supported) apt voodoo. Be sure to uninstall all PPA and other non-Ubuntu packages and return your system to as close to stock as possible before upgrading to the next release of Ubuntu.

---

### Post by Bashing-om on 2016-11-28
gabers2004; Hey ....

Short answer is Yes and Yes.

But as usual Ian says it better .


If you want to install a later version kernel, weellll, you can - but there be dragons ; Ask your self what you hope to gain by installing a updated kernel .

If you wait for the next point release on 16.04 you will have the option to enable the ability to install yakety's kernel natively and it's supporting X packages . Bit again, why ?- What issue do you expect to fix ?

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]you can your can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Frogs Hair on 2016-11-28
There are various instructions available for installing the 4.8 kernel on 16.04 found with a web search, but you would be on your own if things go wrong. 16.10 includes the 4.8 kernel though it isn't a long term support release. I don't know what kind of upgrades the 16.04 point releases may include over its life.
 
16.10:```
uname -r 4.8.0-27-generic
```

---

### Post by wildmanne39 on 2016-11-28
When it comes to upgrading kernels the rule of thumb is unless you have an issue that upgrading will fix or the new kernel adds support for a new piece of hardware that you have there is no advantage to updating the kernel and should just keep using the one ubuntu comes with.

---

### Post by gabers2004 on 2016-11-29
Thanks y'all!
It seems a common question is "Why would you want to upgrade to kernel 4.8.x?" 
Heres why:
Right Now I'm using an ethernet cable to solve issues with my wireless card, well, this is my brother's anyway. Being an arch-user, Kernel 4.8.x does support it thanks to the ath10k_pci module. Thanks to you, all I have to do is load the module, and my wireless should work. I should just teach my brother to use arch. Lol. Thanks!

---

### Post by jeremy31 on 2016-11-29
Post results for ```
lspci -nnk | grep -iA2 net
```
It appears only a couple Atheros cards are not supported in the Ubuntu 4.4 kernel but a bug report could get support in as it does work in 4.8

---

