---
title: "Cannot blacklist a module"
date: 2007-03-17
forum: General Help
---

### Post by cyrano1917 on 2007-03-17
I have a sony vaio SZ which works fine with Ubuntu except for the ethernet driver which crashes when there is to much traffic :(
I found out that the problem was coming form the driver sky2 so I change it for the Sysconnect driver which works perfectly. I blacklisted the old sky2 module in /etc/modprobe.d/blacklist (I added the line "blacklist sky2") but the module keeps reappearing after reboot time when I do lsmod. Any suggestion?

Thanks!

---

### Post by Dr. Nick on 2007-03-18
remove the word "blacklist" I dont think it needed, just type the modules name.
If that doesnt work and you cant figure out what to do then you can remove the module manually, but it will come back each kernel update.

---

### Post by cyrano1917 on 2007-03-18
Thanks but it does not work. I have the impression that the blacklist system does not concern the ethernet module which is not mentionned anywhere in the modprobe.d directory... any other proposal?

---

### Post by Dr. Nick on 2007-03-18
Hmm. I successfully blacklisted a wireless module, never tried Ethernet though. If you know the name of the module file you can try to move it to a different directory just to prevent it from loading, then add the one you want loaded to the /etc/modules file and see if that takes care of it.

Only drawback to that method is you will have to do it after each kernel update as it will put the module back

---

### Post by cowlip on 2007-03-18
I wonder if any of the solutions here help?  [http://www.debianhelp.org/node/5215](http://www.debianhelp.org/node/5215)

"

> udev manages non-removable devices too. Moreover, it consults
> blacklist entries in the directory /etc/hotplug/blacklist.d/. Try
> placing a file in that directory containing the name of the module you
> wish to blacklist.
"
------------------
"
Perhaps this will work for you on Debian. The file is in /etc/init.d/rc.local.
There is a lot of script in this file compared to the on in Fedora Core 2,
but it probably works the same.

I'd just try adding the following lines in this file and see how it goes.

modprobe -r sky2
modprobe sysconnect

"
-------------
"in /etc/discover.conf-2.6 

skip sky2
"
-----------
maybe try in /etc/modules.conf

alias sky2 off
blacklist sky2
install sky2 /bin/true  [[[(iffy one)]]]
--------------
boot-time kernel option

sky2.blacklist=yes
(per [http://www.debian.org/releases/etch/i386/ch05s02.html.en](http://www.debian.org/releases/etch/i386/ch05s02.html.en)
section 5.2.1.3)

---

### Post by cyrano1917 on 2007-03-18
Thanks for the link but there is no modprobe.conf in my /etc/ directory. Should I add one?
The other solutions are similar to what I am doing: for the moment I just run a script at boot time which simply does: 
rmmod sky2 (the old module)
modprobe sk98lin (the good one)

but I find it really unsatisfactory since sk98lin starts correctly at boot time. It seems that /etc/modprobe.d/blacklist does not concern all the modules which are loaded... :mad:

---

### Post by Dr. Nick on 2007-03-18
I wouldn't create a modprobe.conf, IIRC that was the old way of doing things, it seems that modules are being handled a bit different as of late, not for certain on that though.

---

### Post by cyrano1917 on 2007-03-19
OK thanks for your replies guys. It doesn't seem to be a simple issue then. So nobody knows how to deactivate a #?!%$ module which is not referenced in the /etc/modprobe.d/ directory?
I guess I'll have to do with my little "rmmod" script at boot time but it' s really an ugly solution...

J

---

### Post by cowlip on 2007-03-19
I guess last resort is to try filing a launchpad bug

---

