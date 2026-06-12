---
title: "No resume from hibernate"
date: 2006-12-18
forum: General Help
---

### Post by buttari on 2006-12-18
Hi all,
since I upgraded to Edgy I can't resume from hibernate. I should say that the computer resumes (in fact I can ssh on it from another machine), but the display is blank.
I tried a couple of things found on the forum like redoing mkswap on the swap partition and updtae /etc/fstab and /etc/initram-tool/conf.d/resume but still no success. I also corrected the fstab swap entry replacing the uuid with the "old style" /dev/sda3 but nothing.
Ah, swapon -s says:
```

Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       1951888 75492   -1

```
Help would be greatly appreciated.
Thanks
Alfredo

---

### Post by buttari on 2006-12-18
bump.
nobody can help me?

---

### Post by Lord Illidan on 2006-12-19
--SRY Wrong post ---

---

### Post by Lord Illidan on 2006-12-19
> **Lord Illidan said:**
> Are you using the Nvidia drivers?


Give us the full specs of the pc.

---

### Post by buttari on 2006-12-19
so, my laptop is a Thinkpad T60p.

Centrino duo
1 GB Ram
ATI MOBILITY FireGL V5200
(need anything else?, not sure what to add)
Just upgraded to edgy and never installed anything outside the ubuntu repositories.

I went one step further. I hibernated, then I tried to resume. My display went blank as usual but I could ssh from another machine and do dmesg. Here's what I got:
```

[17189271.852000] ACPI Exception (evxface-0545): AE_BAD_PARAMETER, Removing notify handler [20060707]
[17189271.888000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17189271.888000] ibm_acpi: http://ibm-acpi.sf.net/
[17189271.892000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17189271.892000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[17189271.928000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[17189271.936000] Uhhuh. NMI received. Dazed and confused, but trying to continue
[17189271.936000] You probably have a hardware problem with your RAM chips
[17189271.952000] ACPI: AC Adapter [AC] (on-line)
[17189271.992000] ACPI: Battery Slot [BAT0] (battery present)
[17189272.080000] usb 2-1: configuration #1 chosen from 1 choice
[17189272.100000] input: HID 04b3:310b as /class/input/input6
[17189272.100000] input: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:1d.0-1
[17189272.340000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17189272.504000] usb 3-1: configuration #1 chosen from 1 choice
[17189272.564000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

It says that I have problems with my RAM. I'm not sure; should I try a memtest?
btw everything was working perfect before upgrading to edgy. One more thing: once I ssh I issue
```
$sudo reboot
```
I got the "System is going down for reboot" message but nothing happens.
Thanks

Alfredo

---

### Post by zanglang on 2006-12-20
Just a quick check, but have you made this change to your /boot/grub/menu.lst?
[http://ubuntuforums.org/showthread.php?t=287524](http://ubuntuforums.org/showthread.php?t=287524)

---

### Post by buttari on 2006-12-20
> **zanglang said:**
> Just a quick check, but have you made this change to your /boot/grub/menu.lst?
[http://ubuntuforums.org/showthread.php?t=287524](http://ubuntuforums.org/showthread.php?t=287524)

yes I tried it. I also tried to use the old style "/dev/sda3" instead of the uuid format in both /etc/fstab and /etc/initram-tools/conf.d/resume.
Thanks

Alfredo

---

### Post by Amaranth on 2006-12-21
What kind of laptop do you have?

---

### Post by pgilmon on 2006-12-22
Look at [this]("http://www.ubuntuforums.org/showthread.php?t=214129") post. Perhaps it will help you...

Take also a look at [this]("http://www.ubuntuforums.org/showpost.php?p=1674295&postcount=13"). I describe a problem that corrupted my filesystem while trying to get hibernation to work, perhaps it will save you from losing all your data.

I also had problems when upgrading to Edgy with hibernation. They were related to swap space. Edgy names the partition with unique ID's, and I think that swap space wasn't correctly sitched on, and since hibernation depends on swap, it didn't work correctly, I eventually had to reinstall everything from scratch and, with a fresh Edgy install (before installing nvidia proprietary drivers), hibernation worked. I guess it had to do with the new way of naming partitions, but since I had to reinstall everything I couldn't experiment much on it...

---

### Post by buttari on 2006-12-22
Hi,
thanks everybody for the help. Unfortunately none of the things you suggested worked. I think I'll go on without hibernation until I have time to do a fresh install.

Alfredo

---

### Post by dave_abrahams on 2006-12-24
> **buttari said:**
> Hi,
thanks everybody for the help. Unfortunately none of the things you suggested worked. I think I'll go on without hibernation until I have time to do a fresh install.

Alfredo

Don't hold your breath; my freshly-installed edgy won't suspend to RAM -or- disk, much less resume, on my t60p.

On my dapper installation I used suspend2 to suspend-to-disk (requires a kernel rebuild) and I had suspend-to-RAM working for a while but it mysteriously stopped.

---

### Post by buttari on 2006-12-24
> **dave_abrahams said:**
> Don't hold your breath; my freshly-installed edgy won't suspend to RAM -or- disk, much less resume, on my t60p.

On my dapper installation I used suspend2 to suspend-to-disk (requires a kernel rebuild) and I had suspend-to-RAM working for a while but it mysteriously stopped.

Uh oh,
ok, I'll wait for Feisty.
Thanks

Alfredo

---

### Post by dave_abrahams on 2006-12-25
I wouldn't count on it being fixed in feisty either.  Speaking very broadly, getting hibernate right "once and for all" doesn't seem to be a major priority in the Linux community, and it takes the cooperation of many different players.  FWIW, my stock edgy install suspends to RAM just fine... unless the machine is in my dock with a USB keyboard plugged in.  You might try installing uswsusp for suspend-to-disk.  At least it's entirely in userspace so there's no kernel rebuild required.

Good luck.

---

### Post by Amaranth on 2006-12-25
Getting hibernate right "once and for all" requires driver support, non-stupid hardware, and a non-broken BIOS. We're only in control of one part of this. :)

---

### Post by dave_abrahams on 2006-12-26
Very true, but somehow it manages to work flawlessly on every Windows XP laptop I've ever seen.  With sufficient will it should be possible to get it right on the linux laptops, too.

---

### Post by buttari on 2006-12-27
> **Amaranth said:**
> Getting hibernate right "once and for all" requires driver support, non-stupid hardware, and a non-broken BIOS. We're only in control of one part of this. :)

Well, hibernate used to work for me with dapper so none of the above applies to my case :-)

---

### Post by dave_abrahams on 2006-12-27
> **buttari said:**
> Well, hibernate used to work for me with dapper so none of the above applies to my case :-)

Guess what?  Me too (but only after some hacking around with conifiguration that I never would have had to do on 'doze)!  But then it stopped working, so somehow I feel it still applies to me.

---

