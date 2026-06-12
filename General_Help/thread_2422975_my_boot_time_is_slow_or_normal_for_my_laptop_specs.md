---
title: "my boot time is slow or normal for my laptop specs?"
date: 2019-07-15
forum: General Help
---

### Post by s-e-b-a on 2019-07-15
I recently bought a used laptop specifically to use Ubuntu on it. I completely wiped the hard disk and installed Ubuntu 19.04 on it. I see people writing how their Ubuntu  boots up in seconds and feel like mine is taking a bit long. The laptop is a cheap one, so I don't expect fast speeds, but am wondering if this speed is normal for this laptop or if there is something that is not working as it should and could be improved.

I know the speed can be improved if I switch to an SSD or if I remove snap, splash screen, or other things, but I'm only trying to figure out if the speed is normal with current specs and a fresh Ubuntu install with the things it comes with by default. I'm looking for things such as invalid swap partitions which I see many people writing about, but when I run the commands I don't know what to look for. 

Timing by hand with a watch while booting, it takes about a minute and a half from pressing the power button till the log-in screen. About 15 seconds of that is spent typing the HDD encryption password. Then, from the log-in screen it takes an additional 30 seconds or so from the moment I enter the user password to when the desktop is visible.



Some details about the laptop:

It has a 500GB hard disk at 5400 RPM. I chose to encrypt it during installation.

Everything is updated. No additional drivers were available.

OS: Ubuntu 19.04 x86_64 
Host: 80MH Lenovo ideapad 100-14IBY 
Kernel: 5.0.0-20-generic 
Packages: 1726 (dpkg), 9 (snap) 
Shell: bash 5.0.3 
Resolution: 1366x768 
DE: GNOME 3.32.1 
WM: GNOME Shell 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel Celeron N2840 (2) @ 2.582GHz 
GPU: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display 
Memory: 1324MiB / 3823MiB 



Here are some of the usual commands I see people using when figuring out problems with boot up. What I need help with is figuring out what the outputs from these commands are telling me. If any additional information is required, I'll gladly supply it.


**systemd-analyze**
```

Startup finished in 3.230s (firmware) + 1.237s (loader) + 22.094s (kernel) + 1min 926ms (userspace) = 1min 27.488s 
graphical.target reached after 1min 519ms in userspace

```


**systemd-analyze blame**
```

32.936s plymouth-quit-wait.service
12.702s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
12.278s NetworkManager-wait-online.service
12.000s networkd-dispatcher.service
32.936s plymouth-quit-wait.service
12.702s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
12.278s NetworkManager-wait-online.service
12.000s networkd-dispatcher.service
11.779s snapd.service
10.945s udisks2.service
10.916s ModemManager.service
10.460s accounts-daemon.service
6.647s dev-loop13.device
6.618s dev-loop10.device
6.604s dev-loop12.device
6.601s dev-loop9.device
6.573s networking.service
6.449s thermald.service
6.361s dev-loop8.device
6.207s dev-loop4.device
6.126s rsyslog.service
6.122s bluetooth.service
6.087s avahi-daemon.service
6.062s systemd-logind.service
6.060s NetworkManager.service
6.019s wpa_supplicant.service
6.002s apport.service
5.985s grub-common.service
5.103s dev-loop11.device

```


