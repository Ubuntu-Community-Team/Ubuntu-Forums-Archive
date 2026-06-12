---
title: "How to use an older kernel?"
date: 2016-04-03
forum: General Help
---

### Post by BulletsWithGPS on 2016-04-03
I am using kernel 4.4 and I want to switch to 3.16. 

Any way I can do this? How?

---

### Post by ian-weisser on 2016-04-03
The simple answer is: Go locate the kernel package you want on launchpad.net and install it.
However, it is not recommended, unsupported, may thoroughly break your system, and may be vulnerable to published exploits.
If you break your system, we cannot help you beyond recommending a reinstall of a supported version of Ubuntu with a supported kernel.

Why would you want to install an obsolete, unsupported, two-year-old kernel? What does it provide that recent kernels do not?

No supported release of Ubuntu uses kernel 4.4 either.  Xenial (16.04) uses 4.4, but is still unreleased. Polish and bugfixing  is ongoing. It's not finished yet. Users experienced with installing experimental kernels already know where to find them and how to install them. Consider using a stable, supported version like 15.10.

---

### Post by BulletsWithGPS on 2016-04-03
I still have problems on 4.2 so It doesnt really matter.

When they updated the 14.04 kernel from 3.13 to 4.2 my wifi stopped working and this seems the only way to solve it.

---

### Post by nerdtron on 2016-04-03
> **BulletsWithGPS said:**
> I still have problems on 4.2 so It doesnt really matter.

When they updated the 14.04 kernel from 3.13 to 4.2 my wifi stopped working and this seems the only way to solve it.

Did you removed the older kernel during the upgrade? You can try rebooting, press the shift key on GRUB boot-up and you should see the available kernels. Choose the older ones. Press enter to continue startup and see if it fixes your problem.

---

### Post by jeremy31 on 2016-04-03
Post the results for ```
lspci -nnk | grep -iA2 net; lsusb; lshw -c net; rfkill list all
```

We might be able to get wifi working again

---

