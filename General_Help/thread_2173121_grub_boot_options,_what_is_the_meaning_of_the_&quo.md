---
title: "grub boot options, what is the meaning of the &quot;--&quot;"
date: 2013-09-08
forum: General Help
---

### Post by prof7bit on 2013-09-08
I am referring to this old thread:

[http://ubuntuforums.org/showthread.php?t=1718877](http://ubuntuforums.org/showthread.php?t=1718877)

where the solution turned out to be such a kernel command line in the (manually created) grub.cfg:

```

kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso quiet splash -- locale=de_DE console-setup/layoutcode=de 
```

I have seen this double-minus ("--") in a few other example grub.cfg files (I am currently experimenting with booting iso files from usb drive with grub2 [also experimented with grub4dos but it seems grub2 is better suited for my needs]) and most of these kernel (or linux) lines have the "--" at the end. Is this parsed by grub, is this parsed by the kernel, is it some kind of separator and it matters what comes before and what comes after the "--" or is it just a kernel option like all other options and if so what is its meaning? I have searched but could not find any documentation mentioning it.

---

### Post by carlwsnyder on 2013-09-08
From my experience of using GRUB 2, the -- simply acts as a separator between the options set in the /etc/default/grub file and options set elsewhere.  No I haven't seen any documentation to support my assertion, that is only my opinion.

---

### Post by VMC on 2013-09-08
> **prof7bit said:**
> I am referring to this old thread:

[http://ubuntuforums.org/showthread.php?t=1718877](http://ubuntuforums.org/showthread.php?t=1718877)

where the solution turned out to be such a kernel command line in the (manually created) grub.cfg:

```

kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso quiet splash -- locale=de_DE console-setup/layoutcode=de 
```

I have seen this double-minus ("--") in a few other example grub.cfg files (I am currently experimenting with booting iso files from usb drive with grub2 [also experimented with grub4dos but it seems grub2 is better suited for my needs]) and most of these kernel (or linux) lines have the "--" at the end. Is this parsed by grub, is this parsed by the kernel, is it some kind of separator and it matters what comes before and what comes after the "--" or is it just a kernel option like all other options and if so what is its meaning? I have searched but could not find any documentation mentioning it.
Those "double minuses" are needed for that grub legacy file. I think in your case it should be "--locale" and not "-- locale" There using another layout. I know in a live boot that's the case anyway.

---

