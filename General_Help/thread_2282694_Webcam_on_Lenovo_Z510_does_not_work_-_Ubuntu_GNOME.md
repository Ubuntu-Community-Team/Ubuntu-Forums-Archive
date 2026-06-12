---
title: "Webcam on Lenovo Z510 does not work - Ubuntu GNOME 14.04.2"
date: 2015-06-16
forum: General Help
---

### Post by amjjawad on 2015-06-16
Hi everyone,

On Ubuntu GNOME 14.04.2, the webcam on Lenovo Z510 does not work.

Here is the output of "lsusb":

```
~$ lsusb 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 8087:07dc Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

I am not sure what should I do?
Tried to search on the Internet for an hour or so but didn't find anything useful :(

Thank you!

---

### Post by amjjawad on 2015-09-08
Upgraded to 14.04.3 and the camera is working now.

---

### Post by amjjawad on 2015-09-08
I am not sure what is going on? it was working yesterday, it is NO longer working today :(

```
~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

I'm testing it using "Cheese" and while it worked yesterday, it says no: no device found.

Can someone help?

Thank you!

---

### Post by Bucky Ball on 2015-09-09
Restart the machine. Once stable at a desktop, plug the device in. Run this command immediately after plugging before doing _anything_ else:

```
dmesg
```

Post the output. You only give us the lsusb when it is not detected so we have no idea what the webcam is.

---

### Post by amjjawad on 2015-09-09
> **Bucky Ball said:**
> Restart the machine. Once stable at a desktop, plug the device in. Run this command immediately after plugging before doing _anything_ else:

```
dmesg
```

Post the output. You only give us the lsusb when it is not detected so we have no idea what the webcam is.

Thanks for your reply. The Camera is built-in with the laptop and it is already plugged since it has been built in and can't be attached nor unplugged.

Do I still have to post the output of
```
dmesg
```
Or there is another command?

Thanks!

---

### Post by Bucky Ball on 2015-09-09
No. Just wondering why you are posting the results of a command that gives information about plugged in USB devices. I see now this has nothing to do with that. :-k :)

If it works one day and not the next and you haven't done anything to cause this, how old or young is the machine? Sounds like something odd happening with hardware.

---

### Post by amjjawad on 2015-09-09
> **Bucky Ball said:**
> No. Just wondering why you are posting the results of a command that gives information about plugged in USB devices. I see now this has nothing to do with that. :-k :) 
I don't know, I thought that was needed. Well, that is exactly why I posted here on the first place because I had no idea how to fix the issue :)

> If it works one day and not the next and you haven't done anything to cause this, how old or young is the machine? Sounds like something odd happening with hardware.

The machine is one year old but never been used much .. maybe less than 10 times or so. So, it is really new.

It is working on Windows 8 which is the default on this machine. 
I installed Ubuntu GNOME 14.04 last year but didn't use it.

This year, I wanted to use it instead of sitting in the dark doing nothing. When I tried to check the camera, it didn't work :(

After upgrading to 14.04.3, I noticed the camera started to work. That was yesterday.

Today, it is back to not working again :(

So, not sure what is going on?

It is working on Windows 8 (sad but true) and it is not working on GNU/Linux.

No, I will never use Windows so I need to fix it and use it under GNU/Linux.

Thanks!

---

### Post by Bucky Ball on 2015-09-09
The fact it is working in Windows tells us there is nothing wrong with the hardware. That is all.

Please try and update. Open a terminal and:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

These commands will _not_ upgrade your OS to a newer release. Post any and all errors between code tags (see the last link in my signature). Reboot and at the grub menu of kernels/OSs, go to the second one, Advanced Options, and on that screen choose the first kernel on the list.

It sounds like it might be working on one kernel and not the other. Perhaps the kernel being booted into is changing. A shot in the dark, but possible.

---

### Post by plucky on 2015-09-09
Also try **guvcview** as an alternative to cheese.

Good luck

---

### Post by amjjawad on 2015-09-09
> **plucky said:**
> Also try **guvcview** as an alternative to cheese.

Good luck

Hi and thanks for posting.

[ATTACH=CONFIG]264316[/ATTACH]

Same, nothing changed.

---

### Post by amjjawad on 2015-09-09
> **Bucky Ball said:**
> The fact it is working in Windows tells us there is nothing wrong with the hardware. That is all.

Yes, I'm aware there is nothing wrong with the hardware. I think it is a driver issue.

> Please try and update. Open a terminal and:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```    

These commands will _not_ upgrade your OS to a newer release. Post any and all errors between code tags (see the last link in my signature). Reboot and at the grub menu of kernels/OSs, go to the second one, Advanced Options, and on that screen choose the first kernel on the list.

I highly appreciate your help but I am aware of all that and I have already done it but sadly, nothing has changed. I even did it yet again just to triple check that I didn't miss anything :) same old, nothing changed.

> It sounds like it might be working on one kernel and not the other. Perhaps the kernel being booted into is changing. A shot in the dark, but possible.
Maybe or a driver issue.

I will boot to an old kernel and see. Who knows? maybe that will help ...

Thank you very much :)

---

### Post by amjjawad on 2015-09-09
I have 3 Kernels. I rebooted the machine, selected each one of those 3 and booted the laptop. Well, sadly nothing :(

[ATTACH=CONFIG]264317[/ATTACH]

This is a screenshot for both Cheese and guvcview.

---

