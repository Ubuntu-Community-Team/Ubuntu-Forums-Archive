---
title: "unnecessary nvidia update on laptop not having nvidia graphics"
date: 2015-01-09
forum: General Help
---

### Post by dieter-erich on 2015-01-09
Hi,
    I have an eeePC 1004HA notebook with an Intel graphics running under UBUNTU 14.04 (to be correct, the WUBI version). Recently, the update function that I enabled to work automatically, proposes to update Nvidia drivers and a number of related things. My questions:
1) Why is this proposed, does the update not know that I do not have an Nvidia graphics?
2) Should I simply allow the update or can this lead to problems (as I had recently on a Thinkpad W520)?
3) If an update (installation) of these Nvidea drivers does not make sense how can I inactivate as to not being asked again?
Thanks for any suggestions, D-E

---

### Post by QIII on 2015-01-10
Hello!

Could you provide us a screenshot?

---

### Post by dieter-erich on 2015-01-10
Thanks, screenshot attached!

---

### Post by QIII on 2015-01-10
OK.  That is odd.

If it had just been parts of the open source drivers, I'd have just said it was coming along as a dependency of a kernel update or something.

If you do not have the proprietary NVIDIA driver installed, there seems no reason for such an update.

Unfortunately, I don't have a good answer for you at the moment.

---

### Post by grahammechanical on 2015-01-10
We can untick those packages so that they do not download. We can also go to Software and Updates and untick the box labelled Proprietary Drivers for Devices (Restricted). As to why you are receiving a security update to an Nvidia driver when you do not have one installed, I have no idea. The Additional Drivers tab should show the video driver in use.

I know that if we install a proprietary video driver and then revert to using the open source video driver, the proprietary driver is not removed. It will still be listed as a package on the OS. And hence something that will need a security update.

Do you have Nvidia driver code on your system, even if not installed? It should show up in the Ubuntu Software Centre. Search for "Nvidia."

Regards.

---

### Post by dieter-erich on 2015-01-10
There is a lot of Nvidia under 'Software povided by Ubuntu' but none is installed (ticked). So, apparently, even if there is no hint to Nvidia in the system files the updater wants to install these drivers. I know that there is a way of permanently blocking updating/installing specific files. Can you please let me know how this is being done?! I'd then would simply block everything related with Nvidia although I do not know whether the other files installed through the (following) updates would then refer to something missing. I want to avoid skrewing up my (well-functioning) install.
Thanks, D-E

---

### Post by mc4man on 2015-01-10
Why don't you run a simulated upgrade, it will show you exactly what's being updated.
```
sudo apt-get -s upgrade 
```

---

