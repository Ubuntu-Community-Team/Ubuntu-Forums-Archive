---
title: "Kernel Panic"
date: 2007-11-04
forum: General Help
---

### Post by Eloyo on 2007-11-04
while playing counter strike on Nvidia 64 MB with wine and compiz running, it got stuck in a moment and was impossible to go to tty or anything. not even ctrl alt backspace. so i rebooted with the button.
It got ubuntu running and when starting compiz, freeze again.

so i rebooted mannually and next, i have this:

[22.254265] crc error
[22.255410] VFS: cannor open root device "UUID=de0d99b9-f783-4412-ab88-5556170b25fc" or unknown-block(0,0)
[22.255410] Please append a correct "root=" boot option; here are the available partitions:
[ 22-255486] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

note i'm reading this in Recovery mode. 

this means my video card exploded?

---

### Post by Eloyo on 2007-11-04
so i got into grub and booted from the sequence. from root(hda0,0) or something. it booted okay. loaded the graphics for console (in recovery), and it freezes after "Process udevd(pid:1443, etc).

gives some codes, and then it freezes in 

"Fixing recursive fault but reboot is needed!" 

doesn't seem to be fixing anything. any help? i rebooted it  manually and stops in the same argument.

thanks

---

