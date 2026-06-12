---
title: "Enable low power settings for NAS box running Ubuntu Server"
date: 2013-04-20
forum: General Help
---

### Post by onlinespending on 2013-04-20
I have installed Ubuntu Server 13.04 (Raring Ringtail) on a NAS box that I only intend to be able to SSH into it for maintenance. It has no GUI installed and is not connected to a monitor. Since this device will be on quite a bit, I'd like to reduce power consumption as much as possible.

+ Graphics
  - since the box won't even be able to monitor is there a way to disable the GPU or force it into a low power state?
  - how can I adjust when the "monitor" turns off from the command line (I know how to in gnome). This may help reduce power since it won't be actively driving video out.

+ S3 Standby
  - how can I adjust the standby delay from the command line?

+ ALPM (Link Power Management)
  - I've seen a lot discussed about this, but nothing definitive about how to enable this in 13.04. One document says to use "echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm", but I don't even have an /etc/pm/config.d directory. Just /etc/pm/sleep.d.

+ CPUFREQ
  - I'd like to set it to use the conservative governor.

+ Anything else?
  - I'm all for reducing power consumption as much as possible on this machine, so if it can essentially be run in a laptop mode that would be nice.

Thanks for any suggestions!

---

### Post by onlinespending on 2013-04-22
Seems there's a nice little utility called TLP that offers a lot of power management control. Is this what people still recommend for 13.04? Thanks

---

### Post by tgalati4 on 2013-04-22
If your monitor is not connected, then your graphics card should not fire up since it negotiates with the monitor to determine the resolution and refresh rate.

cpufreq should be set up automatically if your processor supports it.  You didn't tell us any details for your hardware.  There are several tools you can use:

tgalati4@Mint14-Extensa ~ $ apropos cpufreq
cpufreq-aperf (1)    - Calculates the average frequency over a time period
cpufreq-info (1)     - Utility to retrieve cpufreq kernel information
cpufreq-set (1)      - A small tool which allows to modify cpufreq settings.

You can use *hdparm* with switches to spin down the disks after a certain period of time.  Run the OS off of a USB stick with persistance (to save your config files), so your hard disks won't stay away for the operating system.  The downside is that your log files get lost in RAM when you lose power.  

S3 standby is normally controlled by the BIOS, so look in the BIOS and see if you can change it.  

Your best investment is a Kill-a-Watt meter that measures actual wattage used over a period of time.  My old, whitebox server uses 45 watts.  An even older whitebox running freenas uses 35 watts.  I have two Dell PowerEdge 1750 servers that use 215 to 240 watts each depending on load.  Those I keep asleep and wake when I'm doing development work.  Depending on your electric rates, it pays to get a low-power board (Intel Atom, Via C7, or even Raspberry Pi).  I have a Via C7 microboard that uses 12 watts.  I think the Raspberry Pi's are 2 to 5 watts, but I don't have one, so someone else will have to chime in on their power usage.

---

