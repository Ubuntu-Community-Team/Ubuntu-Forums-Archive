---
title: "Hardware Enablement Stack"
date: 2018-05-03
forum: General Help
---

### Post by ea-mail-wc on 2018-05-03
I have recently upgraded to Ubuntu Desktop 18.04 LTS.

I usually log into my server remotely using Teamviewer, however, due to a problem I've had to login via SSH.

Upon doing this I get the following message.

Welcome to Ubuntu 18.04 LTS (GNU/Linux 4.15.0-20-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)




 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)


0 packages can be updated.
0 updates are security updates.




WARNING: Security updates for your current Hardware Enablement
Stack ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)


There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash.

Running 'update-manager' returns 'The software on this computer is up-to-date'

Running 'hwe-support-status --show-all-unsupported' gives

linux-generic-lts-utopic xserver-xorg-video-all-lts-utopic
xserver-xorg-lts-utopic xserver-xorg-input-all-lts-utopic
libegl1-mesa-drivers-lts-utopic

Running 'hwe-support-status --show-replacements' gives

xserver-xorg-lts-xenial linux-generic-lts-xenial

Running ' sudo apt-get install xserver-xorg-lts-xenial linux-generic-lts-xenial' gives

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package xserver-xorg-lts-xenial
E: Unable to locate package linux-generic-lts-xenial

On the webpage given 'http://wiki.ubuntu.com/1404_HWE_EOL' under 'How can I stop using an HWE stack?' the following instructions are given

sudo apt-get remove $(hwe-support-status --show-all-unsupported)


I wanted to make sure that this is the right direction to go?

Afraid to do anything that might mess up my system.

---

### Post by dino99 on 2018-05-03
'remove' left behind settings; better using 'purge' instead

---

### Post by ea-mail-wc on 2018-05-03
Sorry, are you saying I should use

[COLOR=#000000]sudo apt-get purge $(hwe-support-status --show-all-unsupported)

What about the fact that the suggested replacements can't be found?[/COLOR]

---

