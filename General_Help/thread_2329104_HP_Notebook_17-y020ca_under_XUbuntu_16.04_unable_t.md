---
title: "HP Notebook 17-y020ca under XUbuntu 16.04 unable to resume from suspend"
date: 2016-06-28
forum: General Help
---

### Post by Nathaniel_Osgood on 2016-06-28
I recently purchased an HP Notebook 17-y020ca and installed Ubuntu 16.04. I originally had to overcome some WiFi issues with the Broadcom Corporation BCM43142 wireless card, but now that side of things appears to be working well. 


Unfortunately, there is a fatal issue remaining: the laptop is completely unable to resume after suspending.  This behavior is deterministic -- while suspend appears to place the computer in a standard "suspended" state (with a slowly blinking light), a resume following a suspension yields a slightly glowing screen with no text or indication of display of any content.  Perhaps most notably, the disk light flickers occasionally (suggesting that some processes remain active), but the computer is completely unresponsive.


Control-Alt-F1 (which normally brings me to another console) does nothing  While it is possible that this is simply a display problem, I have not been able to escape via anything but a complete shutdown.

As the video device is often suspect in these sort of problems, I would note that the information on my video card (as output from  "lspci -vnn | grep -A12 VGA") is as follows:


```

>00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Carrizo [1002:9874] (rev ca) (prog-if 00 [VGA controller])
>    DeviceName: ATI UMA EG BROADWAY
>    Subsystem: Hewlett-Packard Company Carrizo [103c:8221]
>    Flags: bus master, fast devsel, latency 0, IRQ 226
>    Memory at e0000000 (64-bit, prefetchable) [size=256M]
>    Memory at f0000000 (64-bit, prefetchable) [size=8M]
>    I/O ports at 3000 [size=256]
>    Memory at f0d00000 (32-bit, non-prefetchable) [size=256K]
>    Expansion ROM at f0d80000 [disabled] [size=128K]
>    Capabilities: [48] Vendor Specific Information: Len=08 <?>
>    Capabilities: [50] Power Management version 3
>    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
>    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+`

``` 


Contents of/var/log/pm-suspend.log on my computer can be found here: [http://paste.ubuntu.com/18010440/](http://paste.ubuntu.com/18010440/)


The following is the contents of my /proc/cmdline


`BOOT_IMAGE=/vmlinuz-4.4.0-21-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7`

Please note that an upgrade of the kernel to 4.4.8 (as advocated on many other threads involving suspend/resume problems) does not solve this problem.

While I have investigated it less closely, I would note that hibernate/unhibernate also reliably fails on this machine.

I would be truly grateful for any suggestions that anyone could give.  I would be happy to share output from journalctl, dmesg or other tools if readers think that this may be of help.  I much appreciate your consideratoin!


Sincerely,

Nathaniel Osgood

---

### Post by mastablasta on 2016-06-28
if you suspect the GPU driver then check if it's power management features are propperly enabled.

also check BIOS settings for various ACPI features and such. perhaps some of them do not work or do not work propperly in Linux. hard to say, but usually the laptop manual would have plenty of such information

---

### Post by Nathaniel_Osgood on 2016-06-28
Thanks -- I have checked both of these, and definitely see no ACPI or obvious GPU settings problems.  Please note that have no particular reason to suspect the amdgpu driver at issue for my problem; it is simply that video cards are often implicated in suspend/resume problems.

---

### Post by mastablasta on 2016-06-29
oh AMDGPU... that's preety much a beta driver.

is powerplay enabled?: [SIZE=2]https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PP-4.5-Steps
[/SIZE]

---

### Post by Nathaniel_Osgood on 2016-06-29
Thanks, but my understanding is that as of 16.04 amdgpu has now replaced fglrx as the standard driver for the the AMD graphics drivers (including, I had thought AMD Radeon 5 card series carried by the model of HP laptop that I am using).  I would be grateful to know if I am mistaken on this.

I appreciate you mentioning  the powerplay question and will look into this.

---

### Post by mastablasta on 2016-06-29
> Advanced Micro Devices, Inc. [AMD/ATI] Carrizo [1002:9874]

That's AMD Radeon R7 chip, which itself is relatively new.

edit: it seems there is also an R5 version

---

### Post by Nathaniel_Osgood on 2016-06-29
Apologies, but I didn't get the implications of your note.  The computer at issue indeed has a AMD Radeon R5 processor, which I believe is significantly older than the R7. I would certainly welcome learning if there is more appropriate driver for 16.04.

---

### Post by Nathaniel_Osgood on 2016-07-03
After much research, experimentation and observation, I found the problem above that was the machine was indeed resuming almost entirely -- it was simply not properly setting the video state so that the monitor was on and displaying contents.  I am not sure if this was due to a bug in the amdgpu driver, elsewhere in the kernel, but I found that the easiest way to resolve this was to ignore the man page information for pm-suspend regarding the antiquated character of "--quirk-radeon-off", and indeed to  use that option as follows:


**pm-suspend --quirk-radeon-off**


Upon resuming, the system resets the video card in the correct state, and the system works well.


I appreciate all of those who gave my problem thought.  I hope that this discovery is of use to others with HP Pavilion laptops, or other similar laptops.

---

### Post by c.laudia on 2016-08-21
Hello Nathaniel,

it seems that I have the same problem with my HP Pavilion, so I wanted to try if your solution works for me as well.
Can you tell me where exactly (which file..) I have to add "**pm-suspend --quirk-radeon-off"** ?

Thanks
Claudia

---

