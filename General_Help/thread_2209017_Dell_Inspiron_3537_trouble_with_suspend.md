---
title: "Dell Inspiron 3537 trouble with suspend"
date: 2014-03-03
forum: General Help
---

### Post by yuviG on 2014-03-03
I have a brand new laptop Dell Inspiron 3537, and have installed on it ubuntu desktop 12.04.04 (64 bit). Everything is working fantastically, but I'm having trouble with suspend. Whenever I close the lid, and the computer goes into suspend, when I open it up again, everything is black. I can move the mouse for a split second but then it's stuck.

Nothing I do gives any respond (no terminal mode no nothing), and I have to resort to a hard shutdown. I have no idea what's the problem. I'm not experiencing similar problems with hibernate, so it's definitly suspend (also happening when trying a manual suspend).

My graphics card is AMD Radeon HD 8800M, the result of the command[FONT=Ubuntu Mono]lspci | grep VGA[/FONT] is as follows:

```

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8800M Series]

```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]The driver I have installed is the newest beta version ([this]("https://launchpad.net/ubuntu/+source/fglrx-installer-experimental-13")), but downgrading didn't help (in fact, the experimental one solved some other issues I had with running photoshop through wine). I tried searching all around google but found exactly nothing relavent (and [the little I found]("http://ubuntuforums.org/showthread.php?t=1978290") didn't help). I even tried [opening a quesiton]("http://askubuntu.com/questions/428058/dell-inspiron-3537-problems-with-resuming-from-suspend-after-installing-video-d") on AskUbuntu but no luck there either.

Please help, this is a serious headache for me, and I have to solve it (it's my work computer, I constantly need to open and close it, at least once every day)

---

### Post by phidia on 2014-03-03
I've had similar suspend problems with an ATI equipped laptop-not your specific card however. You might try looking at your log files to see if there is anything there. ([https://one.ubuntu.com/help/faq/where-are-log-files-kept-on-ubuntu/](https://one.ubuntu.com/help/faq/where-are-log-files-kept-on-ubuntu/)) 

Although it might not be much help you could try the laptop compatibility webpage [here]("http://www.linux-laptop.net").

I also checked at AMD's [linux driver page]("http://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx") I didn't see your card there but you might try asking there for their recommendation.

---

### Post by yuviG on 2014-03-03
Thanks for the reply. The computer actually has an ubuntu certification [here]("http://www.ubuntu.com/certification/hardware/201305-13649/") with version 12.04 so I knew beforehand that it should be fine (and, well, it is. Besides the suspend thing everything else is very smooth). 

What log files should I look up? I've checked /var/log/pm-suspend.log as it seemed the most relevant, but the content didn't look interesting (I can post it here if it might help). I couldn't tell which other files to look for.

---

### Post by phidia on 2014-03-03
It's true that your model is certified (I looked at that link earlier) however it appears that, as often happens, the Inspiron 3537 comes with several GPU options. Does your computer have dual cards? My point is that I'm not sure all the video cards are fully supported.
Ubuntu [suspend troubleshooting guide is here]("https://wiki.ubuntu.com/DebuggingKernelSuspend"). I hope that helps.

---

### Post by yuviG on 2014-03-04
I followed the **[COLOR=#333333][FONT=Ubuntu Beta]"resume-trace" debugging procedure for finding buggy drivers[/FONT][/COLOR]** from that link, and this is what dmesg.txt had when searching for "hash matches":

```

[    1.766773]   Magic number: 0:665:273
[    1.766776]   hash matches /build/buildd/linux-lts-saucy-3.11.0/drivers/base/power/main.c:643
[    1.766798] tty tty10: hash matches
[    1.766804] net lo: hash matches

```

Any ideas?

---

### Post by yuviG on 2014-03-04
Also, I ran **dmesg | grep fglrx **from terminal and got this:

```

[   12.203459] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.206400] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[   12.210284] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7634 MBytes.
[   12.210440] <6>[fglrx]   vendor: 1002 device: 6823 count: 1
[   12.210639] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   12.210748] <6>[fglrx] Kernel PAT support is enabled
[   12.210760] <6>[fglrx] module loaded - fglrx 13.30.1 [Jan  8 2014] with 1 minors
[   42.760504] fglrx_pci 0000:03:00.0: irq 66 for MSI/MSI-X
[   42.760981] <6>[fglrx] Firegl kernel thread PID: 1513
[   42.761024] <6>[fglrx] Firegl kernel thread PID: 1514
[   42.761065] <6>[fglrx] Firegl kernel thread PID: 1515
[   42.761152] <6>[fglrx] IRQ 66 Enabled
[   42.772492] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   42.772495] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
[   42.772496] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   42.772497] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 

```

---

### Post by yuviG on 2014-03-11
Installing the latest beta version of the upcoming Ubuntu 14.04 solved the issue!!
I almost can't believe it. It was so easy...  I'm very impressed with it. It also automatically handled other problems that I when installing 12.04 I had to figure out for myself (such as messed up grub and language switching hot keys). I've never experienced such an Ubuntu release that worked so well out of the box.

---

### Post by djbolojo on 2014-04-21
I know that this issue is marked as solved but yuviG you said tha installing 14.04 to the inspiron worked and solved your problem. How did you do it because i can find a problem solution to my problem which is just the upgrade to 14.04 or the installation of 14.04 from the beginning. I have a major problem with amd drivers after the upgrade and/or installation of Ubuntu 14.04

---

### Post by rowan2 on 2014-08-22
Upgrading to A08 bios seems to have solved it for me.

EDIT: Scratch that, it was switching from ATi to Intel graphics. :( Still has the problem with ATi. :(

---

