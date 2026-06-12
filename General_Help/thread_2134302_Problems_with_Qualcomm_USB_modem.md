---
title: "Problems with Qualcomm USB modem"
date: 2013-04-10
forum: General Help
---

### Post by NomadAU on 2013-04-10
Hi,

I originally posted to the Networking forum on this problem ([http://ubuntuforums.org/showthread.php?t=2131762](http://ubuntuforums.org/showthread.php?t=2131762)), but after a lot of reads, and no replies, I'm beginning to think I've asked the wrong question. 

So, I'll reframe the question differently...

What component (or components) in Ubuntu 12.04 LTS are responsible for calling the qcserial code when I boot up my Thinkpad?  

So far, I'm aware of **udev** being involved, and believe the udev daemon (**udevd**) is called by the kernel when a **device** is **added** or **removed**.
In my /lib/udev/rules.d I have a rule file called 60-gobi.rules, containing a line 
```
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9204", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
```

So, on bootup, the Qualcomm Gobi 2000 card (inside my ThinkPad), is recognised by the kernel, and its details are passed to udevd.  The udevd looks in its rules files for a match on the device (vendor and product id) and then calls the **gobi_loader** executable passing the parms specified in the matching rule. 
On successful execution of the gobi_loader, dmesg will show something like the following
```
[ 28.528884] USB Serial support registered for Qualcomm USB modem
[ 28.530017] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
[ 28.530148] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
[ 28.532168] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
[ 28.532335] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB1
[ 28.533344] qcserial 2-1.4:1.3: Qualcomm USB modem converter detected
[ 28.533568] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB2
```

Then some magic happens, that I don't understand, which lets my Network Manager use the device for 3G wireless...so far so good.

Some time later, and I think it is related to performing a Suspend followed by Resume, the following entries are seen using dmesg.
```
[ 190.935461] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 190.935664] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[ 190.935868] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
```

Thereafter, I can no longer see my wireless card, and of course, can't use my 3G.

I am trying to figure out what event or activity in the Ubuntu OS will call gobi_loader to disconnect the device?

More importantly, how can I **re-drive** the initial boot-up behaviour so that my device is recognised again, and reinstalled **without** having to reboot?

Hopefully someone out there will be able to shed some light on the inner workings of kernel, udev, devices...and Suspend/Resume.

I should also add, that the HW combination (ThinkPad W510, and Qualcomm Gobi 2000) works just fine under RedHat EL...so IMHO the hardware combination is not the issue here.  It's something specific to Ubuntu...

---

