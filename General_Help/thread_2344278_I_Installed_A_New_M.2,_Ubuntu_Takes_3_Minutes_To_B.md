---
title: "I Installed A New M.2, Ubuntu Takes 3 Minutes To Boot"
date: 2016-11-23
forum: General Help
---

### Post by ThePowerpuffGirls on 2016-11-23
When I installed Ubuntu on my SAMSUNG 850 EVO M.2, I noticed a new message at the top of the screen when the screen goes black before the UI displays. It says *ERROR* conflict detected w"

It seems to work without issue except that it take a really long time to boot; it hangs.
I looking at the boot screen that says UBUNTU and the 5 dots at below it light up one at a time and turn off. This is not the first M.2 i have. I've installed one, same model on another computer without issue.

For some reason, this computer seems to different, and had some weird issues, like my one with VLC that I posted earlier this month.

I was going to reinstall, until I noticed that error come up again right before the install screen comes on.

OS: Ubuntu 16.04 (x64)
SSD/HDD:
1. SAMSUNG 850 EVO 250GB (M.2)
2. SAMSUNG 850 EVO 250GB (SATA)
3. Hitachi 4TB (7200RPM/64MB Cache) (SATA)
Motherboard: ASUS B150 Pro-Gaming/AURA
RAM: Kingston HyperX 16GB (1x16GB) DDR4 2133
Processor: Intel® Core&#8482; i7-6700K CPU @ 4.00GHz (×8)
Graphics: Intel® HD Graphics 530 (Skylake GT2)
WLAN PCI-E: ASUS PCE-N15 B/G/N 300Mbps

---

### Post by oldfred on 2016-11-23
This may show errors?
 Newer systems with systemd:
systemd-analyze blame 

Is this also an NVMe drive or just M.2?

---

### Post by ThePowerpuffGirls on 2016-11-23
I'm not sure if it has NVMe. I still have the box. How do I find that out?

I get this for the command:
```

         2.603s upower.service
           288ms vboxdrv.service
           189ms dev-sda2.device
           168ms apparmor.service
           134ms ModemManager.service
           118ms systemd-localed.service
            88ms accounts-daemon.service
            87ms systemd-logind.service
            80ms lightdm.service
            79ms irqbalance.service
            74ms grub-common.service
            68ms speech-dispatcher.service
            67ms plymouth-quit-wait.service
            63ms apport.service
            62ms ondemand.service
            61ms systemd-hostnamed.service
            52ms snapd.firstboot.service
            51ms alsa-restore.service
            50ms gpu-manager.service
            49ms binfmt-support.service
            45ms NetworkManager.service
            44ms rsyslog.service
            43ms pppd-dns.service
lines 1-23...skipping...
          2.603s upower.service
           288ms vboxdrv.service
           189ms dev-sda2.device
           168ms apparmor.service
           134ms ModemManager.service
           118ms systemd-localed.service
            88ms accounts-daemon.service
            87ms systemd-logind.service
            80ms lightdm.service
            79ms irqbalance.service
            74ms grub-common.service
            68ms speech-dispatcher.service
            67ms plymouth-quit-wait.service
            63ms apport.service
            62ms ondemand.service
            61ms systemd-hostnamed.service
            52ms snapd.firstboot.service
            51ms alsa-restore.service
            50ms gpu-manager.service
            49ms binfmt-support.service
            45ms NetworkManager.service
            44ms rsyslog.service
            43ms pppd-dns.service
            42ms udisks2.service
lines 1-24...skipping...
          2.603s upower.service
           288ms vboxdrv.service
           189ms dev-sda2.device
           168ms apparmor.service
           134ms ModemManager.service
           118ms systemd-localed.service
            88ms accounts-daemon.service
            87ms systemd-logind.service
            80ms lightdm.service
            79ms irqbalance.service
            74ms grub-common.service
            68ms speech-dispatcher.service
            67ms plymouth-quit-wait.service
            63ms apport.service
            62ms ondemand.service
            61ms systemd-hostnamed.service
            52ms snapd.firstboot.service
            51ms alsa-restore.service
            50ms gpu-manager.service
            49ms binfmt-support.service
            45ms NetworkManager.service
            44ms rsyslog.service
            43ms pppd-dns.service
            42ms udisks2.service
            41ms avahi-daemon.service
            38ms proc-sys-fs-binfmt_misc.mount
            38ms systemd-udev-trigger.service
            37ms thermald.service
            37ms keyboard-setup.service
            35ms boot-efi.mount
            35ms console-setup.service
            28ms plymouth-start.service
            23ms networking.service
            23ms systemd-journald.service
            19ms systemd-tmpfiles-setup-dev.service
            18ms systemd-tmpfiles-clean.service
            17ms systemd-fsck@dev-disk-by\x2duuid-C7C7\x2dEE17.service
            16ms systemd-modules-load.service
            16ms rtkit-daemon.service
            15ms systemd-udevd.service
            15ms systemd-tmpfiles-setup.service
            13ms wpa_supplicant.service
            13ms plymouth-read-write.service
            11ms systemd-rfkill.service
            10ms user@1000.service
lines 1-45

```

