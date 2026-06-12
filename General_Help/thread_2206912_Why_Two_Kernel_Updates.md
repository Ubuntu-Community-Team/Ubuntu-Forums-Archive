---
title: "Why Two Kernel Updates?"
date: 2014-02-21
forum: General Help
---

### Post by akacheebe2 on 2014-02-21
This is new ground for me as I've never done anything with the old kernels before.  This computer is running Ubuntu 12.04 with Mate and is one of 3 that I have on my home network but this issue doesn't appear on the other systems.

Problem I'm having is whenever a new kernel update comes along this one computer not only updates the 3.5.0 kernel but it also downloads and updates the old 3.2.0 kernel as well?  I've been searching the web trying to find out how to remove the old 3.2.0 kernel and the simplest way seems to be through Synaptic Package Manager, which I have installed on my systems.  

When I open Synaptic and look for "linux-image" I get a bunch of 3.5.0 along with many 3.2.0 shown and from what I've read all I need to do is check the 3.2.0 kernel image for removal.  But then I go search for "linux-header" and I only have two show up and BOTH are 3.2.0?  NO 3.5.0 header is listed??

According to the article I saw online, I'm suppose to remove the 3.2.0 headers but if I do that then there won't be ANY "linux-header" left and I'm afraid I'll break Ubuntu.

So, can someone tell me why I only have the linux-header for 3.2.0 and also how to completely remove the old 3.2.0 kernel so I won't have to continue to waste bandwidth downloading updates for TWO kernels?

Thanks

---

### Post by monkeybrain20122 on 2014-02-21
You should remove some old kernels. In synaptic look at autoremovable.

---

### Post by akacheebe2 on 2014-02-21
> **monkeybrain20122 said:**
> You should remove some old kernels. In synaptic look at autoremovable.

So what about the missing 3.5.0 linux-header?

---

### Post by monkeybrain20122 on 2014-02-21
You should have two header files (linux header and linux header generic) and two images (image and image-extras) for each kernel version.  The headers should be installed with each kernel upgrade, I have no idea why they are missing. Can you just install them with synaptic?

---

### Post by akacheebe2 on 2014-02-21
> **monkeybrain20122 said:**
> You should remove some old kernels. In synaptic look at autoremovable.

Humm, this is weird?  Went back into Synaptic and searched for  "linux-header" again and found a dozen or more of both 3.2 and 3.5??  I swear there was only two on that page before and they were 3.2.0???  :confused:

Ok so that problem has resolved itself but pray tell what do you mean by "look at autoremovable" because nothing shows up in Synaptic when I search for that and there's nothing about it in the menus across the top of that page?

---

### Post by monkeybrain20122 on 2014-02-21
> **akacheebe2 said:**
> Humm, this is weird?  Went back into Synaptic and searched for  "linux-header" again and found a dozen or more of both 3.2 and 3.5??  I swear there was only two on that page before and they were 3.2.0???  :confused:

Ok so that problem has resolved itself but pray tell what do you mean by "look at autoremovable" because nothing shows up in Synaptic when I search for that and there's nothing about it in the menus across the top of that page?

You only need to keep two kernels, one is your current one, the other is the previous version supposedly for fallback in case the update has broken something. Anything older would be autoremovable in Ubuntu and you can clean them in synaptic or just 
```
sudo apt-get autoremove
```
The command line is actually better in this case because with synaptic you have to click and check each entry for removal.

It is good to remove old kernels because they take up space. If you run LTS and have a small / partition you may run out of space if you accumulate too many old kernels over the lifespan of the OS. You have nothing to autoremove because you have only two kernels at the moment.

---

### Post by Dave_L on 2014-02-21
In synaptic, select "Status" in the lower left pane, "Installed" in the upper left pane, and "3.2.0" in the Quick filter box.

Which packages are listed?

---

### Post by akacheebe2 on 2014-02-21
> **Dave_L said:**
> In synaptic, select "Status" in the lower left pane, "Installed" in the upper left pane, and "3.2.0" in the Quick filter box.

Which packages are listed?

I've got a ton of 3.2.0* stuff, probably about 60 items?

---

### Post by Dave_L on 2014-02-21
Are all those 60 items **installed**?

---

### Post by akacheebe2 on 2014-02-21
> **Dave_L said:**
> Are all those 60 items **installed**?

I guess so as they have a green square in the far left column of each one.  When I removed other stuff that green square turns white.

---

