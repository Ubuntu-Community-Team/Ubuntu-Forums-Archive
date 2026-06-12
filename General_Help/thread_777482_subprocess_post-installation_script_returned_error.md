---
title: "subprocess post-installation script returned error exit status 1..."
date: 2008-05-01
forum: General Help
---

### Post by bryncoles on 2008-05-01
just had an odd experience! i tried to tidy up my system with the ol' apt-get autoremove and got a 'subprocess post-installation script returned error exit status 1' message back. 

the offending program is bnetd -which allows diablo 2 to play on a network. i installed it, but never got round to installing diablo 2, so i dont mind either way if bnetd stays or goes (in fact i wouldnt mind it going). 

the output i get is:

bryn@bryn-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bnetd (0.4.25-7) ...
chown: cannot access `/var/run/bnetd': No such file or directory
dpkg: error processing bnetd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bnetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
bryn@bryn-laptop:~$ 

any ideas anyone?

---

### Post by bryncoles on 2008-05-02
ah ha! no problem - ive sorted it!

bnetd was the offending program. i tried creating the directory which it said it couldnt find in '/var/run/bnetd'. that didnt help - it just failed somewhere else, with the same error. 

i tried 'sudo apt-get install -f', which should (i think) repair broken packages. it didnt. i tried 'fix broken pakages' in synaptic. no use. i couldnt reinstall bnetd through synaptic either - it errored out at that too!

so i downloaded the latest .deb package from the bnetd website instead, installed that and was then able to remove it. 

so; anyone getting a subprocess post installation script error, i dunno what causes it, but just download the latest .deb for the package, install that and then remove through synaptic.

nice! :-D

---

### Post by jwillson on 2011-10-12
Hi Bryncoles,

That solution actually didn't work for me, but I did manage to get it fixed.

Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+s...td/+bug/846560](https://bugs.launchpad.net/ubuntu/+s...td/+bug/846560)

Here's what ACTUALLY WORKED for me:
Note: XXX should be replaced with the actual PID number that you get.

sudo /etc/init.d/bnetd stop
ps -e -o pid -o args | grep bnetd
XXX bnetd
sudo kill -9 XXX
rm /etc/init.d/bnetd
sudo apt-get remove bnetd

Notice the "rm /etc/init.bnetd". That's necessary to be able to actually remove it. I hope this helps!

---

