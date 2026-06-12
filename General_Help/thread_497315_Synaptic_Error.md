---
title: "Synaptic Error"
date: 2007-07-10
forum: General Help
---

### Post by evolving_monkey on 2007-07-10
My system locked up when installing vmware-server. I entered incorrect key. I hit the back button to re-enter key and install froze. I let it set for some time. I then decided to reboot. Now when I try to run Synaptic Package Manager I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I pressed alt f2 and entered the above command dpkg --configure -a and nothing happened.

Any advice would be appreciated. Thank you for your time.

---

### Post by evolving_monkey on 2007-07-10
Other post on same subject did not come up in my first search: [http://ubuntuforums.org/showthread.php?t=496550&highlight=synaptic+error](http://ubuntuforums.org/showthread.php?t=496550&highlight=synaptic+error)

They are having similar problem.

The difference is that when I run the command nothing Happens.

---

### Post by bobshowrocks on 2007-07-10
Are you running the command in the terminal?

---

### Post by evolving_monkey on 2007-07-10
Actually yes, I have been running the command in terminal. The funny thing is that last night I couldn't get the command to work. It either said it was a bas command or nothing happened. This morning I gave it a try and without hesitation it worked. Synaptic works fine and the problem seems to have vanished as quickly as it came. VMWare server finished installing and seems to be running fine. 

The problem is that now the rest of the system is flaking out. Amarok says it has no mp3 support and locks up. That is pretty mush the way everything else is also. Synampti and vmware server are 2 of the few things that work properly now. Looks like I might have to reload Ubuntu. That didn't take long

---

### Post by El Viejo Lobo on 2007-07-10
> **evolving_monkey said:**
> My system locked up when installing vmware-server. I entered incorrect key. I hit the back button to re-enter key and install froze. I let it set for some time. I then decided to reboot. Now when I try to run Synaptic Package Manager I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I pressed alt f2 and entered the above command dpkg --configure -a and nothing happened.

Any advice would be appreciated. Thank you for your time.

Try this with the right changes:
[http://ubuntuforums.org/showthread.php?t=424665](http://ubuntuforums.org/showthread.php?t=424665)

---

### Post by evolving_monkey on 2007-07-23
Unfortunately nothing seemed to work. Fortunately, It only takes about 30 minutes to reload Ubuntu. Everything is great now.

Thank you.

---

