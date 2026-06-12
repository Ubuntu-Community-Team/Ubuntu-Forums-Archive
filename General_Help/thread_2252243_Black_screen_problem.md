---
title: "Black screen problem"
date: 2014-11-10
forum: General Help
---

### Post by bbullett on 2014-11-10
This problem is not only related with ubuntu. I tried different distros. Black screen appears when HDD is loaded 100%. E.x: when OS boots and I start firefox while HDD indicator is lighted on, system freezes and after 2 seconds black screen appears. While this black screen I tried CTRL+ALT+F1 and suspended PC then started it and tty appeard, but I was unable to restart lightdm or run startx. My PC is Acer extensa 5220, I tried different distros like fedora, opensuse and even chromeos, but each fails. I have also changed CPU to Pentium T4300, changed ram and hdd but this problem still exists. Can you help me to solve this problem?

---

### Post by Bashing-om on 2014-11-10
bbullett; Hello ;

A black screen is often a graphics issue.
Can you boot up the liveDVD(USB) ?
Yes, then can you boot to grub's boot menu in the install ? ( when bios screen clears depress the -shift- key [legacy] OR escape key [EFI]

Then we can examine what graphics the system is using.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by bbullett on 2014-11-10
Yes, I can boot liveDVD(USB). "About this computer" says: Graphics Intel 965GM x86/MMX/SSE2
```
sudo lshw -c video  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc100000-fc1fffff



```

---

### Post by Bashing-om on 2014-11-11
bbullett; Hey :

Intel graphics is not an area I am familiar with, however, we can do a bit more looking.
This:
> 
Mobile GM965/GL960 Integrated Graphics Controller (primary)

Makes me consider what we have here is hybrid graphics. The system can not tell what to do in this situation. Perhaps we can give it better direction ?
What returns:
```

lspci -nnk | grep -iA3 vga

```
See if we can find out what we are dealing with; give us an indication what to do in the actual install.

[INDENT][INDENT]what to do, what to do
[/INDENT][/INDENT]

---

### Post by hans-nesse-6 on 2014-11-11
I have the same graphics card and apparently a similar problem.  I get a black screen whenever I go to specific websites on specific browsers (just started yesterday).  I wonder if it is the same problem you're running into.  Reliably, I get a black screen whenever I open the [www.google.com/chrome](www.google.com/chrome) website with Firefox.

I have not been able to replicate your issue starting firefox while the HDD light is on, but will try a bit more. I started a separate thread [here.]("http://ubuntuforums.org/showthread.php?t=2252367")

---