### Post by Impavidus on 2014-02-21
> **monkeybrain20122 said:**
> You only need to keep two kernels, one is your current one, the other is the previous version supposedly for fallback in case the update has broken something. Anything older would be autoremovable in Ubuntu and you can clean them in synaptic or just 
```
sudo apt-get autoremove
```
The command line is actually better in this case because with synaptic you have to click and check each entry for removal.

It is good to remove old kernels because they take up space. If you run LTS and have a small / partition you may run out of space if you accumulate too many old kernels over the lifespan of the OS. You have nothing to autoremove because you have only two kernels at the moment.
Not yet in 12.04. The feature to autoremove old kernels was added later.

---

### Post by philinux on 2014-02-21
Op make sure you have linux-generic installed.

see link in sig below to remove old kernels.

Step 6. Do the dry run first off course.

---

### Post by akacheebe2 on 2014-02-21
Ran the autoremove command earlier today and it didn't remove any old kernels.  Here is what I got on here now.

```
-Dimension-8400:~$ dpkg -l linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-doc-3.2. <none>         (no description available)
ii  linux-firmware 1.79.9         Firmware for Linux kernel drivers
ii  linux-generic- 3.5.0.46.52    Generic Linux kernel image and headers
ii  linux-generic- 3.2.0.58.69    Complete Generic Linux kernel
un  linux-headers  <none>         (no description available)
un  linux-headers- <none>         (no description available)
un  linux-headers- <none>         (no description available)
ii  linux-headers- 3.2.0-23.36    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-23.36    Linux kernel headers for version 3.2.0 on 64
ii  linux-headers- 3.2.0-29.46    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-29.46    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-30.48    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-30.48    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-31.50    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-31.50    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-32.51    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-32.51    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-33.52    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-33.52    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-34.53    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-34.53    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-35.55    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-35.55    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-36.57    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-36.57    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-37.58    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-37.58    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-38.61    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-38.61    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-39.62    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-39.62    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-40.64    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-40.64    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-41.66    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-41.66    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-43.68    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-43.68    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-44.69    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-44.69    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-45.70    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-45.70    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-48.74    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-48.74    Linux kernel headers for version 3.2.0 on 32
un  linux-headers- <none>         (no description available)
un  linux-headers- <none>         (no description available)
ii  linux-headers- 3.2.0-51.77    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-51.77    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-52.78    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-52.78    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-53.81    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-53.81    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-54.82    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-54.82    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-55.85    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-55.85    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-56.86    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-56.86    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-57.87    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-57.87    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.2.0-58.88    Header files related to Linux kernel version
ii  linux-headers- 3.2.0-58.88    Linux kernel headers for version 3.2.0 on 32
ii  linux-headers- 3.5.0-28.48~pr Header files related to Linux kernel version
un  linux-headers- <none>         (no description available)
ii  linux-headers- 3.5.0-30.51~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-30.51~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-31.52~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-31.52~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-32.53~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-32.53~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-34.55~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-34.55~pr Linux kernel headers for version 3.5.0 on 32
un  linux-headers- <none>         (no description available)
un  linux-headers- <none>         (no description available)
ii  linux-headers- 3.5.0-37.58~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-37.58~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-39.60~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-39.60~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-40.62~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-40.62~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-41.64~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-41.64~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-42.65~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-42.65~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-43.66~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-43.66~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-44.67~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-44.67~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-45.68~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-45.68~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0-46.70~pr Header files related to Linux kernel version
ii  linux-headers- 3.5.0-46.70~pr Linux kernel headers for version 3.5.0 on 32
ii  linux-headers- 3.5.0.46.52    Generic Linux kernel headers
ii  linux-headers- 3.2.0.58.69    Generic Linux kernel headers
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
ii  linux-image-3. 3.2.0-23.36    Linux kernel image for version 3.2.0 on 64 b
ii  linux-image-3. 3.2.0-29.46    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-30.48    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-31.50    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-32.51    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-33.52    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-34.53    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-35.55    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-36.57    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-37.58    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-38.61    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-39.62    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-40.64    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-41.66    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-43.68    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-44.69    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-45.70    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-48.74    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-49.75    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-51.77    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-52.78    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-53.81    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-54.82    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-55.85    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-56.86    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-57.87    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.2.0-58.88    Linux kernel image for version 3.2.0 on 32 b
ii  linux-image-3. 3.5.0-28.48~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-30.51~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-31.52~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-32.53~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-34.55~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-36.57~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-37.58~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-39.60~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-40.62~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-41.64~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-42.65~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-43.66~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-44.67~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-45.68~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-3. 3.5.0-46.70~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-ge 3.5.0.46.52    Generic Linux kernel image
ii  linux-image-ge 3.2.0.58.69    Generic Linux kernel image
un  linux-initramf <none>         (no description available)
un  linux-kernel-h <none>         (no description available)
un  linux-kernel-l <none>         (no description available)
ii  linux-libc-dev 3.2.0-59.90    Linux Kernel Headers for development
un  linux-lts-quan <none>         (no description available)
un  linux-lts-quan <none>         (no description available)
un  linux-lts-quan <none>         (no description available)
un  linux-restrict <none>         (no description available)
ii  linux-sound-ba 1.0.25+dfsg-0u base package for ALSA and OSS sound systems
un  linux-source-3 <none>         (no description available)
un  linux-tools    <none>         (no description available)

```

