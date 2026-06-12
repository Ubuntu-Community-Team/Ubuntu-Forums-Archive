---
title: "Not able to boot into ubuntu 16.04 after update"
date: 2019-02-11
forum: General Help
---

### Post by surfnraven on 2019-02-11
I was prompted to update Chrome and then my UniFi (Ubiquiti) software this morning and then prompted for a restart.
It all seemed innocent enough, but now I can't get back in :(
Anyway, the bios splash screen comes up and then nothing happens.
I'm able to boot into a live "cd" (usb) on the machine. Also, I'm able to access the drive with the installation(s) on it from the live CD and I see the filesystems.

Here's what I've tried.
I followed the directions on things to try at (as well as other links that appeared to be similar):
[https://ubuntuforums.org/showthread.php?p=10871917#post10871917](https://ubuntuforums.org/showthread.php?p=10871917#post10871917)
[https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)
Neither shift or tab seems to bring up grub during a boot.

So I tried boot-repair and it seemed to work, but still just a blank screen. 
Here are the results of my first attempt with this tool: [https://paste.ubuntu.com/p/X2g4hcNwXK/](https://paste.ubuntu.com/p/X2g4hcNwXK/)
And my second attempt: [https://paste.ubuntu.com/p/yBNWJSQZt9/](https://paste.ubuntu.com/p/yBNWJSQZt9/)

Since I was on 16.04(I think?) anyway, I tried to installing a 18.04 instance alongside since I'd have to eventually upgrade anyway and that seemed to work as well, but I'm still just getting a blank screen on restart after the bios splash screen.

Is there anything that you all can see from the log files? Any other ideas on things to try?
Thanks in advance for the help!

---

### Post by surfnraven on 2019-02-16
I ended up trying a new m.2 drive and it still didn't work so I researched m.2 booting and my motherboard and found this link:
[https://forums.tomshardware.com/threads/asus-n751jk-not-booting-from-ssd-m-2.3401634/](https://forums.tomshardware.com/threads/asus-n751jk-not-booting-from-ssd-m-2.3401634/)

I followed the steps below and was finally able to boot back into my system:
> Your M.2 SSD contains UEFI driver information within the firmware. By disabling the CSM module Windows will read and utilize the M.2-specific UEFI driver

Go into the bios, under the boot tab there is an option for CSM, make sure it is disabled.

Click on secure boot option below and make sure it is set to other OS, not windows UEFI.

Thanks for reading!

---

