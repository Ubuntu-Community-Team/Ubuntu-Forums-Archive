---
title: "Frequent intermittent freezing (16.04.2)"
date: 2017-06-18
forum: General Help
---

### Post by ObsequiousNewt on 2017-06-18
Frequently (at an estimate almost daily), Kubuntu will freeze. The mouse moves, the caps-lock light works, and I can press Ctrl-Alt-F# to switch to and from a console, but clicking and keyboard input has no effect, nor does using Ctrl-Alt-Escape.

There seems to be a "slowing down" effect about a second before it fully freezes.

dmesg doesn't reveal anything at the time of the freeze, neither does /var/log/syslog. No processes are using exceptionally high CPU or memory.

Here is the output of inxi -F:
```
System:    Host: watership Kernel: 4.8.0-54-generic x86_64 (64 bit) Console: tty 1 Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO product: 80V4 v: Lenovo YOGA 710-14IKB
           Mobo: LENOVO model: Lenovo YOGA 710-14IKB v: SDK0J40709 WIN
           Bios: LENOVO v: 2XCN25WW(V2.00) date: 10/14/2016
CPU:       Dual core Intel Core i5-7200U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3100 MHz 1: 484 MHz 2: 472 MHz 3: 499 MHz 4: 497 MHz
Graphics:  Card: Intel Device 5916
           Display Server: X.org 1.18.4 driver: intel tty size: 240x67 Advanced Data: N/A out of X
Audio:     Card-1 Intel Device 9d71 driver: snd_hda_intel Sound: ALSA v: k4.8.0-54-generic
           Card-2 Logitech H600 [Wireless Headset] driver: USB Audio
Network:   Card-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci
           IF: wlp1s0 state: up mac: 58:00:e3:42:be:ad
           Card-2: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 256.1GB (11.9% used) ID-1: /dev/sda model: SAMSUNG_MZNTY256 size: 256.1GB
Partition: ID-1: / size: 227G used: 21G (10%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 8.43GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 226 Uptime: 1 day Memory: 4215.9/7825.9MB Init: systemd runlevel: 5
           Client: Shell (bash) inxi: 2.2.35
```

The top few hits for freezing issues in Kubuntu mostly have to do with nvidia or swap, neither of which should be applicable here.

---

### Post by SagaciousKJB on 2017-06-18
When it freezes and you're able to switch to a console, are you able to run commands? You should use vmstat and iostat while it's freezing like that, though the liklihood bash will load up while it's freezing like this is questionable.

It sounds a lot like RAM/swap to me. I am still on a system with 2 GB and this is a pretty regular occurrence for me once RAM starts filling up. Keep in mind some applications don't report TRUE memory usage. That is saying you're only using 50%, but that could mean it's only 50% user threads where as the system is trying to use the other 50% for kernel stuff and therefore your RAM is actually maxed out.

Seems kind of unlikely though that with 8 gb of ram and 8 of swap that you'd be running out unless you were having some major memory leaks. What kind of applications are you running when it happens?

---

### Post by ObsequiousNewt on 2017-06-18
Yes, I can run commands, which is how I conclude the above (viz. nothing useful in dmesg or /var/log/syslog). I hadn't run vmstat or iostat specifically, and I'll try those the next time it freezes, but running top shows no significant processor or memory drain.

Applications I was running when it happened are pretty much just: firefox, thunderbird, emacs, quassel, konsole. I do have a lot of tabs open on firefox but no more than it should be able to handle.

In general though I don't think it's a resource problem. I can move the mouse after it freezes, and there doesn't seem to be any lag there. Nor does bash in the console show any lag. It's more like the window manager is hanging for some reason.

---

### Post by ObsequiousNewt on 2017-06-19
Output of iostat and vmstat:
```

hazel@watership:~$ iostat
Linux 4.8.0-54-generic (watership)     06/19/2017     _x86_64_    (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           8.72    0.01    4.27    0.36    0.00   86.63

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               2.97        21.71      2078.13    2394101  229158545

hazel@watership:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 0  0      0 545724 270484 3683688    0    0     8    44   75   86  9  4 87  0  0

```

---

### Post by SagaciousKJB on 2017-06-19
Well, it's a total stab in the dark, but if you grep /var/log/Xorg.0.log for warning messages do you see anything?

```
grep WW /var/log/Xorg.0.log
```

It's been a while since I used KDE but I think you might wanna check /var/log/kdm.log too

---

### Post by ObsequiousNewt on 2017-06-20
No results in Xorg.0.log, and kdm.log doesn't appear to exist.

---

### Post by dragonfly41 on 2017-06-20
I've used this tip before to troubleshoot freezing or glitches.

To test the possibility of glitch in a memory card can you try removing half of your memory cards.

Test for freezing.

If freeze occurs swap the half memory.

Test for freezing again.

This might possibly narrow down fault in one of a number of memory cards.
I always clean the edges of memory cards with clean rubber eraser before replacing.

It is a long shot I'm afraid.

Alternatively run a memory test from grub menu.

---

### Post by ObsequiousNewt on 2017-06-29
Sorry for the late reply... it went a few days without freezing and I thought it was working.

I don't think it's possible to remove the memory cards from a Yoga 13. As for memtest, I'd run that, but I can't seem to get it to appear in the boot menu.

---

### Post by efflandt on 2017-06-30
You can download memtest86 and boot it from CD or USB. [http://www.memtest86.com/technical.htm](http://www.memtest86.com/technical.htm) Although, if that is the RAM it came with it would be strange for it to have a problem.

Assuming that is a laptop and no obvious panel on the bottom to access the RAM, you might be able to find a YouTube video showing how to open it up. That is what I had to do when I wanted to add RAM to a low end HP laptop. I had to peel back a couple of the rubber feet near the hinge to get at a couple of the screws, then go around the clamshell case with a credit card (hopefully an old one) to separate the bottom half. And it was a good thing that I popped it open first (didn't have Linux on it then), because I thought I could add 4 GB to its 4 GB, but it only has one RAM slot, the other place for one on the motherboard has no slot attached. If you have a single 8 GB card, there would be no way to just remove half of it.

You could look through the following to see what RAM you have including size in each bank (slot):```
sudo lshw | less
```But not sure if that would show if a bank has no slot attached.

The only time I had similar symptoms was when a cheap Galaxy GT 430 graphics card began failing shortly after its one year warranty expired. Occasionally keyboard and mouse buttons would stop responding, but mouse cursor would usually still move. Eventually there were graphic glitches during boot and in logs nvidia driver reported "hardware not responding". I am still using that PC and never had that issue since replacing that graphics card.

---

### Post by ObsequiousNewt on 2017-07-06
I can't boot memtest from USB. It requires non-EFI mode, and due to some firmware bug I wot not of, trying to boot in legacy mode just brings up a blank screen with a blinking cursor.

The output of lshw reports that I have only one memory stick which is 8 GiB, so trying to open it up won't help either [until I can at least get some other memory to test with...]

In terms of other problems I have had with this laptop, the main other problem is a keyboard bug, reported as [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1585094](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1585094).

---