---

### Post by akacheebe2 on 2014-02-23
Well, I ran that one line kernel cleanup but I've still got TWO kernels installed just like before?

```
Dimension-8400:~$ dpkg -l linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version                          Description
+++-================================-================================-================================================================================
un  linux-doc-3.2.0                  <none>                           (no description available)
ii  linux-firmware                   1.79.9                           Firmware for Linux kernel drivers
ii  linux-generic-lts-quantal        3.5.0.46.52                      Generic Linux kernel image and headers
ii  linux-generic-pae                3.2.0.59.70                      Complete Generic Linux kernel
un  linux-headers                    <none>                           (no description available)
un  linux-headers-3                  <none>                           (no description available)
un  linux-headers-3.0                <none>                           (no description available)
un  linux-headers-3.2.0-23           <none>                           (no description available)
un  linux-headers-3.2.0-23-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-29           <none>                           (no description available)
un  linux-headers-3.2.0-29-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-30           <none>                           (no description available)
un  linux-headers-3.2.0-30-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-31           <none>                           (no description available)
un  linux-headers-3.2.0-31-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-32           <none>                           (no description available)
un  linux-headers-3.2.0-32-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-33           <none>                           (no description available)
un  linux-headers-3.2.0-33-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-34           <none>                           (no description available)
un  linux-headers-3.2.0-34-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-35           <none>                           (no description available)
un  linux-headers-3.2.0-35-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-36           <none>                           (no description available)
un  linux-headers-3.2.0-36-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-37           <none>                           (no description available)
un  linux-headers-3.2.0-37-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-38           <none>                           (no description available)
un  linux-headers-3.2.0-38-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-39           <none>                           (no description available)
un  linux-headers-3.2.0-39-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-40           <none>                           (no description available)
un  linux-headers-3.2.0-40-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-41           <none>                           (no description available)
un  linux-headers-3.2.0-41-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-43           <none>                           (no description available)
un  linux-headers-3.2.0-43-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-44           <none>                           (no description available)
un  linux-headers-3.2.0-44-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-45           <none>                           (no description available)
un  linux-headers-3.2.0-45-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-48           <none>                           (no description available)
un  linux-headers-3.2.0-48-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-49           <none>                           (no description available)
un  linux-headers-3.2.0-49-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-51           <none>                           (no description available)
un  linux-headers-3.2.0-51-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-52           <none>                           (no description available)
un  linux-headers-3.2.0-52-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-53           <none>                           (no description available)
un  linux-headers-3.2.0-53-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-54           <none>                           (no description available)
un  linux-headers-3.2.0-54-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-55           <none>                           (no description available)
un  linux-headers-3.2.0-55-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-56           <none>                           (no description available)
un  linux-headers-3.2.0-56-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-57           <none>                           (no description available)
un  linux-headers-3.2.0-57-generic-p <none>                           (no description available)
un  linux-headers-3.2.0-58           <none>                           (no description available)
un  linux-headers-3.2.0-58-generic-p <none>                           (no description available)
ii  linux-headers-3.2.0-59           3.2.0-59.90                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic-p 3.2.0-59.90                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
un  linux-headers-3.5.0-28           <none>                           (no description available)
un  linux-headers-3.5.0-28-generic   <none>                           (no description available)
un  linux-headers-3.5.0-30           <none>                           (no description available)
un  linux-headers-3.5.0-30-generic   <none>                           (no description available)
un  linux-headers-3.5.0-31           <none>                           (no description available)
un  linux-headers-3.5.0-31-generic   <none>                           (no description available)
un  linux-headers-3.5.0-32           <none>                           (no description available)
un  linux-headers-3.5.0-32-generic   <none>                           (no description available)
un  linux-headers-3.5.0-34           <none>                           (no description available)
un  linux-headers-3.5.0-34-generic   <none>                           (no description available)
un  linux-headers-3.5.0-36           <none>                           (no description available)
un  linux-headers-3.5.0-36-generic   <none>                           (no description available)
un  linux-headers-3.5.0-37           <none>                           (no description available)
un  linux-headers-3.5.0-37-generic   <none>                           (no description available)
un  linux-headers-3.5.0-39           <none>                           (no description available)
un  linux-headers-3.5.0-39-generic   <none>                           (no description available)
un  linux-headers-3.5.0-40           <none>                           (no description available)
un  linux-headers-3.5.0-40-generic   <none>                           (no description available)
un  linux-headers-3.5.0-41           <none>                           (no description available)
un  linux-headers-3.5.0-41-generic   <none>                           (no description available)
un  linux-headers-3.5.0-42           <none>                           (no description available)
un  linux-headers-3.5.0-42-generic   <none>                           (no description available)
un  linux-headers-3.5.0-43           <none>                           (no description available)
un  linux-headers-3.5.0-43-generic   <none>                           (no description available)
un  linux-headers-3.5.0-44           <none>                           (no description available)
un  linux-headers-3.5.0-44-generic   <none>                           (no description available)
un  linux-headers-3.5.0-45           <none>                           (no description available)
un  linux-headers-3.5.0-45-generic   <none>                           (no description available)
ii  linux-headers-3.5.0-46           3.5.0-46.70~precise1             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic   3.5.0-46.70~precise1             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-quanta 3.5.0.46.52                      Generic Linux kernel headers
ii  linux-headers-generic-pae        3.2.0.59.70                      Generic Linux kernel headers
un  linux-image                      <none>                           (no description available)
un  linux-image-3.0                  <none>                           (no description available)
un  linux-image-3.2.0-23-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-29-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-30-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-31-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-32-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-33-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-34-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-35-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-36-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-37-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-38-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-39-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-40-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-41-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-43-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-44-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-45-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-48-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-49-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-51-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-52-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-53-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-54-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-55-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-56-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-57-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-58-generic-pae <none>                           (no description available)
ii  linux-image-3.2.0-59-generic-pae 3.2.0-59.90                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
un  linux-image-3.5.0-28-generic     <none>                           (no description available)
un  linux-image-3.5.0-30-generic     <none>                           (no description available)
un  linux-image-3.5.0-31-generic     <none>                           (no description available)
un  linux-image-3.5.0-32-generic     <none>                           (no description available)
un  linux-image-3.5.0-34-generic     <none>                           (no description available)
un  linux-image-3.5.0-36-generic     <none>                           (no description available)
un  linux-image-3.5.0-37-generic     <none>                           (no description available)
un  linux-image-3.5.0-39-generic     <none>                           (no description available)
un  linux-image-3.5.0-40-generic     <none>                           (no description available)
un  linux-image-3.5.0-41-generic     <none>                           (no description available)
un  linux-image-3.5.0-42-generic     <none>                           (no description available)
un  linux-image-3.5.0-43-generic     <none>                           (no description available)
un  linux-image-3.5.0-44-generic     <none>                           (no description available)
un  linux-image-3.5.0-45-generic     <none>                           (no description available)
ii  linux-image-3.5.0-46-generic     3.5.0-46.70~precise1             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal  3.5.0.46.52                      Generic Linux kernel image
ii  linux-image-generic-pae          3.2.0.59.70                      Generic Linux kernel image
un  linux-initramfs-tool             <none>                           (no description available)
un  linux-kernel-headers             <none>                           (no description available)
un  linux-kernel-log-daemon          <none>                           (no description available)
ii  linux-libc-dev                   3.2.0-59.90                      Linux Kernel Headers for development
un  linux-lts-quantal-doc-3.5.0      <none>                           (no description available)
un  linux-lts-quantal-source-3.5.0   <none>                           (no description available)
un  linux-lts-quantal-tools          <none>                           (no description available)
un  linux-restricted-common          <none>                           (no description available)
ii  linux-sound-base                 1.0.25+dfsg-0ubuntu1.1           base package for ALSA and OSS sound systems
un  linux-source-3.2.0               <none>                           (no description available)
un  linux-tools                      <none>                           (no description available)

```

