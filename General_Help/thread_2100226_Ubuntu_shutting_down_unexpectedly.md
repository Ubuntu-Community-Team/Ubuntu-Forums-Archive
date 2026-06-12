---
title: "Ubuntu shutting down unexpectedly"
date: 2013-01-01
forum: General Help
---

### Post by RockStone9 on 2013-01-01
I experienced some issues with my acer travelmate 5730 shutting down when I tried to install ubuntu 12.04... However I managed to install it and after a few updates the shutting down stopped...

But yesterday I wanted to plug in another monitor and set dual displays via AMD CCC. After setting dual displays I had to reboot the notebook. And since then the notebook has been shutting down soon after being turned on, not even letting linux or win to boot. I tried many many tricks, from updating drivers to reseting BIOS by pulling out the CMOS battery. I got to the state when I am able to boot linux by launching recovery mode, selecting the root terminal and typing restart... then the ubuntu boots and everything works fine. However, when I want to launch ubuntu normally, it shuts down while booting. I managed to look at the temperature a few times and it never got over 50°C... So I don't assume it to be overheating. I'm starting to think there could be a hardware problem... my graphic card is ati radeon hd 3470

Does anybody have an idea what might be the cause?

---

### Post by sudodus on 2013-01-01
Welcome to the Ubuntu Forums :-)

I think that your operating system is not cooperating well with your graphics card. You made it work with one monitor, but it broke when you installed the fix for two monitors.

When you boot via recovery mode, will you have dual display, or only one display?

If you have dual display, then try to mimic that way to boot! Otherwise maybe you should try to uninstall the dual display settings.

There are some boot options, that you can see either directly in grub (type 'e' to view and or edit the boot command lines), or in the grub configuration files.

Check the entries in the file
```
/boot/grub/grub.cfg
``` Look for a line similar to
```
        linux   /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=cdc8b4a7-46af-43bd-91fc-030c21ef9887 ro recovery [COLOR="Red"]nomodeset[/COLOR] 

```
Probably the critical boot option is [FONT="Courier New"][SIZE="3"]nomodeset[/SIZE][/FONT] Of course you should not add [FONT="Courier New"]recovery[/FONT] 


In the following file
```
/etc/default/grub
```
check and change the following line to match what is used in recovery mode
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so for example (I don't know about all your boot options)
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Finally, run ```
sudo update-grub
``` and reboot!

Good luck :KS

---

### Post by RockStone9 on 2013-01-01
I've tried it (it was "nomodeset") and still the same, even had some troubles with getting to ubuntu via recovery mode...

---

### Post by 2F4U on 2013-01-01
Unexpected shutdowns or crashes can also be an indication of a hardware problem such as bad RAM. Did you run memtest to make sure your RAM is ok?

---

### Post by RockStone9 on 2013-01-01
tried, memtest shuts down as wel...

and about the dual display, when I set it in AMD CCC it asks me to reboot, and after rebooting and repeating the recovery mode way, the dual display occurs only when logging in, afterwards it switches back to mirror (clone) displays.

---

### Post by 2F4U on 2013-01-01
> **RockStone9 said:**
> tried, memtest shuts down as wel...

and about the dual display, when I set it in AMD CCC it asks me to reboot, and after rebooting and repeating the recovery mode way, the dual display occurs only when logging in, afterwards it switches back to mirror (clone) displays.

Am I right in assuming that you tried memtest from a liveCD, i. e. not booting into the installed system and running memtest from there? If your system is even shutting down from running memtest of a liveCD, my guess would be a serious hardware problem.

---

### Post by sudodus on 2013-01-01
> **RockStone9 said:**
> tried, memtest shuts down as wel...

and about the dual display, when I set it in AMD CCC it asks me to reboot, and after rebooting and repeating the recovery mode way, the dual display occurs only when logging in, afterwards it switches back to mirror (clone) displays.
1. Memtest should not shut down, and it is only text mode, and it should not depend on any advanced setting in the operating system. Try adding nomodeset to the grub command line for memtest and try to run it for a long time.

If the RAM is bad (you get errors), and you have more than one RAM card, take one card out each time, run memtest to find out which one is bad.

2. If the RAM is OK, check that the HDD is OK, [COLOR="Red"]because your system seems to change very quickly[/COLOR].

a. The file system(s). Boot from the Ubuntu install drive. Check with
```
sudo e2fsck -f /dev/sd[COLOR="Red"]xy[/COLOR]
```
where x is the drive letter and y is the partition number, for example /dev/sda5

b. The disk hardware. Check the S.M.A.R.T. status, probably there is a summary is a BIOS menu. Otherwise use for example ***smartctl*** installed with ***smartmontools***.

If this won't work, I think you need to move your hard disk drive to another computer and try to rescue what is possible to read. ***ddrescue*** is a good tool.

---

### Post by RockStone9 on 2013-01-01
I tried to run memtest without live CD... after the PC starts I get to choose between win, linux, linux recovery, older versions.. and memtest.
I also tried running memtest with one card at a time (1GB, 2GB) and each time it shuts down... if I recall correctly (getting confused from everything I've tried so far) I had tried SMART check yesterday with smartmontools and the disk turned out to be ok

and I can't add the nomodeset line because I've started having difficulties to get into the ubuntu...

---

### Post by sudodus on 2013-01-01
> **RockStone9 said:**
> I tried to run memtest without live CD... after the PC starts I get to choose between win, linux, linux recovery, older versions.. and memtest.
I also tried running memtest with one card at a time (1GB, 2GB) and each time it shuts down... if I recall correctly (getting confused from everything I've tried so far) I had tried SMART check yesterday with smartmontools and the disk turned out to be ok

and I can't add the nomodeset line because I've started having difficulties to get into the ubuntu...
You do that directly editing the grub menu at boot. Press 'e' to enter edit mode.

I'm glad your HDD passed the S.M.A.R.T. test, yet as 2F4U indicated, it might be a good idea to start memtest from an external CD/DVD/USB drive, because then you eliminate possible errors of the internal HDD.

If still no success to even run memtest, there is probably some other problem with the hardware (motherboard, cpu, graphics card ...)

---

### Post by RockStone9 on 2013-01-01
I can't launch the memtest from a live CD, the notebook shuts down before it gets to boot up...
I do believe it's a hardware problem...
I think it's about time to get a new notebook... this one served me for more than 6 years, but I'm afraid its time has come :-)

---

### Post by sudodus on 2013-01-01
Yes, maybe it is dying. I glad that the S.M.A.R.T. was good yesterday. Probably you can take the HDD out of the laptop, attach it to another computer and save your personal data.

---

### Post by RockStone9 on 2013-01-01
done... and now, what to do with this notebook? i will probably use the hdd as an external one for the next notebook...

---

### Post by sudodus on 2013-01-01
> **RockStone9 said:**
> done... and now, what to do with this notebook? i will probably use the hdd as an external one for the next notebook...
Maybe you can also keep the RAM or give it to someone with a computer that can use it.

Is there a recycling facility that accepts electronic scrap in your town?

---

### Post by RockStone9 on 2013-01-01
I think so... I'll see. Maybe I'll use some parts for my new machine. Anyway, thanks.

---

