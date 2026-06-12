---
title: "Help! KDE is falling apart!"
date: 2008-02-13
forum: General Help
---

### Post by Zeroangel on 2008-02-13
I've been using Ubuntu/Kubuntu since Breezy and now for the first time it seems to be totally falling apart.

First Kopete wouldnt run properly, then amarok starts acting flaky, then I get random lockups, then kicker starts crashing forcing an X-Server restart to get it going again, now I cant even log into KDE because X restarts when KDE gets to at "Starting Services". Now in GNOME, KMail won't fetch my messages (can't initialize imaps or pop3s) and even emesene (my MSN messenger app) is causing my machine to lock up.

Restarting wont fix the problems, nor does apt-get update. I did several things at once before thing started going wonky and they were basically
- dpkg-reconfigure on kdelibs and kopete (in attempt to fix Kopete issues)
- ran passwd command to change user password for my main account
- apt-get upgrade as usual (it upgraded my linux-image package along with some other seemingly unimportant things)

Probably a few other things, nothing that I know of. During the time that kicker started acting up, I tried restarting it to no avail from the terminal and got a message having to do with locales and plurals before everything really went down the drain -- and even GNOME seems to be acting weird.

Can anyone give me an idea on where to start looking?

---

### Post by Zeroangel on 2008-02-13
Oh yeah, heres my last apt-get update before the locale/plural error
> Log started: 2008-02-13  09:25:16
(Reading database ... 326155 files and directories currently installed.)
Preparing to replace language-pack-en 1:7.10+20071120 (using .../language-pack-en_1%3a7.10+20080205_all.deb) ...
Unpacking replacement language-pack-en ...
Preparing to replace language-pack-en-base 1:7.10+20071012 (using .../language-pack-en-base_1%3a7.10+20080205_all.deb) ...
Unpacking replacement language-pack-en-base ...
Preparing to replace language-pack-kde-en 1:7.10+20071120 (using .../language-pack-kde-en_1%3a7.10+20080205_all.deb) ...
Unpacking replacement language-pack-kde-en ...
Preparing to replace language-pack-kde-en-base 1:7.10+20071012 (using .../language-pack-kde-en-base_1%3a7.10+20080205_all.deb) ...
Unpacking replacement language-pack-kde-en-base ...
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.51 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace clamav-base 0.91.2-3ubuntu2.2 (using .../clamav-base_0.91.2-3ubuntu2.3_all.deb) ...
Unpacking replacement clamav-base ...
Preparing to replace inkscape 0.46.0-svn+17178 (using .../inkscape_0.46.0-svn+17330_i386.deb) ...
Unpacking replacement inkscape ...
Preparing to replace libclamav2 0.91.2-3ubuntu2.2 (using .../libclamav2_0.91.2-3ubuntu2.3_i386.deb) ...
Unpacking replacement libclamav2 ...
Preparing to replace libpq5 8.2.6-0ubuntu0.7.10.1 (using .../libpq5_8.3.0-1~gutsy1_i386.deb) ...
Unpacking replacement libpq5 ...
Preparing to replace linux-headers-2.6.22-14 2.6.22-14.51 (using .../linux-headers-2.6.22-14_2.6.22-14.52_all.deb) ...
Unpacking replacement linux-headers-2.6.22-14 ...
Preparing to replace linux-headers-2.6.22-14-generic 2.6.22-14.51 (using .../linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Unpacking replacement linux-headers-2.6.22-14-generic ...
Preparing to replace linux-libc-dev 2.6.22-14.51 (using .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace linux-source-2.6.22 2.6.22-14.51 (using .../linux-source-2.6.22_2.6.22-14.52_all.deb) ...
Unpacking replacement linux-source-2.6.22 ...
Preparing to replace emesene 0.99svn1013-1 (using .../emesene_0.99svn1015-1_all.deb) ...
Unpacking replacement emesene ...
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up clamav-base (0.91.2-3ubuntu2.3) ...

Setting up inkscape (0.46.0-svn+17330) ...

Setting up libclamav2 (0.91.2-3ubuntu2.3) ...

Setting up libpq5 (8.3.0-1~gutsy1) ...

Setting up linux-headers-2.6.22-14 (2.6.22-14.52) ...
Setting up linux-headers-2.6.22-14-generic (2.6.22-14.52) ...

Setting up linux-libc-dev (2.6.22-14.52) ...
Setting up linux-source-2.6.22 (2.6.22-14.52) ...
Setting up emesene (0.99svn1015-1) ...
Setting up language-pack-en (1:7.10+20080205) ...
Setting up language-pack-kde-en (1:7.10+20080205) ...
Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Reloading GNOME Display Manager configuration...* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Setting up language-pack-kde-en-base (1:7.10+20080205) ...
Reloading GNOME Display Manager configuration...* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Processing triggers for libc6 ...
ldconfig deferred processing now taking placeI was looking through some random files in /var/log and the debug file shows a bunch of entries like this
> Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.208571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fc_noserial_if1_oss_pcm_0_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.209133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_midi_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.209697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_midi_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.210263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_mixer__1'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.210851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fc_noserial_if1_oss_mixer__1'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.211510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_capture_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.212122] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_playback_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.212688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_playback_1'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.213249] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fc_noserial_if1_alsa_capture_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.213901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.214459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.215064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.215629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Feb 13 14:50:01 icarus NetworkManager: <debug> [1202935801.216188] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0').Pretty much every device in my system is there (thats just a SMALL portion of the list). The logfiles for Dmesg or Xorg shows nothing out of the ordinary though.

I did also notice that I had USB 2.0 support disabled in my BIOS so I enabled that before the problems started occurring too...

---

### Post by Zeroangel on 2008-02-14
*bump!*

---

### Post by Zeroangel on 2008-02-14
Ah, finally found it!

PROBLEM: Latest language-pack-kde-en packages break compatibility for Gutsy Canadian Users.
WORKAROUND: Downgrade packages + Remove repository "gutsy-proposed"

[http://ubuntuforums.org/showthread.php?t=695801](http://ubuntuforums.org/showthread.php?t=695801)

That oughtta suffice until the KDE *buntu devs fix the packages.

---

