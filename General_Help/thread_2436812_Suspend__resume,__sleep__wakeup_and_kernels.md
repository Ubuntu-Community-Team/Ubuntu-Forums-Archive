---
title: "Suspend / resume,  sleep / wakeup and kernels"
date: 2020-02-13
forum: General Help
---

### Post by ra7411 on 2020-02-13
Whatever you call it, suspend/resume is a major convenience. 

In my 4.5 yrs of using Ubuntu, I've gone through a number of episodes when s/r worked fine, only to be followed by a period when nothing I could do would get it functioning regularly again.
During that period, I've been using AMD cpu desktop machines (14.04,16.04,18.04).

Ubuntu updates sometimes include kernel ver updates (right?), and I don't know for sure, but I suspect that's what accounts for these otherwise inexplicable on-again off-again periods.

Recently, I was running a ver of 5.3 with s/r working, then after an update w/ reboot it wouldn't run. I updated to a 5.5 ver and s/r was still defunct. I randomly back-dated to a 5.1 ver and now it works again.
So does my tentative explanation seem likely, or not? (Or does everybody except me already know this? :confused:)

Thanks

---

### Post by EuclideanCoffee on 2020-02-13
Whenever this happens on computers I support, more or less, it's related to Nvidia. Go to your dmesg and grep for errors.

Like so:

dmesg | grep 'error'

or grep 'Error'

And if you see something related to acpi, then you'll have to adjust your Linux kernel boot configuration.

Here's a reference list: [https://raw.githubusercontent.com/torvalds/linux/master/Documentation/admin-guide/kernel-parameters.txt](https://raw.githubusercontent.com/torvalds/linux/master/Documentation/admin-guide/kernel-parameters.txt)

Note the acpi configuration options. 

Use this to guide you as you Google your exact issues. You can also post your dmesg errors if you think it'd be helpful to you and other users. :)

---