---

### Post by Dave_L on 2014-02-23
Doesn't "un" mean uninstalled?

What's the output from:

```
dpkg -l '*3.2.0-*'
```

---

### Post by Akacheebe on 2014-02-23
They got my old username back but it's still me. 

I looked in Synaptic and it shows green squares next to the 3.2.0 kernel and also on the 3.5.0 kernel. Here's the result of that entry. 

```
Dimension-8400:~$ dpkg -l '*3.2.0-*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                            Description
+++-==================================-==================================-====================================================================================
un  linux-headers-3.2.0-23             <none>                             (no description available)
un  linux-headers-3.2.0-23-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-29             <none>                             (no description available)
un  linux-headers-3.2.0-29-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-30             <none>                             (no description available)
un  linux-headers-3.2.0-30-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-31             <none>                             (no description available)
un  linux-headers-3.2.0-31-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-32             <none>                             (no description available)
un  linux-headers-3.2.0-32-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-33             <none>                             (no description available)
un  linux-headers-3.2.0-33-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-34             <none>                             (no description available)
un  linux-headers-3.2.0-34-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-35             <none>                             (no description available)
un  linux-headers-3.2.0-35-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-36             <none>                             (no description available)
un  linux-headers-3.2.0-36-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-37             <none>                             (no description available)
un  linux-headers-3.2.0-37-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-38             <none>                             (no description available)
un  linux-headers-3.2.0-38-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-39             <none>                             (no description available)
un  linux-headers-3.2.0-39-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-40             <none>                             (no description available)
un  linux-headers-3.2.0-40-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-41             <none>                             (no description available)
un  linux-headers-3.2.0-41-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-43             <none>                             (no description available)
un  linux-headers-3.2.0-43-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-44             <none>                             (no description available)
un  linux-headers-3.2.0-44-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-45             <none>                             (no description available)
un  linux-headers-3.2.0-45-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-48             <none>                             (no description available)
un  linux-headers-3.2.0-48-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-49             <none>                             (no description available)
un  linux-headers-3.2.0-49-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-51             <none>                             (no description available)
un  linux-headers-3.2.0-51-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-52             <none>                             (no description available)
un  linux-headers-3.2.0-52-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-53             <none>                             (no description available)
un  linux-headers-3.2.0-53-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-54             <none>                             (no description available)
un  linux-headers-3.2.0-54-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-55             <none>                             (no description available)
un  linux-headers-3.2.0-55-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-56             <none>                             (no description available)
un  linux-headers-3.2.0-56-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-57             <none>                             (no description available)
un  linux-headers-3.2.0-57-generic-pae <none>                             (no description available)
un  linux-headers-3.2.0-58             <none>                             (no description available)
un  linux-headers-3.2.0-58-generic-pae <none>                             (no description available)
ii  linux-headers-3.2.0-59             3.2.0-59.90                        Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic-pae 3.2.0-59.90                        Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
un  linux-image-3.2.0-23-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-29-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-30-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-31-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-32-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-33-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-34-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-35-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-36-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-37-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-38-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-39-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-40-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-41-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-43-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-44-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-45-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-48-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-49-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-51-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-52-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-53-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-54-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-55-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-56-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-57-generic-pae   <none>                             (no description available)
un  linux-image-3.2.0-58-generic-pae   <none>                             (no description available)
ii  linux-image-3.2.0-59-generic-pae   3.2.0-59.90                        Linux kernel image for version 3.2.0 on 32 bit x86 SMP
Dimension-8400:~$ 

```

