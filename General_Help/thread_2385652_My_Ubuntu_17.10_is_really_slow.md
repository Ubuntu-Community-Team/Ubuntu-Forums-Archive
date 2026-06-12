---
title: "My Ubuntu 17.10 is really slow"
date: 2018-02-22
forum: General Help
---

### Post by ifal78 on 2018-02-22
I have Ubuntu installed on a PC with the following specs:

[LIST]
[*]Processor: Intel® Core™ i7-5500U CPU @ 2.40GHz × 4
[*]Memory: 7.7 GiB (originally 8)
[*]Graphics: Intel® HD Graphics 5500 (Broadwell GT2)
[*]GNOME: 3.62.2
[*]OS type 64-bit
[*]Disk 491.2 GB (originally 500 GB)
[/LIST]

Also, I can see that there are 4, 86 MB Loop Devices (snaps). 

I regularly use Chrome, and it freezes from time to time, I check and I have the stable version. 

What can I do to identify the cause?

---

### Post by tinylagarto on 2018-02-26
It seems you should have enough RAM and power to run Ubuntu on it smoothly. 

I could think of Chrome, it uses a lot of system resources. 

You could look at htop or top from the terminal to see what is running. 

Htop is not preinstalled, so you have to grab it from the repositories. 

Another question would be if you are running the Wayland or Xorg session. You can switch that from the display manager at login.

---

