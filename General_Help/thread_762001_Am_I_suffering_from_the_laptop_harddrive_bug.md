---
title: "Am I suffering from the laptop harddrive bug?"
date: 2008-04-21
forum: General Help
---

### Post by olskar on 2008-04-21
Hi, 
I am worried that I suffer from that harddrivebug..

"sudo smartctl -a /dev/sda | grep Load_Cycle_Count" shows me a value that increases by ~7 every minute...

I have tried sudo hdparm -B 255 /dev/sda and sudo hdparm -B 254 /dev/sda but it does not help..

---

### Post by ibuclaw on 2008-04-21
First off, what is the harddrivebug?

I've never heard of it before, though I do feel sympathetic towards your worries, I had a try at the smartctl command, and my settings remained as constants.

Have you tried setting the hdparm to a lower number?
```
 sudo hdparm -B 127 /dev/sda 
```
That will invoke a different behavior to your hard-drive. Whether or not it'll have a desired effect is another matter.

Once I know more, I could give a more defined answer.

Regards
Iain

---

### Post by olskar on 2008-04-21
Thanks for trying to help :)

More info:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/)

---

### Post by ibuclaw on 2008-04-21
Well, it certainly seems like an issue to keep an eye on.

Have you had a sift through the links that were up in the bug report?
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)

I'm probably detouring off the subject a bit when I say this, but how much swap and primary memory do you have?

Not that it is the cause of such high load/unload cycles. But am I right in assuming, that if you have a small amount of memory and your running power hungry apps, then the load/unload cycle time would increase as more and more data is moved in and out of swap?

You could perhaps try some hard-drive performance tricks with the ext3 filesystem.

Small things such as adding **noatime** to your root partition mount options in  /etc/fstab.
Also reducing the amount that is written to your /var and /tmp directories would help performance too.
```

/dev/sda1         /       ext3    **noatime**,errors=remount-ro,data=writeback 0       1
# Other Mounts
# etc
# ...
[B]tmpfs     /var/log        tmpfs     defaults,noatime        0 0
tmpfs     /tmp            tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp        tmpfs     defaults,noatime        0 0[/B]

```

Reducing Swappiness, so the activity of moving data is kept in the Primary Memory at all costs.
```
gksudo gedit /etc/sysctl.conf
```
and add at the bottom.
```
vm.swappiness=0
```

You can also remove any unwanted services that you'll never need.

I can't give full details, but there is a thread with lots of links here:
[http://ubuntuforums.org/showthread.php?t=189192&highlight=tweak+filesystem+performance](http://ubuntuforums.org/showthread.php?t=189192&highlight=tweak+filesystem+performance)

Afterall, it makes sense in my mind that a less strained system is going to have a better lifespan.

Regards
Iain

---

