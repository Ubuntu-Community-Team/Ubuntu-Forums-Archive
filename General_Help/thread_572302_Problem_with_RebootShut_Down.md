---
title: "Problem with Reboot/Shut Down"
date: 2007-10-10
forum: General Help
---

### Post by HarryTruman on 2007-10-10
I've got a problem when I reboot or shutdown my Ubuntu VM.  I'm running 7.04 in the most recent Parallels 3.0 on an Intel MacBook Pro, but I had the same problem happening on my Windows computer that I installed Linux on a few months ago.  

The problem is that, during a reboot, the second that the OS begins unloading the display goes to hell -- see the following attachment.  It stays like that for the duration of the system shutting down and then the display goes back to normal (proper text) at BIOS.  When I shutdown entirely, the process seems to stop somewhere along the way and the system never shuts down entirely; I'm forced to hit the power button.

I'm really not sure what's going on, I've never seen anything like this in my previous Ubuntu installs, and I've not seen Windows/Mac/Linux do anything like this before.  Can anyone point me in the right direction on this one?

---

### Post by upbeat.linux on 2007-10-10
Depending on your motherboard and processor this may or may not solve the problem but try:

```
sudo gedit /boot/grub/menu.lst
```

For each *Ubuntu boot option add the following to the end of the **kernel** line:

```
acpi=force
```

You should then have something like:

```
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/sda1 ro quiet splash acpi=force
```

A few others (on [http://bugs.launchpad.net/ubuntu/](http://bugs.launchpad.net/ubuntu/)) have resolved the same issue by using this fix.

---

### Post by HarryTruman on 2007-10-10
Added that to the kernel line, no dice.

---

