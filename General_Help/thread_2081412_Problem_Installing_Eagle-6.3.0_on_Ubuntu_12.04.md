---
title: "Problem Installing Eagle-6.3.0 on Ubuntu 12.04"
date: 2012-11-06
forum: General Help
---

### Post by afz12 on 2012-11-06
I tried to install Cadsoft Eagle (PCB CAD software) in Ubuntu 12.04 but it didn't work. The software center lists it as an entry but seems to lack any files for installing it. I downloaded eagle-lin-6.3.0.run from the website and tried to install by terminal using

3.  Type "chmod +x example.run" (press enter).
4.  Now type "./example.run", press enter, and the installer will run. (e.g ./eagle-lin-6.3.0.run)

as suggested by a forum correspondent's previous post but the last step failed with error messages (even when adding "sudo" in front. However the same procedure worked perfectly on another notebook running Mint Mate without any problems. Also the windows version installs easily on both using Virtualbox.

I tried Synaptic and found a much earlier version and this installed OK. However I still can't update eagle on Ubuntu 12.04 even though MInt Mate has no problems with the latest version.

Admittedly, like most software, the differences between updates are usually small and often unnoticeable. However I'd like to understand why Ubuntu 12.04 has problems but Mint Mate does not. Since I am still learning Linux, any solutions that I can try will be useful to me. Thanks in advance.

---

### Post by zombifier25 on 2012-11-06
Can you post the entire error message?

---

### Post by afz12 on 2012-11-06
Hi Zombifier25

I repeated the procedure - this is the only error message returned

/tmp/eagle-setup.6856/eagle-6.3.0/bin/eagle: error while loading shared libraries: libssl.so.1.0.0: cannot open shared object file: No such file or directory

I looked for the file libssl.so.1.0.0 in Synaptic but it isn't there. I also tried a terminal using sudo apt etc but no joy either. I thought that perhaps MInt "carries" this file so I ran Mint Mate as a VM in Ubuntu 12.04 (same 64 bit OS source DVD as on my other notebook) but it gave the same error! I wonder if this is a hardware issue? However this Ubuntu 12.04 machine is much more up to date than my older one running Mint Mate. It seems odd that a modern machine should have inferior hardware to much older one. Both are 64 bit - this is 4-core i5, the older one is 2-core i3.

Any suggestions welcome zombifier25!

---

### Post by zombifier25 on 2012-11-07
I can't check since I'm on a Windows box, but looks like your program depends on libssl1.0.0, so install it and try again.

---