---

### Post by oldfred on 2016-11-23
Not much showing slow boot.
Not sure what upower is but that still is only 2.6 sec.

My network manager is the long time for me and it shows 8 sec. Everything else is similar.

If NMVe the drives/partitions are not mounted as sda, but nmve devices.

---

### Post by mc4man on 2016-11-24
Maybe just take a look at plain systemd-analyze command & see if some 'section' is using abnormal time. Here it will break as 4, (loader) includes a greeter screen..
$ systemd-analyze (autologin
Startup finished in 2.068s (firmware) + 3.543s (loader) + 3.168s (kernel) + 1.071s (userspace) = 9.851s

$ systemd-analyze (greeter
Startup finished in 2.052s (firmware) + 5.300s (loader) + 3.054s (kernel) + 828ms (userspace) = 11.235s

---

### Post by ThePowerpuffGirls on 2016-12-05
IT started as soon as I installed the M.2 drive, I'm going back to SATA, because I'd nothing but trouble with the M.2 drives. MY main computer hangs every 2nd time I start it up between the login and desktop screen, and hangs shutting down. I can't remember if it did it with the SATA. I think it's a cool idea for the M.2, but unfortunately, they don't work for well for me. WHen it hangs on my main computer, the drives don't show up, and I have to restart.

---

### Post by Keith_Helms on 2016-12-06
The Samsung 850 EVO uses SATA whether you buy the M.2 format or the 2.5" format.  Do you have any other SATA devices?  The manual for your motherboard says this: "When the M.2 Socket 3 is operating in SATA mode, SATA port 1 will be disabled."

---

### Post by ThePowerpuffGirls on 2016-12-08
To me that doesn't make sense since M.2 and SATA are two different interfaced from my understanding. The SATA has the cables while the M.2 has a chip unless if there was a M.2 to SATA adapter.

---

### Post by Irihapeti on 2016-12-08
This might throw some light on the matter:
[https://rog.asus.com/articles/hands-on/easy-guide-to-ssds-sata-msata-m-2-and-u-2/](https://rog.asus.com/articles/hands-on/easy-guide-to-ssds-sata-msata-m-2-and-u-2/)

---

### Post by Keith_Helms on 2016-12-09
> **ThePowerpuffGirls said:**
> To me that doesn't make sense since  M.2 and SATA are two different interfaced from my understanding. The  SATA has the cables while the M.2 has a chip unless if there was a M.2  to SATA adapter.

The M.2 port accepts circuit boards with an edge connector that plugs  into the port.  Those circuit boards can use different sets of the  "pins" provided by the port which is reflected by one or 2 notches in  different places on the edge connector.  The M.2 port provides the  circuit board with access to different internal system buses depending  on the notches used and the chipset on the card.   So, an SSD in M.2  format can hook into the system through either the PCIe bus, the USB  bus, or the SATA bus.

When M.2 first appeared, many manufacturers just took their existing  2.5" SATA SSDs and changed the form factor, but continued to use the  SATA interface.  The Samsung 850s are one of those that come in both  2.5" and M.2 form factors.  You're still limited by the maximum SATA  speed of 6 Gb/s.  Newer M.2 SSDs take advantage of the faster speed  allowed by using the PCIe bus.   The Samsung 950, 951, and 960 drives  use the PCIe/NVMe interface.

Look at this search result on Amazon for Samsung M.2 drives:
[https://www.amazon.com/s/ref=sr_nr_p_89_0?fst=as%3Aoff&rh=n%3A172282%2Cn%3A541966%2Cn%3A1292110011%2Cn%3A1292116011%2Ck%3Assd+drives+m.2%2Cp_89%3ASamsung&keywords=ssd+drives+m.2&ie=UTF8&qid=1481278750&rnid=2528832011](https://www.amazon.com/s/ref=sr_nr_p_89_0?fst=as%3Aoff&rh=n%3A172282%2Cn%3A541966%2Cn%3A1292110011%2Cn%3A1292116011%2Ck%3Assd+drives+m.2%2Cp_89%3ASamsung&keywords=ssd+drives+m.2&ie=UTF8&qid=1481278750&rnid=2528832011)

You'll notice the 850s have 2 notches in the edge connector and is  called a M.2 SATA III Internal SSD, while the 950, 951, and 960s only  have one notch in the connector and are called M.2 PCI Express Gen3 x4  Solid state drive SSD.  That tells you they're using a different  interface.

So, quick summary - the M.2 port allows interfacing with multiple system buses including SATA.

---

### Post by ThePowerpuffGirls on 2016-12-12
OK, thanks. I'm sorry to the delay in response.
I'm will install 2.5 SATA in the computer downstairs and see if that helps. If it does, then there is something wrong with the M.2, some kind of a defect, or something. I can't imagine what would cuase it to take so long to boot up. ALso, that error 'conflict detected w', which I've only seen after installing the M.2.

---

### Post by Keith_Helms on 2016-12-12
> **ThePowerpuffGirls said:**
> OK, thanks. I'm sorry to the delay in response.
I'm will install 2.5 SATA in the computer downstairs and see if that helps. If it does, then there is something wrong with the M.2, some kind of a defect, or something. I can't imagine what would cuase it to take so long to boot up. ALso, that error 'conflict detected w', which I've only seen after installing the M.2.

The reason I asked you if you had any SATA devices was because the doc for your motherboard indicated using an SATA mode M.2 card would conflict with using SATA port 1.  If you're using port 1 along with the M.2 card, that just might generate a "conflict detected" error.

---

### Post by ThePowerpuffGirls on 2016-12-24
Oh, OK. I will check and maybe maybe that is causing it to be extremely slow booting up.

---

### Post by ThePowerpuffGirls on 2016-12-28
I'd just checked the SATA port and there is nothing plugged into the first two. I just checked the manual to make sure. SATA 3-6 are in use.

---

### Post by Yellow Pasque on 2016-12-28
Try disabling the splash screen (even just for one boot) to see if you get a more helpful error message.

---

### Post by ThePowerpuffGirls on 2017-01-05
I did. I pressed F11 and got a 'a start job has' something and get a message like
'dev disk'.

Update:
I fixed it. I deleted the swap partition, and removed the swap thingie listed in fstab, and restarted. It now boot up in 10 seconds or less.

---

### Post by ThePowerpuffGirls on 2017-01-11
I installed a M.2 drive on another computer. and have the same thing: *ERRO* conflict detected w. init something. I have a picture pf it, but it's on my Mum's phone. I guess that means that the BIOS (UEFI?) disabled SATA6_1.
I don't get this error on my main desktop, which is a ASUS Z97-K and has a M.2, maybe becuase the BIOS/UEFI isn't set up that way.

Is there a way to set it differently, or is it changeable?

Thank you for your help and input. :)

---

