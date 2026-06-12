---
title: "Frequent Kernel Panics! Please Help!"
date: 2015-11-12
forum: General Help
---

### Post by cobradabest on 2015-11-12
I've been using (or trying to use) Linux on this PC I've built for about a year now, and I am constantly getting Kernel Panics (The screen freezes or goes black with the Caps and Scroll Lock lights flashing), and it does this on every distro I've tried, Ubuntu, Linux Mint, Linux Lite, Ubuntu Studio etc. and it's always the same issue!

I'm using an AMD card, which I've heard has awful drivers for Linux, the card I have inparticular (AMD R9 200) is buggy with Linux Mint, I'm not sure about the other though, but it looks like they might be the same...

I've tried switching to a proprietary driver, but that only made things worse...

I don't know how to check what kernel I have exactly, but I've tried dozens, and they all give me the same issues...

Is there an Ubuntu based distro I can use that WON'T give me kernel panics? I love Linux, and in particular Ubuntu-based OSes,they are perfect for me working on my projects, and I don't want to just stop using it... and no, I'm not loaded, so please don't tell me to just get an nvidia card...

Is there anything I can do?

If it helps, here are the rest of my specs:
500GB HDD
Intel 2-core CPU (Overclocked to around 4GHz)
8GB RAM

I'm currently using Ubuntu Studio 15.10, if that makes any difference.

---

### Post by QIII on 2015-11-12
Hello!

The first thing I would do is back off the overclock to stock and see what happens.

---

### Post by cobradabest on 2015-11-12
Well, I can try it, but is there a way to limit the power and make it not overclocked only when booting Ubuntu? because I also have Windows installed, and I use that to run games, and I need all of the power I can get when I'm on that...

---

### Post by QIII on 2015-11-12
Just to rule that out as part of diagnosing the problem for now.

---

### Post by cobradabest on 2015-11-12
Well, I've done it, and it seems to be more stable, I haven't has a kernel panic so far... So assuming this is the problem, is there anyway to sort make it so that the SPU is overclocked when on Windows, but normal when on Linux?

---

### Post by cobradabest on 2015-11-13
...Anyone... ? I need my CPU overclocked for playing games on Windows, and it'd be a pain to just change the settings every time I want to switch OS...

---

### Post by matt_symes on 2015-11-13
Hi

> **cobradabest said:**
> ...Anyone... ? I need my CPU overclocked for playing games on Windows, and it'd be a pain to just change the settings every time I want to switch OS...

Is it just the CPU you have overclocked ? If so, you may be able to downclock it by using the command below where <freq> is the maximum frequency the governor will clock the  CPU at.

```
sudo cpupower frequency-set -d <freq>
```

Run this command from the terminal and see if it downclocks the CPU's maximum frequency to the frequency you set. Pick one of the clock speed you CPU can step to.

If it works try adding it (without the sudo) to /etc/rc.local or you could put it even earlier in the boot process.

I have never tried this and i have no idea if it will help in your case as your CPU is overclocked, but it gives you a starting point to research. You may still find the kernel is unstable even if you downclock. To be honest, i don't know.

You'll need to install at least the linux-tools... package for your current kernel version and maybe linux-cloud-tools... as well.

You may want to install the metapackages in place of the above two packages so your linux-tools and linux-cloud-tools packages are in sync with your kernel.

Below are (some of) the meta packages for linux-tools and linux-cloud-tools

```
matthew-laptop:/home/matthew/Videos:4 % acse "linux-cloud-tools-generic|linux-tools-generic"
linux-cloud-tools-generic - Generic Linux kernel cloud tools
linux-tools-generic - Generic Linux kernel tools
linux-tools-generic-lts-saucy - Generic Linux kernel tools
linux-tools-generic-lts-trusty - Generic Linux kernel tools
linux-cloud-tools-generic-lts-utopic - Generic Linux kernel cloud tools
linux-cloud-tools-generic-lts-vivid - Generic Linux kernel cloud tools
linux-cloud-tools-generic-lts-wily - Generic Linux kernel cloud tools
linux-tools-generic-lts-utopic - Generic Linux kernel tools
linux-tools-generic-lts-vivid - Generic Linux kernel tools
linux-tools-generic-lts-wily - Generic Linux kernel tools
matthew-laptop:/home/matthew/Videos:4 % 
```

Did the above make any sense as what you are trying to achieve is unusual ?

Kind regards

---

### Post by cobradabest on 2015-11-13
> **matt_symes said:**
> Hi



Is it just the CPU you have overclocked ? If so, you may be able to downclock it by using the command below where <freq> is the maximum frequency the governor will clock the  CPU at.

```
sudo cpupower frequency-set -d <freq>
```

Run this command from the terminal and see if it downclocks the CPU's maximum frequency to the frequency you set. Pick one of the clock speed you CPU can step to.

I take it the GHz number is the frequency? If so, my CPU is 3.2GHz, so do I just type in "3.2"?

Also, how will I know it has worked?

---

### Post by matt_symes on 2015-11-13
Hi

> **cobradabest said:**
> I take it the GHz number is the frequency? If so, my CPU is 3.2GHz, so do I just type in "3.2"?

I've no idea. Like i said, i have not tried it so i can't really help you with specifics. 

You're also overclocking your CPU which is an unknown quantity.

I'm trying to give you a place to start researching this.

Personally i think, if your CPUs maximum step speed is 3.2Ghz when stock clocked then you want to pick a step speed below that to downclock it when overclocked....

...but as i said, research this because i am not tell you what to do but what to research.

> Also, how will I know it has worked?

Check the speed your CPU is running at when under load. I think there are applets in Ubuntu for this.

Kind regards

---

