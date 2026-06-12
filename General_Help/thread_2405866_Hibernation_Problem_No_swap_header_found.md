---
title: "Hibernation Problem: No swap header found"
date: 2018-11-12
forum: General Help
---

### Post by ersa21 on 2018-11-12
Hi, 
[COLOR=#242729][FONT=Arial]I hadn't allocated any swap partition while installing ubuntu before so I couldn't hibernate my laptop which gave error: couldn't find swap device,try swapon. I then created a swap partition using GParted of size about 10Gb and enabled on swapon.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I then checked the status of swap in terminal,

```
sudo swapon -s
```

[/FONT][/COLOR][COLOR=#242729][FONT=Arial] output:

[/FONT][/COLOR]Filename                Type        Size    Used    Priority
/swapfile                                  file        2097148    0    -2
/dev/sda4                                  partition    10663932    0    -3

I don't understand why my swaps is not being used. No my laptop can't hibernate and says no swap header found  How do I solve this problem?

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

In some older posts read that only 2.00GB swap is (allowed or recommended not confirmed) good for Ubuntu. Reduce the swap size and then reboot the system. Check if the solution works.

---

### Post by ersa21 on 2018-11-12
Hi,
My swap file size is about 2GB and I have read that swap partition size should be greater than RAM size so I created a swap partition of 10 GB. I think the problem is system cannot recognize the swap or I don't know why that swap header cannot be found.

---

### Post by plucky on 2018-11-13
[https://help.ubuntu.com/community/SwapFaq](SwapFaq)

Above link should give you all you need to know about swap

If that doesn't help, post output from a terminal for
```
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
ls -l /dev/disk/by-uuid
```

How much memory do you actually have?

Good Luck

---