**systemd-analyze critical-chain**
```

graphical.target @1min 519ms
&#9492;&#9472;multi-user.target @1min 516ms
  &#9492;&#9472;kerneloops.service @39.341s +253ms
    &#9492;&#9472;network-online.target @39.263s
      &#9492;&#9472;NetworkManager-wait-online.service @26.981s +12.278s
        &#9492;&#9472;NetworkManager.service @20.911s +6.060s
          &#9492;&#9472;dbus.service @20.449s
            &#9492;&#9472;basic.target @20.442s
              &#9492;&#9472;sockets.target @20.442s
                &#9492;&#9472;snapd.socket @20.360s +77ms
                  &#9492;&#9472;sysinit.target @20.299s
                    &#9492;&#9472;apparmor.service @17.866s +2.430s
                      &#9492;&#9472;local-fs.target @17.864s
                        &#9492;&#9472;boot-efi.mount @17.752s +111ms
                          &#9492;&#9472;boot.mount @17.684s +57ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-d11eb44d\x2d1cde\x2d428a\x2db676\x2d1439aaea0617.service @17.060s +621ms
                              &#9492;&#9472;dev-disk-by\x2duuid-d11eb44d\x2d1cde\x2d428a\x2db676\x2d1439aaea0617.device @17.010s

```



**/etc/fstab**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=d11eb44d-1cde-428a-b676-1439aaea0617 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=A405-F97B  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```


**blkid**
```

/dev/sda3: UUID="40d38d87-e3ac-4192-b189-891b60a74248" TYPE="crypto_LUKS" PARTUUID="d2b6b81d-e058-4cff-9b54-e80e1f2872c8"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="A405-F97B" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3cca21b1-1fae-441a-aeed-fed7015d74a1"
/dev/sda2: UUID="d11eb44d-1cde-428a-b676-1439aaea0617" TYPE="ext4" PARTUUID="b1fc4af0-cf69-403f-b446-0f09065b90a6"
/dev/mapper/sda3_crypt: UUID="EDxfZF-VF19-F7cC-tdmM-J1UB-isOf-vkWZsi" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="ddc8dd1e-a7d3-40cf-aa6f-3efae91dad30" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="b27dffc4-b0fb-48e5-b85d-23ec2afcb3c4" TYPE="swap"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"

```

---

### Post by uRock on 2019-07-15
Does your computer have a solid state drive or a hard disk drive?

My laptop has an HDD and here's the output of the same command,
```
uRock@Three:~$ systemd-analyze
Startup finished in 9.333s (kernel) + 51.780s (userspace) = 1min 1.114s 
graphical.target reached after 51.751s in userspace

