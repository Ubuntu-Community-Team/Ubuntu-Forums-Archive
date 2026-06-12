---
title: "NetworkManager-wait-online.service and nvmf-autoconnect.service failing on boot?"
date: 2022-06-18
forum: General Help
---

### Post by johntdavis on 2022-06-18
Hello, everyone. I'm new to Ubuntu, but an ... experienced newbie (?) with Manjaro. I've got a Khadas VIM4 single board computer running their tweaked version of Ubuntu (with their drivers), and I'm seeing some odd behavior with failing services on startup.

[COLOR=#ff8c00][FONT=Menlo]:**~**$ systemctl --failed[/FONT]
[FONT=Menlo]  UNIT                               LOAD   ACTIVE SUB    DESCRIPTION                                         [/FONT][/COLOR]
[COLOR=#941F21][FONT=Menlo]**&#9679; NetworkManager-wait-online.service **[/FONT][/COLOR][COLOR=#ff8c00][FONT=Menlo]loaded [/FONT][/COLOR][COLOR=#941F21][FONT=Menlo]**failed failed **[/FONT][/COLOR][COLOR=#ff8c00][FONT=Menlo]Network Manager Wait Online[/FONT][/COLOR][COLOR=#941F21][FONT=Menlo][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=Menlo][COLOR=#941F21]**&#9679; nvmf-autoconnect.service           **[/COLOR][/FONT][/COLOR][COLOR=#ff8c00][FONT=Menlo]loaded[/FONT][/COLOR][COLOR=#2FFF12][FONT=Menlo] [COLOR=#941F21]**failed failed **[/COLOR][/FONT][/COLOR][COLOR=#ff8c00][FONT=Menlo]Connect NVMe-oF subsystems automatically during boot[/FONT][/COLOR][COLOR=#2FFF12][FONT=Menlo][/FONT][/COLOR]

I'm not sure if this is an Ubuntu issue or an issue with their hardware, but I wanted to ask here first in case I was missing something obvious about what's causing these. If either of these *should* be working out of the box, please let me know, and I'll know it's an issue with the Khadas VIM4 beta OS.

I've got network access, and two separate partitions mounted and working on my NVME, so I suspect these are indicative of the network and NVME just not coming up *fast* enough for systemd to be happy. That said, I'm particularly concerned with _NetworkManager-wait-online.service_--I'm not booting off the network, but I know that some services need the network to be online to come correctly. I'm wary of just disabling it, even though it's recommended, e.g., here: [https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) . Is there a way I can tell what services actually need this to work properly? In the alternative, is there a way to extend the delay before it times out?

I'd never heard of NVMe-oF (NVME Over Fabrics), but I think that's what the nvme service is trying to auto-mount? I installed _nvme-cli_ to grab some diagnostic data off my data drive. Maybe it came with that?

I'd appreciate any troubleshooting suggestions. More output below.

Thanks!

```
khadas@Khadas:~$ systemctl status NetworkManager-wait-online.service 
× NetworkManager-wait-online.service - Network Manager Wait Online
     Loaded: loaded (/lib/systemd/system/NetworkManager-wait-online.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sat 2022-06-18 23:14:23 CST; 3h 52min ago
       Docs: man:nm-online(1)
    Process: 982 ExecStart=/usr/bin/nm-online -s -q (code=exited, status=1/FAILURE)
   Main PID: 982 (code=exited, status=1/FAILURE)
        CPU: 122ms


Jun 18 23:13:23 Khadas systemd[1]: Starting Network Manager Wait Online...
Jun 18 23:14:23 Khadas systemd[1]: NetworkManager-wait-online.service: Main process exited, code=exited, status=1/FAILURE
Jun 18 23:14:23 Khadas systemd[1]: NetworkManager-wait-online.service: Failed with result 'exit-code'.
Jun 18 23:14:23 Khadas systemd[1]: Failed to start Network Manager Wait Online.
khadas@Khadas:~$ systemctl status nvmf-autoconnect.service 
× nvmf-autoconnect.service - Connect NVMe-oF subsystems automatically during boot
     Loaded: loaded (/lib/systemd/system/nvmf-autoconnect.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sat 2022-06-18 23:14:23 CST; 3h 52min ago
    Process: 1112 ExecStartPre=/sbin/modprobe nvme-fabrics (code=exited, status=1/FAILURE)
        CPU: 5ms


Jun 18 23:14:23 Khadas systemd[1]: Starting Connect NVMe-oF subsystems automatically during boot...
Jun 18 23:14:23 Khadas modprobe[1112]: modprobe: FATAL: Module nvme-fabrics not found in directory /lib/modules/5.4.125
Jun 18 23:14:23 Khadas systemd[1]: nvmf-autoconnect.service: Control process exited, code=exited, status=1/FAILURE
Jun 18 23:14:23 Khadas systemd[1]: nvmf-autoconnect.service: Failed with result 'exit-code'.
Jun 18 23:14:23 Khadas systemd[1]: Failed to start Connect NVMe-oF subsystems automatically during boot.

```

---

### Post by TheFu on 2022-06-18
```
Jun 18 23:14:23 Khadas modprobe[1112]: modprobe: FATAL: Module nvme-fabrics not found in directory /lib/modules/5.4.125
```
That's the error I'd run down. I doubt there's any solution besides getting the correct driver for the hardware and kernel.

That's an expensive piece of kit you have but does so much more than a r-pi - more processors, the eMMC storage, almost too much video processing.  Nice.  [https://www.khadas.com/product-page/vim4](https://www.khadas.com/product-page/vim4) for people unfamiliar. 

I've never needed 'tiny' more than money.  

BTW, thanks for using code tags.  The odd colors are confusing, however.

I don't use network manager, so my advice around it is usually unwanted.  I'd say purge it, setup static IPs and be done. No more issues ... ever.  I'd also purge systemd-resolved and just edit /etc/resolv.conf.  No need to make those things complicated.  DHCP just screws up things that are simple.

---

### Post by johntdavis on 2022-06-18
Thanks, @TheFu. :) Sorry about the odd colors. I wasn't expecting the forum to actually paste in the color, and it pasted in as a searing, radioactive mutagen green. The orange and red looked better on my screen, but apparently still came off strange. I will be mindful of that in future and avoid color at all. :)

**I completely missed the `modprobe` statement; my fault for trying to troubleshoot on not enough caffeine. Thanks for pointing it out. I wonder if it's because I'm on an LTS kernel? I'd never heard of NVME over Fabric until today. On a hunch, I uninstalled the `nvme-cli` package. That made both fail statements disappear. **Unfortunately, it looks like that package installs quite a bit more than just diagnostic tools, which was not clear to me when I installed it. I'd rather pull the package than install a subsystem with kernel modules that I don't understand, so this is a fine outcome. :)

The VIM 4 is excellent--I did indeed grab it as an upgrade for my Pi, which I use for a lot of self-hosted stuff. The additional, more powerful CPU cores, 8 GB of RAM, and native NVME and eMMC (instead of having to do everything over USB bridges) appealed, and solved *most* of the problems I have had with using the Pi, which boil down to (1) needing to depend on a lot of USB peripherals, including storage; and (2) the Pi 4b's USB subsystem and power delivery not really being up to the task of being used like a mini server or desktop, even though it's increasingly marketed for that. (e.g., I could plug in an external NVME in a USB 3 enclosure, OR a 2.5GbE ethernet adapter, but not both, or the thing wouldn't boot. Not to mention it took two tries to find a powered USB hub that it would actually boot when plugged into, and I still don't know the difference between them since they're both Sabrent.

That said, I'd probably not buy it yet if I had it to do over--I didn't realize the OS and drivers are still in beta, and there have been ... issues. I had to learn how to move home directories and persistent data storage off the eMMC, because we're still having to flash new OS updates in to fix hardware issues ... like the NVME not working. Oh, well. #TheMoreYouKnow, I guess. :P

I didn't consider it too expensive, given all the extra features and improved power delivery system over the Pi 4 8GB, which is *supposed* to be $100 but is around $150+ most of the time. It's primarily going to serve as a DNS server and do some other critical things that need to keep working if my bigger iron goes down, so it's worth it for that, I think. But yes, the video capabilities are ludicrous.

---

### Post by TheFu on 2022-06-18
I fear you'll find this machine doesn't catch on and build the same community that Raspberry Pi has.  That's the nature of all the non-Pi hardware that I've seen.  They just never catch on.

Whereas we can get small x86-64 systems that use 12W, support AMD-v or VT-x so full virtualization is possible with SATA, mSATA, SDHC and USB3 for around $120.  I have one of the APU2 models which I use as a WAN router, but friends use them for things other people might think to get a r-pi.

Full x86-64 compatibility is fantastic.  Stability is fantastic, but there isn't any video GPU at all, so many people would not touch them.  It isn't like using a serial console is THAT hard.  For servers, don't fear the console.  ssh is how servers are managed anyway.

I self-host almost everything and have over 20 yrs.  I just can't see trusting any cloudy company with my email server.

---

