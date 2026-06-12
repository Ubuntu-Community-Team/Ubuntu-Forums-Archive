---
title: "Ubuntu detects tiny11 but wont dualboot on my dads 2008 hp elite desk tower"
date: 2024-07-17
forum: General Help
---

### Post by linuxisdabest on 2024-07-17
hi! Ive Tried most of the ubuntu flavors on my dads computer and they detect tiny11 but wont dualboot with it. Why Not?
its MBR.
and they were all booted off of usb

---

### Post by dragonfly41 on 2024-07-17
I don't know about Tiny 11 but willing to learn.

I dual boot Windows 10 and Ubuntu 22.04 (GPT not MBR) but my Dell does not meet Windows 11 demands.

In learning more (out of curiosity for future configuration) I found these articles 

[https://www.easeus.com/partition-manager-software/install-windows-11-on-mbr-in-2023.html#:~:text=As%20for%20the%20question%2C%20Windows,primary%20disk%20for%20Windows%2011](https://www.easeus.com/partition-manager-software/install-windows-11-on-mbr-in-2023.html#:~:text=As%20for%20the%20question%2C%20Windows,primary%20disk%20for%20Windows%2011).

And this discussion might help you.

[https://www.thurrott.com/windows/windows-11/294806/hands-on-with-tiny11-2311](https://www.thurrott.com/windows/windows-11/294806/hands-on-with-tiny11-2311)

Your comment "its MBR" raises a flag. My dual booting is GPT.

Final thought is to try EasyUEFI (trial) in Windows. But a 2008 HP vintage might not cut it.

Anything here.

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

[https://ubuntuforums.org/search.php?searchid=35013725](https://ubuntuforums.org/search.php?searchid=35013725)

---

### Post by linuxisdabest on 2024-07-18
tiny 11 is a modified build of windows 11 for use on old/vintage pcs

---

### Post by dragonfly41 on 2024-07-19
So be it.

---

### Post by him610 on 2024-07-19
> People also ask
What is Tiny11 for?
If you're using an older or lower-end PC but want faster performance and lower resource usage, install Tiny11. It's a stripped version of Windows 11, which you can install on any PC regardless of the system's requirements…
Now we know.

---

### Post by yancek on 2024-07-20
>  tiny 11 is a modified build of windows 11 for use on old/vintage pcs

And why would you be posting a question about a windows system at a Linux/Ubuntu forum?  Doesn't microsoft have a site for support/inforamtion?

It is usually a good idea to post some information (or at least a link) on non-standard software.  The link below is to the microsoft site and Tin 11 is not connected to Microsoft in any way.  Well, that might be a good thing for some.  So it's third party software and use at your own risk.

[https://answers.microsoft.com/en-us/windows/forum/all/is-tiny11-really-safe/b615975e-b576-4cab-b465-acaae912a367](https://answers.microsoft.com/en-us/windows/forum/all/is-tiny11-really-safe/b615975e-b576-4cab-b465-acaae912a367)

More information at the site at the link below.  Have you at least read through both these sites?

[https://www.partitionwizard.com/news/tiny11-vs-windows-11.html](https://www.partitionwizard.com/news/tiny11-vs-windows-11.html)

Your original question "Ive Tried most of the ubuntu flavors on my dads computer and they detect tiny11 but wont dualboot with it".  Are you serious? How would you expect anyone to try to answer a question with so little information.  I expect most users here (like myself) have never hear of Tiny 11 for starters.  You don't indicate  how you are trying to dual boot, how you installed Tiny 11, whether it was successful, if you installed it on the same drive as whatever Ubuntu you have. You say your Ubuntu won't boot the Tiny 11 but give no details.  Does your Ubuntu boot?  After installing the TIny 11, did you boot into Ubuntu and update grub.  Did you see an entry for it in the output?   If you have some version of Ubuntu installed you could get and post the device/partiition information to start with either parted -l or fdisk -l and get more detailed information from boot repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