```I am running a lighter distro, Debian 10 Gnome.

---

### Post by GhX6GZMB on 2019-07-16
I'd say it's normal. My old HP6910p takes around two minutes, of which 35 seconds are in the BIOS. Intel core 2, 2 GHz, 4 MB RAM, 120 GB HDD, Lubuntu 19.04.
If you change to an SSD you'll see completely different times.

---

### Post by kpatz on 2019-07-16
Laptop HDDs are optimized for power consumption/battery life, not speed, so slower boot times are normal.

If you want fast boot times, install a SSD.

---

### Post by oldfred on 2019-07-16
The Ubuntu standard gnome desktop is considered heavier or needs newer, faster systems to work well.
You may be better off with a lighter weight flavor.
       [URL="https://wiki.ubuntu.com/UbuntuFlavors"]https://wiki.ubuntu.com/UbuntuFlavors
      [/URL]
 Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie 
    
I use another version of gnome called gnome-panel or flashback which also is lighter and also worked on my old laptop. It was the old style top & bottom panels like Ubuntu was before Unity. My desktop monitor is 4:3 so top & bottom panels give my more space than using the icons on the side.

More info:
       [https://wiki.archlinux.org/index.php/GNOME/Flashback](https://wiki.archlinux.org/index.php/GNOME/Flashback)
The differences to the MATE project is that GNOME Flashback uses GTK+ 3 and tries to follow the current GNOME development by integrating recent changes of the GNOME libraries.
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback) 
    

[URL="https://wiki.ubuntu.com/UbuntuFlavors"]
[/URL]

---

### Post by s-e-b-a on 2019-07-17
Thanks all who replied so far :)

To be clear, I'm ok with the current speed. Just wondering if it is a normal speed.

I know that upgrading the hardware, getting an SSD, using a lighter distro, uninstalling certain apps, etc., are all things that would make things faster. I only want to know if everything is working as it should with my exact current set up or if there are problems that should be fixed ;)

I would like some help figuring out what all that information that I got from those commands mean. Mostly the ones of the swap partitions in fstab and blkid. Or if anything in there looks unusual. 

Thanks :KS

---

### Post by CatKiller on 2019-07-17
That kind of time seems pretty normal for an old, low-performance computer with a mechanical drive. You could possibly shave a bit off here and there without major changes, but it wouldn't make a massive difference.

You'd maybe take off about a minute if you got rid of snaps and switched to an SSD.

---

### Post by Autodave on 2019-07-17
Several year old HP laptop running Xubuntu 18.04.  On original spinning drive it took a little over a minute to boot. (This is a half decent machine.) Replace HD with an SSD: boot time now 21 seconds.  And that was with a $39 (US) SSD.

---

### Post by HermanAB on 2019-07-17
Why do you reboot?  Use suspend.

---

### Post by mastablasta on 2019-07-18
i need to check the analyze command, but on fresh Kubuntu install, the boot time was about 45 seconds on my 15 year old desktop (but HDD are relatively new Seagates). i remember measuring it to see how much i gained form windows XP which took about 10 minutes to boot (and load lal antivirus, firewalls etc). in any case the 1:30 is still a lot shorter than my i3 windows 10 laptop at work. it takes more than 3 minutes to boot (it's on HDD). and on win 10 sometimes it starts to scan the drive (4x). so it's slow after boot and i can't get much done.

---

### Post by Tadaen_Sylvermane on 2019-07-18
> [COLOR=#000000]Why do you reboot?

was going to say the same thing. boot times should be damn near irrelevant for a linux system. reboots are very rarely required, unlike their windows counterparts where it can occasionally be a daily thing depending on usage.[/COLOR]

---

### Post by uRock on 2019-07-18
> **Tadaen_Sylvermane said:**
> was going to say the same thing. boot times should be damn near irrelevant for a linux system. reboots are very rarely required, unlike their windows counterparts where it can occasionally be a daily thing depending on usage.[/COLOR]

I shut all of my desktop systems down at night.

---

### Post by #&amp;thj^% on 2019-07-18
> **uRock said:**
> I shut all of my desktop systems down at night.

+1 I do the same, except for 2 servers.
I will have to admit though My Arch Installs boot 1:30 faster.

---

### Post by uRock on 2019-07-18
> **1fallen said:**
> +1 I do the same, except for 2 servers.
I will have to admit though My Arch Installs boot 1:30 faster.

My Netbook running Debian 10 with LXDE on the OEM HDD boots in 38 seconds, according to systemd-analyze. That blew my mind. My desktop isn't much faster due to the full disk encryption.

---

### Post by #&amp;thj^% on 2019-07-18
> **uRock said:**
> My Netbook running Debian 10 with LXDE on the OEM HDD boots in 38 seconds, according to systemd-analyze. That blew my mind. My desktop isn't much faster due to the full disk encryption.
Nice. :)
Full encryption here also:
```
systemd-analyze
Startup finished in 18.553s (kernel) + 1min 9.684s (userspace) = 1min 28.238s 
graphical.target reached after 44.895s in userspace

