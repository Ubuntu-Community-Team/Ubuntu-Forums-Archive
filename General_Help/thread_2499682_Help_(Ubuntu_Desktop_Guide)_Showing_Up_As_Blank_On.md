---
title: "Help (Ubuntu Desktop Guide) Showing Up As Blank On Ubuntu 24.04 LTS"
date: 2024-08-06
forum: General Help
---

### Post by john_jr2 on 2024-08-06
Hello,

Does anyone know how to fix the Help (Ubuntu Desktop Guide, the blue question mark icon in the panel that comes with Ubuntu 24.04 LTS et cetera) when it shows up as blank instead of showing information on how to use Ubuntu?

Screenshot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294060&stc=1[/IMG]

So far I have tried this without any luck: I checked for & installed updates in the App Center and Software Center, I have opened a terminal & run sudo apt update and sudo apt install yelp.

Thank you.

---

### Post by guiverc on 2024-08-07
If you need the info quick; you can get details from [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

Sorry I'm not *currently* using Ubuntu Desktop or GNOME, so I don't have the application appearing on my desktop currently for me to explore further. I did boot a Ubuntu 24.04 LTS *daily* ISO on a nearby machine to confirm what I see matches the link I provided, but can't look further [currently] sorry; I didn't get a blank/white screen on my quick boot in a *live* environment.

---

### Post by tea for one on 2024-08-07
Try opening the Ubuntu Desktop Guide via the terminal.
It may produce error messages?
```
yelp
```

---

### Post by john_jr2 on 2024-08-07
> **tea for one said:**
> Try opening the Ubuntu Desktop Guide via the terminal.
It may produce error messages?
```
yelp
```

Thank you, it still opens blank, I noticed that when I hover over the blankness, sometimes hover text appears.

In terminal, this error keeps repeating: "AcceleratedSurfaceDMABuf was unable to construct a complete framebuffer"

Also, here is my system details, I cleaned installed Ubuntu 24.04 LTS back when I installed it, and my Nvidia driver is the 535 driver.

Another issue that I have is that 50% of the time Ubuntu does not shut down, the screen goes black eventually, but it is not really shut down.

I wonder if both issues are related to my graphics card & the drivers?

I had the shutdown issue on Ubuntu 22.04 LTS as well, with a different driver, but probably not as often.

# System Details Report
---


## Report details
- **Date generated:**                              2024-08-07 09:51:58


## Hardware Information:
- **Hardware Model:**                              Acer Aspire TC-780
- **Memory:**                                      12.0 GiB
- **Processor:**                                   Intel® Core&#8482; i5-7400 × 4
- **Graphics:**                                    NVIDIA GeForce GT 1030
- **Disk Capacity:**                               2.0 TB


## Software Information:
- **Firmware Version:**                            R02-B2
- **OS Name:**                                     Ubuntu 24.04 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.8.0-39-generic

---

### Post by tea for one on 2024-08-07
> **john_jr2 said:**
> I wonder if both issues are related to my graphics card & the drivers?
Possibly/probably?
Unfortunately, I cannot offer further advice as I do not have a Nvidia GPU.

If you boot into a "Try Ubuntu" live session, can you view the Help application?

---

### Post by him610 on 2024-08-07
If it is any help, here is link to Ubuntu Desktop Guide [https://help.ubuntu.com/stable/ubuntu-help/]("https://help.ubuntu.com/stable/ubuntu-help/")

---

### Post by nhassan42 on 2024-08-10
I'm facing the same Issue, updated everything and still showing blank screen

---

### Post by him610 on 2024-08-10
You might consider clearing your cache and cookies; it might help.

---

### Post by currentshaft on 2024-08-10
.

---

### Post by john_jr2 on 2024-08-11
> **tea for one said:**
> Possibly/probably?
Unfortunately, I cannot offer further advice as I do not have a Nvidia GPU.

If you boot into a "Try Ubuntu" live session, can you view the Help application?

Thank you, I tried booting an Ubuntu live session, and the same thing happened there as well.

---

### Post by john_jr2 on 2024-08-11
Wow! That worked, thank you very much, Currentshaft!

> **currentshaft said:**
> Try this:

export WEBKIT_DISABLE_COMPOSITING_MODE=1
export WEBKIT_DISABLE_DMABUF_RENDERER=1
export WEBKIT_DMABUF_RENDERER_DISABLE_GBM=1
yelp

---

### Post by currentshaft on 2024-08-11
?

---

### Post by mastermindg on 2024-09-08
Adding this to `.bashrc` will allow you to launch Help from anywhere and work appropriately:

```
export WEBKIT_DISABLE_COMPOSITING_MODE=1
export WEBKIT_DISABLE_DMABUF_RENDERER=1
export WEBKIT_DMABUF_RENDERER_DISABLE_GBM=1
```

---

