---
title: "fix dependency problem for latest skype"
date: 2005-10-14
forum: General Help
---

### Post by oasiscity on 2005-10-14
Hi,
I downloaded the latest skype from skype.com.
skype_1.2.0.17-1_i386.deb

I input sudo dpkg -i skype_1.2.0.17-1_i386.deb,
but it said that skype requires libqt3c102-mt (>= 3:3.3.3.2), but in system there is 3:3.3.3-7ubuntu3.
Now system has one dependency problem.

but actually skype works perfectly regardless of this.

now the problem rises when I open synaptic.
When I want to install/update something else,
skype is chosen automatically to be delected.

I want to keep skype as it is now. so, how can I fix the dependency problem and tell system that skype can use the existinng libqt3c102-mt?

---

### Post by oasiscity on 2005-10-14
sorry, I didn't notice that issue have been disucssed here.
[http://forum.skype.com/viewtopic.php?t=37482&sid=41fb949742f6b66443048d21403fc310](http://forum.skype.com/viewtopic.php?t=37482&sid=41fb949742f6b66443048d21403fc310)

how can I delete this thread?

[QUOTE=oasiscity]Hi,
I downloaded the latest skype from skype.com.
skype_1.2.0.17-1_i386.deb

I input sudo dpkg -i skype_1.2.0.17-1_i386.deb,
but it said that skype requires libqt3c102-mt (>= 3:3.3.3.2), but in system there is 3:3.3.3-7ubuntu3.
Now system has one dependency problem.

but actually skype works perfectly regardless of this.

now the problem rises when I open synaptic.
When I want to install/update something else,
skype is chosen automatically to be delected.

I want to keep skype as it is now. so, how can I fix the dependency problem and tell system that skype can use the existinng libqt3c102-mt?[/QUOTE]

---

### Post by tanimislam on 2005-10-22
Actually, I have re-debianized the skype package from the original tar.bz2 file. This is the version of skype dynamically linked to the Qt libraries. I have also built the Debian package on Ubuntu Breezy, so your YMMV.

The Debian package is very large, so if you are still interested in this please email me at 

tanim AT virginia DOTT edu

And I will send you the file by email.

---

