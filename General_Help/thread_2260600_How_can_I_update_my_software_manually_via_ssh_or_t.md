---
title: "How can I update my software manually via ssh or terminal"
date: 2015-01-13
forum: General Help
---

### Post by DiogoSaraiva on 2015-01-13
[SIZE=4]sometimes I get something like this:[/SIZE]

[IMG]http://www.omgubuntu.co.uk/wp-content/uploads/2012/05/updates-initial.jpeg[/IMG]

But as I use basically always SSH to control my ubuntu (e.g. ssh diogosaraiva@192.168.*.***) how can I perform these updates with prompt/terminal commands or shell scripts?

[SIZE=3]Thanks in advance and have a nice day...

***update***

[SIZE=2]On my old Raspberry pi I remember that for update the firmware was:```
 sudo rpi-update
```[/SIZE][/SIZE]

---

### Post by kpatz on 2015-01-13
**sudo apt-get update && sudo apt-get upgrade** (or **dist-upgrade**)

The difference (from here): [http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)
> upgrade
    upgrade is used to install the newest versions of all packages
    currently installed on the system from the sources enumerated in
    /etc/apt/sources.list. Packages currently installed with new
    versions available are retrieved and upgraded; under no
    circumstances are currently installed packages removed, or packages
    not already installed retrieved and installed. New versions of
    currently installed packages that cannot be upgraded without
    changing the install status of another package will be left at
    their current version. An update must be performed first so that
    apt-get knows that new versions of packages are available.

dist-upgrade
    dist-upgrade in addition to performing the function of upgrade,
    also intelligently handles changing dependencies with new versions
    of packages; apt-get has a "smart" conflict resolution system, and
    it will attempt to upgrade the most important packages at the
    expense of less important ones if necessary. So, dist-upgrade
    command may remove some packages. The /etc/apt/sources.list file
    contains a list of locations from which to retrieve desired package
    files. See also apt_preferences(5) for a mechanism for overriding
    the general settings for individual packages.

---

### Post by nerdtron on 2015-01-13
check for updates:
```
 sudo apt-get update
```

Install the updates
```
 sudo apt-get upgrade
```

---

### Post by DiogoSaraiva on 2015-01-13
But when I perform ```
sudo apt-get update && sudo apt-get upgrade -y
```
or
```
sudo apt-get update && sudo apt-get upgrade
``` and y and enter,



I still getting on the screen something like this:

[IMG]http://www.omgubuntu.co.uk/wp-content/uploads/2012/05/updates-initial.jpeg[/IMG]

But with less MB to be downloaded...

---

### Post by nerdtron on 2015-01-13
Did you click "Details of updates".

Those were probably the kernel upgrades which are not updated on normal "sudo apt-get upgrade". Try the "sudo apt-get dist-upgrade".

---

### Post by kpatz on 2015-01-13
Try dist-upgrade instead of upgrade.  So:  **sudo apt-get update && sudo apt-get dist-upgrade**

Did you actually go to the trouble of hand drawing that dialog box? ;)

---

### Post by Karlchen on 2015-01-13
_**Correction:**_
> **nerdtron said:**
> Those were probably the kernel upgrades which are not updated on normal "sudo apt-get upgrade". Try the "sudo apt-get dist-upgrade". To the best of my knowledge ```
sudo apt-get upgrade
``` **will install available kernel updates**, like e.g. the kernel updates which were available today on Trusty from K3.13.0-43 to K3.13.0-44.
To the best of my knowledge and according to the apt-get manpages, too, the difference between "sudo apt-get upgrade" and "sudo apt-get dist-upgrade" is the way how dependency conflicts will be handled.
> **"man apt-get"][SIZE=1]       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources
           enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and
           upgraded said:**
> 

[U]Beware:
[/U]The next few posts will reveal that in fact I was wrong and nerdtron, deaflowr and kpatz were right. "sudo apt-get upgrade" will not upgrade from K3.13.0-43 to K3.13.0-44, because this involves adding new packages. I should have taken the section "upgrade" literally.

---

### Post by nerdtron on 2015-01-13
sudo apt-get upgrade will install kernel upgrades? It's not happening on my Xubuntu install. It will say, "the following packages have been held back". Then lists the kernels upgrades, just like a server install.. But then again, this is from a xubuntu VM and another from a server. I can't remember the default behavior of the full disk ubuntu install i had last year.

---

### Post by kpatz on 2015-01-13
An even better way is to use **sudo aptitude safe-upgrade**.  This will install any dependencies needed to install the packages it wants to upgrade, and it'll remove unused packages.  This is what I use and it updates kernels and everything fine for me.

If aptitude isn't installed, use **sudo apt-get install aptitude**.  Some versions don't come with it by default.

So **sudo apt-get update && sudo aptitude safe-upgrade** should update everything that the GUI update manager would.

