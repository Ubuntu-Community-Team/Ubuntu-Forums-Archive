---
title: "routine upgrade made system unable to start"
date: 2007-04-13
forum: General Help
---

### Post by rvbhute on 2007-04-13
After a routine upgrade through Upgrade Manager, my system is not starting up. It comes to the Ubuntu logo screen and stays there. It does not hang - I checked by flipping Capslock and Numlock. The kernel version is 2.6.20-14. I am able to boot into 2.6.20-13. Unfortunately, there is a conflict between the Nvidia kernel module and x-org driver and hence, now I'm using VESA driver. 

Any ideas on what I should do?

---

### Post by old_geekster on 2007-04-13
I am having the same problem after installing the 40 updates this evening.  It said a system restart was necessary.  So, I did a restart and it gets to the Ubuntu logo screen and stops as you said.

My problem is it won't boot on any of the other versions.

Hopefully, I won't have to do a new install.

---

### Post by fiddler59 on 2007-04-13
Mine did the same thing with Feisty Beta.......I had to use 2.6.20.12 kernel to get back to where my system would boot !!!
DB

---

### Post by seamuso on 2007-04-13
Mine does the same. I know where mine stops though ....

If I have my nvidia sata controller enabled, it locks when it detects the drives .. if I disable the sata controller, I can boot fine from my pata.

---

### Post by rvbhute on 2007-04-13
Wait and watch seems to be the word - there are a lot of posts saying the same thing.

---

### Post by seamuso on 2007-04-13
> **rvbhute said:**
> Wait and watch seems to be the word - there are a lot of posts saying the same thing.

And it looks like all in here are running nvidia based chipsets :lol:

---

### Post by rvbhute on 2007-04-13
Looks like it 
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-April/000279.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-April/000279.html)
[http://ubuntuforums.org/showthread.php?t=408057](http://ubuntuforums.org/showthread.php?t=408057)
[https://bugs.launchpad.net/ubuntu/+bug/106063](https://bugs.launchpad.net/ubuntu/+bug/106063)

Are they in a big problem or what?  :-)

---

### Post by davidsrsb on 2007-04-13
It's not just nvidia chipsets, my laptop (celeron D + intel video) is also locking up after the 14.22 to 14.23 upgrade

---

### Post by nbound on 2007-04-13
Similar problem here, Nvidia chipset, booting in recovery mode causes hardware error kernel panic and says my CPU is causing it, yet i can boot older kernels just fine.

---

### Post by mikaelbj on 2007-04-13
I have the exact same problem. After upgrading around 40 updates with the update manager and then rebooting like I am asked to, the boot process stops at the Ubuntu loading screen and when I ctrl+alt+F1 I see:
```

......
[Linux-initrd @ 0x1f80a000, 0x7e5456 bytes ]
savedefault
Loading, please wait...
mdadm: No devices listed in conf file were found

```

And I get to the busybox shell.

As far as I know I'm not using mdadm. I'm just using a single sata drive (/dev/sda), which does not show up if I ls -la /dev/ | grep sda.

I am running 2.6.20-14-386. I removed all my older kernels yesterday due to disk space problems, so I can't boot into one of them.

What should I do?

---

### Post by peterbengtsson on 2007-04-13
Doesn't just happen on nVidia drivers. I've got ATI stuff (intel centrino thinkpad t60p) and suffer the same problem. I don't think my kernel was upgrade before the reboot but I could be wrong. The current on is 2.6.20-14.

I can boot into an old kernel and get on the net but the windows don't really work. No mutiple desktops and I can't use the mouse to close or move windows.

---

### Post by rvbhute on 2007-04-13
Guys, try this 
[http://ubuntuforums.org/showpost.php?p=2444593&postcount=28](http://ubuntuforums.org/showpost.php?p=2444593&postcount=28)

Its on the third page of a relevant forum topic  (second link of the 3 I posted earlier).

The important part is it works!

---

### Post by nbound on 2007-04-13
Not for me using the generic amd64 kernels, copied over the equivalent bak file and it did the same thing as the non-bak

---