```
Arch:
```
Startup finished in 5.236s (kernel + 6.860s (userspace) = 12.097s
graphical.target reached after 6.858s in userspace
```
The Arch has 3 harddrives mounted at boot. (@5 TBs)

---

### Post by Autodave on 2019-07-18
Desktops stay running all the time.  However, the laptop only gets used once or twice a month, so it gets shutdown.

---

### Post by uRock on 2019-07-19
> **1fallen said:**
> Nice. :)
Full encryption here also:
```
systemd-analyze
Startup finished in 18.553s (kernel) + 1min 9.684s (userspace) = 1min 28.238s 
graphical.target reached after 44.895s in userspace

```
Arch:
```
Startup finished in 5.236s (kernel + 6.860s (userspace) = 12.097s
graphical.target reached after 6.858s in userspace
```
The Arch has 3 harddrives mounted at boot. (@5 TBs)

Nice! I just finished getting Debian Buster up and running on my production machine. Added my two data drives to fstab, then rebooted. This machine does have the OS on an SSD.
```
systemd-analyze 
Startup finished in 4.535s (kernel) + 6.656s (userspace) = 11.192s 
graphical.target reached after 6.646s in userspace

```

---

### Post by mastablasta on 2019-07-19
```
gregor@stari:~$ systemd-analyze
Startup finished in 5.493s (kernel) + 32.642s (userspace) = 38.135s
graphical.target reached after 32.616s in userspace
```


here we go. Kubuntu on a machine built in 2004 and only slightly upgraded. single core CPU, spinning HDD (nothing fancy like black series or anything...), added 2 Gb ram to have 4. replaced GPU but it+s speed is nearly the same as on original one (only more ram).

on windows XP (same HDD, same setup - dualboot) it takes about 10 minutes.

---

### Post by uRock on 2019-07-19
> **mastablasta said:**
> ```
gregor@stari:~$ systemd-analyze
Startup finished in 5.493s (kernel) + 32.642s (userspace) = 38.135s
graphical.target reached after 32.616s in userspace
```


here we go. Kubuntu on a machine built in 2004 and only slightly upgraded. single core CPU, spinning HDD (nothing fancy like black series or anything...), added 2 Gb ram to have 4. replaced GPU but it+s speed is nearly the same as on original one (only more ram).

on windows XP (same HDD, same setup - dualboot) it takes about 10 minutes.

That's not bad at all for regular HDD. There's nothing special about my desktop. An old Dell XPS with quad core. It has the cheap GPU that came with it. My Netbook still amazes me with how fast it booted running LXDE Debian 10. It was like your's when it ran Windows. Turn it on, then go grab a cup of coffee, then come back and finish waiting for a login screen.

You can tell I didn't learn about this systemd-analyze command until this thread.

---

### Post by s-e-b-a on 2019-07-20
I shut down the laptop at night or if I am moving from one place to another and need to carry it in a backpack. Is it ok to be moving the laptop around in a backpack when it's on suspend?

There's actually no suspend button to select when clicking the power icon in the task bar on top right. Can it only be done by setting the physical power button to suspend when clicked?

---

### Post by uRock on 2019-07-21
> **s-e-b-a said:**
> .....Can it only be done by setting the physical power button to suspend when clicked?

That, closing the laptop, and clicking on the launcher menu and typing suspend will bring it up.

---

### Post by Tadaen_Sylvermane on 2019-07-21
> [COLOR=#000000]I shut all of my desktop systems down at night.

I got out my Kill A Watt and hooked my desktop / printer / monitor / speakers into it and tracked it a few days. It will be turned off at night for the foreseeable future. This alone is 2.50-5 bucks a month on the electric bill. When the total bill i 70 bucks during winter that's a big chunk for a single computer. Server will stay on 24 / 7 though.[/COLOR]

---

### Post by uRock on 2019-07-23
> **uRock said:**
> Does your computer have a solid state drive or a hard disk drive?

My laptop has an HDD and here's the output of the same command,
```
uRock@Three:~$ systemd-analyze
Startup finished in 9.333s (kernel) + 51.780s (userspace) = 1min 1.114s 
graphical.target reached after 51.751s in userspace

```I am running a lighter distro, Debian 10 Gnome.
Update: This is from the same computer after finally getting a working SSD from Amazon. It's a $20 Kingston, so I wasn't surprised the first one I received was bad.
```
systemd-analyze 
Startup finished in 7.677s (kernel) + 9.871s (userspace) = 17.548s 
graphical.target reached after 9.838s in userspace

```
The best $20 I've ever spent, as computer parts are concerned.

---

