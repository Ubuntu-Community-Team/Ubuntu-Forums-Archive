---
title: "Prevent &quot;who&quot; and &quot;ps&quot; from showing my source IP or username?"
date: 2007-07-28
forum: General Help
---

### Post by mightyteegar on 2007-07-28
I run a small SSH server for testing for my classmates and I, and I don't want them knowing where I logged in from on my local network.  The curriculum is networking security and I want as little information about my local etwork divulged as possible.  Short of modifying the source code for the "who" and "ps" commands to mask my username/IP address, is there a way to accomplish this?

---

### Post by cmnorton on 2007-07-29
> **mightyteegar said:**
> I run a small SSH server for testing for my classmates and I, and I don't want them knowing where I logged in from on my local network.  The curriculum is networking security and I want as little information about my local etwork divulged as possible.  Short of modifying the source code for the "who" and "ps" commands to mask my username/IP address, is there a way to accomplish this?
I believe in both cases, you'll have to create a shell-script version of these functions and the install them, so they are picked up first in PATH. In the case of who, you could pass this through a sed or awk script to eliminate the host name. For ps, you could filter out any line that began with root (which is where I saw my telnet ip address on our vpn). 

I am interested in other answers you will get, however. There is probably a more clever thing to do than this suggestion.

---

