---
title: "Parallel Port Printer Missing"
date: 2007-06-05
forum: General Help
---

### Post by Linux_Zoo on 2007-06-05
Hi,

I have Xubuntu 6.06 installed, with a Canon BubbleJet printer attached to the parallel port.  

I tried to use the CUPS web interface to install the printer ([http://localhost:631/admin](http://localhost:631/admin)), but CUPS does not show the parallel port in the drop down list of 'places where the printer might be attached'.

From the command line, > lpinfo -v gives

network socket
network beh
direct hp:/no_device_found
direct http
direct ipp
direct lpd
direct smb

What do I do next?

Thanks!

---

### Post by mitch.c on 2007-06-06
What happens if you:
```
$ sudo modprobe lp && sudo /etc/init.d/cupsys restart
```
Then try:
```
$ lpinfo -v
```
Does that help?

[COLOR="Red"]UAResolved[/COLOR]

---

### Post by Linux_Zoo on 2007-06-06
Thanks!  I'll try that this weekend and let you know.

---

### Post by Linux_Zoo on 2007-06-16
Turned out that the parallel port was disabled in the BIOS.  Once enabled, Xubuntu picked up the printer, and I was able to use CUPS to set up the printer driver.  Sadly the printer printed one line from a Thunderbird email, then froze.  

I think that getting this software to run on an old PC (Celeron 466) is an uphill struggle.  So disappointing, especially considering how well Windows 95 used to run on these old PC's!

---

