---
title: "Facing Issues With GPU After Update"
date: 2016-02-08
forum: General Help
---

### Post by greycloud2 on 2016-02-08
Hi Guys,

I have a Dual Boot (W10 Pro/Ubuntu 14.04.03 LTS) Dell Dimension E520 CPU with NVIDIA 7300LE GPU. I was using Ubuntu 14.04 LTS since 2014 without any issue but a couple of weeks back I updated Ubuntu to 14.04.03 (Update Size was around 629 MB). After completing Update when my CPU rebooted, it freezes whenever I login. The problem is that after reading many threads, I tried some tricks like removing NVIDIA drivers in Terminal mode but didn't help. Yes, a few times I was able to login but the resolution was 4:3 and after selecting NVIDIA from driver list when I reboot CPU I was back to square one. I don't remember what was the NVIDIA driver version I had before update but now whenever I try to install current version, it always installs NVIDIA 304 which I feel is incompatible with my old GPU.

I'd really appreciate if you can guide me about fixing this issue as I'm not that familiar with Linux.

Regards.

---

### Post by ajgreeny on 2016-02-08
How did you carry out the update from 14.04 to 14.04.3, and was the OS regularly updated whilst using 14.04 from the start?

I am amazed that it took over 600MB to do that, particularly if you had been updating regularly, but I would like to know some more of the story behind this, and whether or not you updated to the vivid hardware-enablement-stack.

I still run the original trusty 3.13.0-# series of kernels and the xorg versions from that as well on my Xubuntu 14.04, but my release is till shown as 14.04.3 by the system.

---

### Post by greycloud2 on 2016-02-09
> **ajgreeny said:**
> How did you carry out the update from 14.04 to 14.04.3, and was the OS regularly updated whilst using 14.04 from the start?

I am amazed that it took over 600MB to do that, particularly if you had been updating regularly, but I would like to know some more of the story behind this, and whether or not you updated to the vivid hardware-enablement-stack.

I still run the original trusty 3.13.0-# series of kernels and the xorg versions from that as well on my Xubuntu 14.04, but my release is till shown as 14.04.3 by the system.

Actually, last year I spend most of my time using Windows so Ubuntu didn't got much chance to update itself. Few weeks back when I was doing some work in Ubuntu, it showed me Update available of around 629 MB. The update downloading/installation went on smoothly without any interruption.  It is just that after Reboot the Graphic Issue popped up.

---

### Post by ajgreeny on 2016-02-09
It certainly sounds like a graphics driver problem but as I have never used an nvidia card I shall have to leave this to others.

However, it may be worth trying to boot to recovery mode, but when you get the menu that appears choose to resume and boot to a GUI which will , I believe, get to a low resolution basic graphics desktop.  From there you may be able to run the Additional Drivers utility and choose another driver version.

---

### Post by greycloud2 on 2016-02-09
Guys, please provide me with some solutions. Am unable to use Ubuntu anymore.

---

### Post by howefield on 2016-02-10
> **greycloud2 said:**
> I don't remember what was the NVIDIA driver version I had before update but now whenever I try to install current version, it always installs NVIDIA 304 which I feel is incompatible with my old GPU.

Have a look in /var/cache/apt/archives/ for nvidia packages, assuming that you haven't cleaned it out. Post it back here.
```
ls /var/cache/apt/archives/ | grep nvidia
```

Can you also post the output of 

```
uname -a
```
and
```
lspci | grep VGA
```

---

### Post by Bashing-om on 2016-02-10
greycloud2; Hello;

In addition to the aboves:
As you note:
> 
it always installs NVIDIA 304 which I feel is incompatible with my old GPU.

see: [http://www.nvidia.com/object/IO_32667.htmlhttp://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.htmlhttp://www.nvidia.com/object/IO_32667.html)
where the recommended driver for the 7300LE chip set is indeed version 304 which Nvidia will continue support through the end of 2017.

As advised, verify the hardware,
clean the system up from prior install attempts
install the appropriate driver.

[INDENT][INDENT][INDENT]just what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by greycloud2 on 2016-02-12
> **howefield said:**
> Have a look in /var/cache/apt/archives/ for nvidia packages, assuming that you haven't cleaned it out. Post it back here.```
ls /var/cache/apt/archives/ | grep nvidia
```Can you also post the output of ```
uname -a
```and```
lspci | grep VGA
```

```
 1 :nvidia-304_304.131-0ubuntu0.14.04.1_amd64.debnvidia-current_304.131-0ubuntu0.14.04.1_amd64.debnvidia-opencl-icd-304_304.131-0ubuntu0.14.04.1_amd64.deb
```

```
 2 :Linux Dell-DM061 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
 3 :01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
```

Hi, please have a look.

---

### Post by Yellow Pasque on 2016-02-12
It looks like you're booting into the old kernel.

You should be using 3.13.0-77 (the updated version of Ubuntu 14.04 kernel) OR
3.19.0-49 (the updated version of Ubuntu 14.04.3 kernel)

---

### Post by greycloud2 on 2016-02-13
> **Temüjin said:**
> It looks like you're booting into the old kernel.

You should be using 3.13.0-77 (the updated version of Ubuntu 14.04 kernel) OR
3.19.0-49 (the updated version of Ubuntu 14.04.3 kernel)

So, what to do know?

---

### Post by Yellow Pasque on 2016-02-13
Hold down the right shift key when you boot to bring up the grub menu. Choose the 3.19 kernel if you have it installed.

---

### Post by $yl9pAR%t on 2016-02-13
Good news, nvidia-304 driver works fine with kernel 3.13. Bad news, you should probably forget about using this driver with unity or other compiz dependend DE. I suggest installing Xubuntu 14.04.1. If you prefer your installed Ubuntu try gnome-session-fallback. You will find, how to do it in link below.

[http://ubuntuforums.org/showthread.php?t=2279009](http://ubuntuforums.org/showthread.php?t=2279009)

---