---

### Post by deadflowr on 2015-01-13
> **Karlchen said:**
> _**Correction:**_
 To the best of my knowledge ```
sudo apt-get upgrade
``` **will install available kernel updates**, like e.g. the kernel updates which were available today on Trusty from K3.13.0-43 to K3.13.0-44.
To the best of my knowledge and according to the apt-get manpages, too, the difference between "sudo apt-get upgrade" and "sudo apt-get dist-upgrade" is the way how dependency conflicts will be handled.

Did you read the entry for the man page?
from apt-get upgrade
> under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be
upgraded without changing the install status of another package will be left
at their current version.


Also, to the OP, sometimes the Details of the update dialog you get will tell you what is happening. But sometimes those details can be hard to see, because the box is tiny. You can resize the box by press the alt key and the middle mouse button. Then pull the mouse outward and it'll make it easier to see the detail contents.
Hope that helps.

---

### Post by Karlchen on 2015-01-14
Hello, deadflowr.

> Did you read the entry for the man page? You may have noticed, I, too posted it. So, yes I have consulted the apt-get manpages more than once. :wink:

Usually, I check and install available upgrades using Synaptic. The recent kernel upgrade from K3.13.0-43(72) to K3.13.0-44(73) has been done on most of my systems already, so I cannot check there any longer. 
But tonight I will upgrade another system at home.
This time I will not do so using any GUI, but instead I will use ```
sudo apt-get update && sudo apt-get upgrade
``` and post the screen output here. This should help find out who is right, those assuming "sudo apt-get upgrade" will skip kernel updates or me. :wink:
(Though I said so before, let me repeat, I was not talking about switching the kernel series (e.g. from K3.13.0 to K3.16.0), just about installing the kernel updates which Synaptic will offer, too.)

Cheers,
Karl

---

### Post by kpatz on 2015-01-14
I just tried it on one of my 14.04 boxes.

**sudo apt-get upgrade** doesn't install the new kernel (it's held back).  **sudo aptitude safe-upgrade** does install the new kernel.

EDIT: **sudo apt-get dist-upgrade** also installs kernel updates.

---

### Post by Karlchen on 2015-01-14
Hi, kpatz.

Using the upgrade from K3.13.0-43 to K3.13.44 executed today through Synaptic as an example:

So "apt-get upgrade" _would be willing_ to execute this part, upgrading the already existing packages:
```
The following packages have been updated:

linux-generic-lts-trusty (3.13.0.43.37) to 3.13.0.44.38
linux-headers-generic-lts-trusty (3.13.0.43.37) to 3.13.0.44.38
linux-image-generic-lts-trusty (3.13.0.43.37) to 3.13.0.44.38
linux-tools-generic-lts-trusty (3.13.0.43.37) to 3.13.0.44.38
linux-tools-lts-trusty (3.13.0.43.37) to 3.13.0.44.38
```
But as we all know for a kernel update we need to add a few new packages, too.
 So it is the second part of the kernel update below which makes _"apt-get upgrade" refuse to execute the kernel update as a whole_:
```
The following packages have been installed:

linux-headers-3.13.0-44 (3.13.0-44.73~precise1)
linux-headers-3.13.0-44-generic (3.13.0-44.73~precise1)
linux-image-3.13.0-44-generic (3.13.0-44.73~precise1)
linux-lts-trusty-tools-3.13.0-44 (3.13.0-44.73~precise1)
linux-tools-3.13.0-44-generic (3.13.0-44.73~precise1)
```
Hm, might be. Doubtlessly, I will learn what will happen tonight. :-)

Cheers,
Karl

---

### Post by Karlchen on 2015-01-14
Hello, deadflowr. Hello, kpatz. Hello, nertron.

_Summary:_
You three were right and I was wrong.
 "sudo apt-get upgrade" refused to upgrade the kernel packages from K3.2.0-74(109) to K3.2.0-75(110).
The reason quite obviously was that upgrading did not only require upgrading existing software packages, but that it also required installing additional software packages (the new kernel packages).
But "sudo apt-get upgrade" will not add any software packages. I should have taken the section about "upgrade" in the manpages literally.

_Workaround/Solution:_
I decided to let Synaptic do the kernel upgrade, not "sudo apt-get dist-upgrade".
 Reason:
There are 2 locked NVidia driver packages in Synaptic which Synaptic will never upgrade unless I unlock them again.
"sudo apt-get dist-upgrade" obviously planned to upgrade them as well. So I would have had to set them on "hold" for apt-get as well. But I was too lazy to do so.

[U]Details:
[/U]In the unlikely case that anybody cares to go through the details, they can be found here: [sudo_apt-get_upgrade]("http://pastebin.com/WyxeDhP5")

Cheers,
Karl

---