---

### Post by Dave_L on 2014-02-23
The only ones of those 3.2.0 packages that are installed are:
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic-pae
linux-image-3.2.0-59-generic-pae

So those are the ones you should uninstall, if you want to get rid of 3.2.0.

---

### Post by Akacheebe on 2014-02-24
Yeah, the idea is to get rid of stuff that's not being used so I don't have to waste bandwidth downloading it in the future.

So should I try to remove them via Synaptic?  I've read where it's easy to really hork up stuff using Synaptic to do this?

Thanks

---

### Post by Dave_L on 2014-02-24
If you're running a newer kernel, e.g. 3.5.0, there should be no problem removing those three packages with synaptic. I do the same thing to get rid of old kernels (I keep only the two previous kernels). I use the "remove completely" function, although I don't know if that matters. 

But you may want to wait for someone else to confirm this.

---

### Post by Impavidus on 2014-02-24
If you're running the 3.5 kernel you can uninstall the packages referring to the 3.2 kernel. Synaptic should tell you it will also uninstall the metapackage that pulls in the new versions of the 3.2 kernel whenever they come available. If it tells you it will uninstall something you don't trust, abort.

Also, I'm not sure of this: are all kernel lines of Precise supported until 2017 or only the original (3.2) and the last one (3.11?)? I think I read somewhere that support for 3.5 and the other one I forget here would be dropped earlier.

