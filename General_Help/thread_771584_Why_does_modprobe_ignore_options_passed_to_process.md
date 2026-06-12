---
title: "Why does modprobe ignore options passed to processor?"
date: 2008-04-27
forum: General Help
---

### Post by peterff on 2008-04-27
I'd like to pass the option max_cstate=2 to the processor module to stop my CPU from whining. However, it appears that in Ubuntu options added to /etc/modprobe.d/options for the processor module are ignored. Can anyone explain why this is, and if there is a workaround?

---

### Post by ghost_ryder35 on 2008-04-27
can you post your options config so we can have a look at it
Mine works fine
```

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

```

---

### Post by peterff on 2008-04-28
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options processor max_cstate=2
```

This has no effect on the cstate of my processor. This message at [http://thinkwiki.org/wiki/Problem_with_high_pitch_noises](http://thinkwiki.org/wiki/Problem_with_high_pitch_noises) led me to conclude that this is a problem specific to Ubuntu:

> On Ubuntu 5.10, the default kernel uses processor as a module. Unfortunately, the script loading it, /etc/init.d/acpid, ignores the options processor max_cstate=3 setting in /etc/modprobe.d/<my file>. As a solution for this specific problem, add the line echo 2 > /sys/module/processor/parameters/max_cstate directly to /etc/init.d/acpid, at the end of the function load_modules(), immediately after the line echo "$PRINTK" > /proc/sys/kernel/printk.)

The solution he describes worked for me until the Hardy upgrade--in the new kernel the file /sys/module/processor/parameters/max_cstate has been removed. Perhaps someone could help me change /etc/init.d/acpid so that it does not ignore options in /etc/modprobe.d/options (assuming this guy is correct that that script is responsible).

---

### Post by peterff on 2008-04-28
Well, I've figured it out: update-initramfs -u. Apparently the problem was that the processor module, along with other things, is loaded into RAM at boot from a file called initramfs. Since initramfs had not been updated to reflect my changes to /etc/modprobe.d/options, the processor was not being loaded with my new option.

---

