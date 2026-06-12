---
title: "High pitched whistle"
date: 2019-04-23
forum: General Help
---

### Post by iamtheeggman2 on 2019-04-23
Hi,

I dont know where to start but I believe the graphics card which hs no fan, just a heatsink is the source of a high pitched whistle. The whistle is not present when running windows 10 or ubuntu 11.4 live disc leading me to believe possible drivers issue? The live disk had the hdmi cable plugged t the tv for the usual 75hz with 1024 768 resolution. Winow is set to that too as is my current linux install. The computer was put together and ran silently unless the cpu got busy, however I recently had to switch to the radeon graphics adapter and I wonder it that was when the whistling started. I am not sure what todo, can i install the graphics driver that came with the old ubuntu live disk and see if that changes it? I do notice the whistle stops when Iget the the ubuntu logo screen after logging out when you want the computer to reset.


```
home@home-System-Product-Name:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:33 memory:d0000000-dfffffff memory:feaf0000-feafffff ioport:d000(size=256) memory:c0000-dffff
home@home-System-Product-Name:~$ 


```


Anyone read this? it says zero views which I find hard to believe.

---

### Post by iamtheeggman2 on 2019-05-29
Hi

I've discovered the source of the whistle, it comes from the plugging in of audio jack from the microphone and the speakers output. I am sure I bought hi def gold plated cable. Any suggestions anyone?


Still it's weird the sound wasn't there in Windows until I just plugged in a microphone. 
Thanks in advance.

---

### Post by yetimon_64 on 2019-05-29
> **iamtheeggman2 said:**
> ... it says zero views which I find hard to believe.

Sorry I can't help with the main question regarding the noise, but I can comment on the quote above. People are seeing the thread, however the thread count function on the forums is broken and has been for quite some time. Wait for further advice on your main question here.

**Edit**: I just noted how old the original post is. You can bump the thread about once a day so people who may be able to help have more chance of spotting it. Just posting the word "bump" daily will keep it up near the top of the forum listing and will increase your chance of a reply to your problem.

Regards, yeti.

---

### Post by Autodave on 2019-05-29
You have 11.4 installed????  Really?  That version was dead many years ago.  Please let us know what version you are running.

---

### Post by yetimon_64 on 2019-05-29
> **Autodave said:**
> You have 11.4 installed????  Really?  That version was dead many years ago.  Please let us know what version you are running.
Wow, that is a VERY old live disc, I missed seeing that. +1.

---

### Post by Autodave on 2019-05-29
IF you are indeed using 11.4, that could very well be the cause of the whistling noise.  Those old drivers running something newer: not a good thing usually.

---

### Post by iamtheeggman2 on 2020-03-04
Further to this old thread, I just went th rough a massive update on windows 10, it took the computer 30 minutes to log into the desktop after startup and the whistle has completely vanished when windows is running, is there really no way I can jiggle around with the drivers in question to sort this annoying whistle?

---

### Post by yetimon_64 on 2020-03-04
> **iamtheeggman2 said:**
> ...is there really no way I can jiggle around with the drivers in question to sort this annoying whistle?Drivers are included with the kernel in Ubuntu as modules. You generally don't manage driver issues the same as in Windows, so basically "no".

**Question:** Are you really using a live disk from **2011** as indicated in your first post ?
IF you are using a live disk download a currently supported LTS release like 18.04 and test the hardware and sound again.
Running a horribly out of date dead release will never help you troubleshoot an issue like sound problems. Your first post would tend to suggest you only use Ubuntu from a live disk. Have you installed a dual boot setup there?

As indicated by Autodave in May last year "**Please let us know what version you are running**." As well as the release number also any flavors, eg, Xubuntu Kubuntu etc, used if not the default Ubuntu install. Different DEs may not always be the same for sound issues.

---

