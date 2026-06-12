---
title: "Slow boot older machine"
date: 2020-07-06
forum: General Help
---

### Post by Otto-C on 2020-07-06
HP 6710b Compaq Ubuntu 18.04. After booting takes 5 Minutes runs a little slow and
sometimes hangs. Not new but wanted to ask.
tia oldcity

Results of systemd-analyze blame

> 

oldcity-u:~$ systemd-analyze blame
     2min 6.171s plymouth-quit-wait.service
    1min 51.853s gpu-manager.service
         24.518s systemd-journal-flush.service
         23.607s dev-sda1.device
         16.571s systemd-sysctl.service
         14.684s systemd-udevd.service
         14.441s snap-gnome\x2dsystem\x2dmonitor-135.mount
         13.910s colord.service
          7.723s snapd.service
          6.416s NetworkManager.service
          5.930s NetworkManager-wait-online.service
          5.138s networkd-dispatcher.service
          4.607s snap-communitheme-1987.mount
          4.460s snap-gnome\x2d3\x2d26\x2d1604-100.mount
          4.221s snap-core-9436.mount
          4.177s snap-core-9066.mount
          4.024s snap-core18-1754.mount
          3.817s snap-gnome\x2dlogs-100.mount
          3.620s udisks2.service
          3.415s dns-clean.service
          3.186s snap-gnome\x2dcalculator-748.mount
          3.037s apparmor.service
          2.876s systemd-tmpfiles-setup-dev.service


---

### Post by Autodave on 2020-07-06
Someone with more knowledge than myself can probably give you more help than I can, but here is my 2 cents worth.  That machine is not fast and only has 2 gig RAM unless you updated it.  I would suggest switching to a lighter desktop such as Xubuntu.

I am actually running Xubuntu on a machine quite similar to what you have, and I get boot time of just over a minute.

---

### Post by GhX6GZMB on 2020-07-06
I'm using a hp6910p, which is practically the same except for the display size (6910: 14.1", 6710: 15.4").

Tried Ubuntu, but it's too heavy for the machine.
I switched to Lubuntu, which runs perfectly with 2 GB (but even better with 4 GB). Am currently at Lubuntu 20.04 LTS, no hiccups at all.

Boot times:
120 GB original HDD: 100 seconds.
new 240 GB SSD: 25 seconds.

I also had very long boot times in the beginning, this relates to a problem with the i965 chipset. I wrote a little essay how to fix it here:
[https://ubuntuforums.org/showthread.php?t=2130640&page=23](https://ubuntuforums.org/showthread.php?t=2130640&page=23) post #223

Good luck.

---

### Post by ActionParsnip on 2020-07-06
If you reboot then run:
```

dmesg -T | less

```
You can look for large gaps in time and this will help diagnose.

Also make sure you have the latest BIOS.

---

### Post by T6&amp;sfpER35% on 2020-07-06
> [COLOR=#000000]Also make sure you have the latest BIOS[/COLOR]
speaking of , how does one go about checking/upgrading that?

---

### Post by GhX6GZMB on 2020-07-06
> **3nd said:**
> speaking of , how does one go about checking/upgrading that?

Quite frankly, don't go there.
If it fails, you'll just have a bricked machine and there's NO support to be found for a 12+ years old laptop.

---

### Post by T6&amp;sfpER35% on 2020-07-06
thanks ,wont do that then ,since i don't have a problem lol , was just wondering as iv'e seen a couple posts suggesting to upgrade BIOS

---

### Post by GhX6GZMB on 2020-07-06
> **3nd said:**
> thanks ,wont do that then ,since i don't have a problem lol , was just wondering as iv'e seen a couple posts suggesting to upgrade BIOS

The suggestion of upgrading the BIOS is an act of pure desperation when everything else has failed.

I've never really seen an issue with a BIOS. The BIOS is firmware, meaning you should see it as an integral part of your hardware. It may be that a new version will provide a couple of new functions or boot menu changes, but they're in no way essential.
Leave it alone, it works and interacts correctly with your hardware, otherwise your machine would never have left the factory.

---

### Post by kneutron on 2020-07-07
> [COLOR=#000000]I've never really seen an issue with a BIOS. The BIOS is firmware, meaning you should see it as an integral part of your hardware. It may be that a new version will provide a couple of new functions or boot menu changes, but they're in no way essential

--Slightly OT, but I have. Old dual-core desktop system probably XP-era converted to server, that wouldn't work right with PCBSD until BIOS was upgraded to latest.  Just because "I haven't seen it" doesn't mean it's not a factor, BIOS updates also provide bugfixes. :)

Example:

[/COLOR][https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=y5fnt](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=y5fnt)

---

