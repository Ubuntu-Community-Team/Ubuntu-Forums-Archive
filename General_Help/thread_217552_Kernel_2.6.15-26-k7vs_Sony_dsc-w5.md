---
title: "Kernel 2.6.15-26-k7
vs Sony dsc-w5"
date: 2006-07-17
forum: General Help
---

### Post by Kosmonaut on 2006-07-17
Since the newest kernelupdate 2.6.15-26-k7 I´m not able to connect my camera to my linux system via usb.
/var/log/messages says:
> Jul 17 16:00:53 localhost kernel: [17180760.112000] usb 1-1: new high speed USB device using ehci_hcd and address 5
Jul 17 16:01:05 localhost kernel: [17180771.768000] usb 1-1: new high speed USB device using ehci_hcd and address 6


Before that kernel-update everything worked fine. Is there someone out there having the same problem?

---

### Post by Kosmonaut on 2006-07-19
Man! There was a Kernel-update today, but my camera still cannot be connected to my System. How could I fix this probem?

---

### Post by Ramses de Norre on 2006-07-19
Have you manually compiled a driver for it? If so you need to recompile that driver with every kernel update.

---

### Post by Kosmonaut on 2006-07-19
No I didn´t need to compile anything.
The camera worked "out-of-the-box", until kernel 2.6.15-23. 
Kernel 2.6.15-25/2.6.15-26 doesn´t seem to support my camera anymore.
I should write a bug-report to launchpad, right?

---

### Post by Ramses de Norre on 2006-07-19
Ok this is a shot in the dark but it might work:
```
sudo rmmod ehci_hcd
```
Then unplug the camera and plug it in again, look in dmesg again then.

---

### Post by Kosmonaut on 2006-07-19
:mrgreen: Yeah...Thanks!
"sudo rmmod ehci_hcd" did work! The camera is visible again. 
What is wrong with ehci_hcd?

---

### Post by Ramses de Norre on 2006-07-19
Ok now for it to work on every reboot do ```
sudo gedit /etc/modprobe.d/blacklist

```
and add this line at the end: ```
blacklist ehci_hcd
```
the module wont load at boot nomore then.
I don't know what's wrong with the module but it shouldn't load for your webcam.. 
I'm not sure whether unloading this module has consequences for your system, if some things stop working you might consider deleting the blacklist line and searching another way to get your cam working.

---

### Post by Kosmonaut on 2006-09-22
I just wanted to report, that my camera is supported again. 
Since the latest kernel update (->2.6.15.27) made it possible to use my camera again, I´m happy again :-D

---

### Post by Ramses de Norre on 2006-09-22
I hope you mean "it's supported without the blacklisting line again" don't you? =)

---

### Post by Kosmonaut on 2006-09-22
Yes indeed...My Camera works like it is suposed to do. Without blacklisting anything. Thank for your hints anyway, I think that I would nerver have solved it by my self.

---

### Post by Ramses de Norre on 2006-09-22
No problem ;)

---

