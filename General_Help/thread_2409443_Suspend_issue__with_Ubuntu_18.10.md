---
title: "Suspend issue  with Ubuntu 18.10"
date: 2019-01-02
forum: General Help
---

### Post by STPitcher on 2019-01-02
I have a System76 laptop.  I recently did a clean install of Ubuntu 18.10

Every time I close the lid, I think it successfully suspends.  But then when I open the lid, the windows flash, the touch pad moves the pointer, but clicking the touch 
pad does nothing.  Moving the pointer over the task bar causes the windows to flash extra.

I can resolve this by hitting the power button, which is set to suspend.  When I hit the power button again to turn it back on, it comes up properly.

Every other time it suspends, it does this.  I can duplicate it with hitting the power button (suspend) rather than closing the lid.  Second time I hit the power button, it comes up cleanly.

Oh yes.  When it comes up badly, it doesn't display the password screen.  THis makes me wonder if it successfully suspended.  But the running light turns off, as though it is really suspended.

Any help?  Any way to trouble shoot?

Thanks for any suggestions.

- stp

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]STPitcher[/COLOR]**]("https://ubuntuforums.org/member.php?u=608815"),

Can you please provide us with the hardware specs of your laptop (and especially its graphic card/s), and also if you are using a proprietary driver on Ubuntu (I'm thinking of the NVIDIA drivers).

If you are using the nouveau driver, can you please try the following steps then reboot and see if this has helped resolved your issue:

1. In Terminal, run: sudoedit /etc/default/grub
2. Modify the line that reads "GRUB_CMDLINE_LINUX" to: GRUB_CMDLINE_LINUX="nouveau.modeset=0"
3. Save the changes.
4. Run: sudo update-grub
5. Reboot and try waking up from suspend mode again.

If this does not work, can you please check in your BIOS what is the preferred graphics card to use (assuming that you have a laptop with discrete + onboard graphics, i.e. Intel + NVIDIA). If it is set to NVIDIA (or dedicated graphics), can you please try switching it to Intel (or onboard) and see if the issue persists.

---

### Post by STPitcher on 2019-01-02
Thanks

steve@Mink:~$ lspci 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
steve@Mink:~$

Not aware that I'm running nouveau drivers.

Does this give you what you're asking for?

- steve

---

### Post by clementc on 2019-01-02
Hi Steve,

Would you mind running the following command please: sudo lshw -c display

---

### Post by STPitcher on 2019-01-02
*-display                 
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:128 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
steve@Mink:~$

---

### Post by clementc on 2019-01-02
Hi [**STPitcher**]("https://ubuntuforums.org/member.php?u=608815"),

You are not using the nouveau (NVIDIA) driver but i915.

Can you please try installing the following applications:
- GNOME Tweaks
- The Dash to Dock extension.

I know that it does not seem to be related with your issue, but I noticed some odd behaviors after waking up from suspend mode on Ubuntu 18.10 until I installed both applications and configured Dash to Dock to my liking.

---

### Post by STPitcher on 2019-01-02
It worked!

Thanks.  

I don't in the slightest understand Dash to Dock.  But my problem now appears to be resolved!

- steve

---

### Post by clementc on 2019-01-03
Hi Steve,

No worries, I am glad that your issue is now resolved.

---

