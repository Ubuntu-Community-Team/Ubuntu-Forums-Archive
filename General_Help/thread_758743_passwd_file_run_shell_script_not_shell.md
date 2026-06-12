---
title: "passwd file run shell script not shell?"
date: 2008-04-18
forum: General Help
---

### Post by Jaiinus on 2008-04-18
Hey there folks, I'm stuck using Redhat Enterprise and it's being a huge pain in the butt. It will boot up every other time and not recognize the USB keyboard and mouse giving up error -110 which is caused by ehci_hd module. So, I figured I'd be clever and set up a service account that will just run a shell script that will simply run a script that does "sudo modprobe -r ehci_hd". I'm at a standstill now, here's what I did:

logged in successfully and ran the script successfully
run the command on it's on fine from bash
triple checked the passwd file entry -> ...:/usr/bin:/usr/bin/fixkeyboard
triple checked the sudo entry, tried it a dozen times too

My guess is that it doesn't want to run a shell scripts but only binary programs. This would suck because I don't want to have have to write this as a bunch of system calls in C and have it run that.

At least I can look forward to lovely ubuntu via VMware once I get the host system functioning!

---

### Post by pointone on 2008-04-18
Er... there's probably an easier way to do this. In Ubuntu/Debian, you can add "blacklist ehci_hd" to /etc/modprobe.d/blacklist to prevent modules from loading on boot. I'm positive Red Hat Linux has a similar blacklist file; it just might be in a different place.

---

### Post by Jaiinus on 2008-04-18
ehci_hcd is the module that enables USB2.0 and this system might/is going to use that for removable storage, which I was told is going to be in use on this system.

What you said brings up a good point though, if someone is going to be at the system using it and this problem rears its head they'll have to choose between control or USB2. I guess there is no real solution for this other than to reboot it when it happens or just use ssh. Or in the case of the bossman, I guess I' going to have to get VNC up for him.

---

### Post by pointone on 2008-04-18
You might be able to get USB 1.1 support with ohci_hcd...

---

