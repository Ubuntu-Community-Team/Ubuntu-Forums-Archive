---
title: "Can you confirm me this?"
date: 2013-02-27
forum: General Help
---

### Post by Juniorr on 2013-02-27
Yesterday I was testing Ubuntu 12.04.2 with Steam and Kernel 3.5.0-25 and Steam reported there was a 313.18 version of NVIDIA's driver on Jockeys. I currently have no system installed so can anyone confirm if there's actually a 313 Experimental driver on Jockeys Additional Drivers?

PS: I have a 12.04.1 CD and then updated to 12.04.2 with 3.2 Kernel, but I used Synaptic to update to Kernel 3.5.0-25.

PS2: I`ve added xedgers ppa's before upgrading to a newer kernel so I'm not sure if that was the reason why 313 showed available.

---

### Post by dino99 on 2013-02-27
hello Junior

if you have installed the edgers ppa, you then might know why you have install it, and what it bring you, dont you ?
ubuntu suppose that users understand what they are doing.
simply install synaptic, upgrade to nvidia-313, then deactivate that ppa to get a stable installation.

---

### Post by Juniorr on 2013-02-27
Well this is kind of the question purpose, if users that didn't add any PPA's actually have 313 Experimental on Additional Drivers, because it's very odd that Steam reported "A newer version for your graphics card driver is available", so I couldn't make sure if it was because of the PPAs or not.

I'm still using a LiveCD so I cant actually test it right now. If you dont have those PPAs could you confirm to me?

---

### Post by dino99 on 2013-02-27
if it is from the livecd, then that mean steam is finding itself new driver; nothing to worry about, you can ignore it.

standard installation:
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by Juniorr on 2013-02-27
Hehehehe no. I'll describe more of what I actually did.

* After fresh install and updates, added the the PPA
* Upgraded to Kernel 3.5
* Then the system updated again and this caused the login screen to freeze so I removed nvidia (sudo apt-get remove --purge nvidia*)
* Installed 310 Experimental
* Then Steam reported a new driver was available 

Right now at this moment Im on a 12.10 LiveCD so I cant actually see for myself if there really is a 313 Experimental driver abailable so I'd like to know if any user here that hasnt added those PPAs actually see a 313 Experimental =)

---