---

### Post by Akacheebe on 2014-02-24
This system must have upgraded to 3.5.0 on it's own as I didn't install that kernel?  

I did a clean install the other day for a friend using 12.04.4 and that one has 3.11.0 in it by default?  So if 3.5.0 isn't LTS then I can upgrade to 3.11.0 can't I?

---

### Post by Dave_L on 2014-02-24
You can install 3.11.0 by installing the metapackage linux-generic-lts-saucy. I've been using it for almost two months on Ubuntu 12.04.

For more details see: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Has your original problem been solved?

---

### Post by ibjsb4 on 2014-02-24
Kernels 3.2; 3.5; 3.8; 3.11 they are all available in 12.04 repositories.

---

### Post by Akacheebe on 2014-02-24
> **Dave_L said:**
> Has your original problem been solved?  Well actually no.  I haven't uninstalled the 3.2.0 kernel yet.  I've got to talk myself into it as this is one of those "first time" deals for me.  Will probably do that tonight when I go in the house and get on that computer.  Right now I'm out in my garage on another system.    

Once I've successfully done that I'll mark this thread solved.  If something goes wrong then I'll probably be back in here looking for help to fix it.  

Thanks  

EDIT:  If I go to synaptic and try to install 3.11.0 will it automatically install the rest of the stuff needed to make it work?

---

### Post by Dave_L on 2014-02-24
> **Akacheebe said:**
> If I go to synaptic and try to install 3.11.0 will it automatically install the rest of the stuff needed to make it work?

Yes. The only package you need to explicitly install is "linux-generic-lts-saucy".

---

### Post by Akacheebe on 2014-02-24
Kernel 3.2.0 is now officially gone and I've successfully rebooted twice.  Only one listed now is 3.5.0-46 which was installed last week.    Maybe try the 3.11.0 upgrade tomorrow but will start another thread if I have problems.  Thanks guys!!

---

### Post by Akacheebe on 2014-03-06
> **philinux said:**
> Op make sure you have linux-generic installed.

see link in sig below to remove old kernels.

Step 6. Do the dry run first off course.

I've got a question about this one line old kernel removal tool in your signature.  As you know from the last post I made I did  an upgrade to 3.11.0-17 on my 3 desktop systems but was  waiting for an upgrade to -18 before I ran the command to remove all the  3.5.0 kernel stuff.  Well, today that -18 kernel update showed  up so I ran the old kernel removal command in terminal and next thing I know, this  computer was upgrading the 3.5.0 kernal before it was going to remove  it???  It said it was going to download 53MB of updates for 3.5.0 before  it uninstalled it???  Having see that I just closed the terminal and stopped it!!

This kinda seems dumb to me as I'm wasting bandwidth for an upgrade that will be removed 10 minutes later??  

Am I missing something here??

Thanks

---

### Post by Impavidus on 2014-03-06
One-line kernel revomal tools aren't that smart. I think you got updates for both the 3.11 and 3.5 kernels at the same time, so you just started upgrading both, intending to remove the 3.5 kernel immediately afterwards. You can order your system to upgrade just the 3.11 kernel instead of applying all upgrades and then remove the 3.5 kernel. I can't think of any oneliners to do that. Besides, it seems this kernel removal oneliner removes all old kernels. I always keep one, just to be sure. Killing the upgrade process can lead to problems, but I think you killed it during the download phase, which should be fine.

---

### Post by Akacheebe on 2014-03-07
Impavidus thanks for your reply. You're right that it was going to update both the 3.11.0 and 3.5.0 kernels.  That is why I ran that one line removal tool but like I said, next thing I know it's downloading 53MB of updates for the3.5.0?  

Ennywho, I guess I can go in Synaptic and remove the 3.5.0 stuff one by one and see how that works since I've install the 3.11.0-18 kernel and still have -17 as a backup.

---

