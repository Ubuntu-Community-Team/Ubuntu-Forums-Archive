---
title: "Kernel Update Interrupted- Broken update command [Solved]"
date: 2015-11-24
forum: General Help
---

### Post by nfmcclure on 2015-11-24
I really don't know what's going on here. My Ubuntu system had updates with kernel updates.  I proceeded to update like normal with the 'software updater' gui.

After a while the computer automatically rebooted.  Without asking. Slightly strange, but to check if things completed like normal, I issued

```

me@computer:-$ sudo apt-get update

```

It proceeded to check all the updates and then ended with "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem".

```

me@computer:-$ sudo dpkg --configure -a

```

Every time I run that command, it auto reboots at the same point.  I managed to get a screenshot of the terminal the instant before it rebooted.

[IMG]http://fromdata.org/wp-content/uploads/2015/11/IMG_20151124_1550451.jpg[/IMG]

(Yes I'm dual booting with Win-10).

That's the last line shown before it reboots with no notice.  Then the same thing happens over and over again.  I can't seem to fix my update command.

Also, 
```

me@computer:-$ sudo apt-get install -f

```

Results in the same "dpkg was interrupted, ..." statement.

Any ideas?

---

### Post by Portaro on 2015-11-24
Ok maybe is good to try remove or edit Kernel boot sequence with Grub customizer .
Try to use the last Kernel before you do the Kernel updates.

If you use Grub customizer is very easy , all you need is select the olde Kernel mark to boot as default and boot.

After this login and try an update to see if any error appear if not your problem is caused by the kernel and the better choice is give some time to this Kernel have more "patches" and with a period of new additions and corrections your porblem with this kernel can disappear.

Unfortunately Kernel is very expensive to maintain because code grow and grow, the hardware providers dont show codes and the use of Microsoft alongside can be problematic because the they insert restrictions to maintain people on their products , Kernel in some architectures can have problems in new hardware or in old hardware, so maintain always attention on the diamond - kernel use the better Kernel for your hardware to have the better experience .

---

### Post by Bucky Ball on 2015-11-25
You don't need grub customizer. Just choose the last kernel you used before the update (choose 'Advanced' which should be the second entry on the list at boot and that will give a list of kernels - choose an older one).

That may get you in so we can have a closer look. Which release of Ubuntu are you using?

---

### Post by nfmcclure on 2015-11-29
> **Bucky Ball said:**
> You don't need grub customizer. Just choose the last kernel you used before the update (choose 'Advanced' which should be the second entry on the list at boot and that will give a list of kernels - choose an older one).

That may get you in so we can have a closer look. Which release of Ubuntu are you using?


I'm using 14.04.  But reverting to an earlier kernel and updating again solved the issue.  I think the heart of the issue is that Ubuntu is not recovering from "sleep" mode correctly.  I sat and watched the whole update to make sure it didn't go to sleep during the update.  I'll look into this issue later.

Thanks for your help!

---

### Post by Bucky Ball on 2015-11-29
All good. You can mark the thread officially solved by checking the second link in my signature. Thanks.

Yes, post a new thread about the sleeping issue. Good luck. :)

---

