---
title: "[Ubuntu 15.10] Slow Boot, Shutdown, Log Out, e.t.c on an SSD"
date: 2016-05-19
forum: General Help
---

### Post by Friendly_Hoovy on 2016-05-19
So, I have an issue. Ubuntu 15.10 seems to not like anything relating to starting or stopping a session. Everything works fine and proper once booted/restarted/logged in, but the boot time is really obnoxious. When I was using Windows 7, for example, on the exact same hardware, I would boot in about 5-10, seconds, and maybe 5 for shutdown. You can see why this bothers me.

Output of systemd-analyze
Startup finished in 1.634s (kernel) + 3min 575ms (userspace) = 3min 2.209s

```
Output of systemd-analyze blame (only the particularly long parts)
25.728s systemd-timesyncd.service
          4.991s NetworkManager-wait-online.service
           519ms [EMAIL="tor@default.servic"]tor@default.servic[/EMAIL]e
           346ms gpu-manager.service
           295ms dev-sdb5.device
           259ms mnt-Storage.mount
           176ms systemd-localed.service
           170ms [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
           163ms systemd-fsck@dev-disk-by\x2duuid-bf01ce45\x2d1960\x2d4093\x2db7
           134ms systemd-tmpfiles-setup.service
           130ms systemd-hostnamed.service
           126ms apparmor.service
           113ms [EMAIL="systemd-rfkill@rfkill0.servic"]systemd-rfkill@rfkill0.servic[/EMAIL]e
           110ms systemd-random-seed.service
```

And a dmesg line which I think may be the culprit.
```
[    3.483029] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input18
[    3.483138] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input19
[    3.483227] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input20
[    3.483290] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input21
[   28.071823] NMI watchdog: BUG: soft lockup - CPU#0 stuck for 23s! [nvidia-smi:504]
```

as well as
```
[   28.071915] Call Trace:
[   28.071974]  [<ffffffffc067d6a0>] _nv018866rm+0x8570/0xbd60 [nvidia]
[   28.072031]  [<ffffffffc06743d5>] ? _nv000903rm+0x85/0xb0 [nvidia]
[   28.072088]  [<ffffffffc06741b4>] ? _nv014190rm+0x164/0x220 [nvidia]
[   28.072146]  [<ffffffffc065dd0d>] ? _nv014771rm+0x4d/0x140 [nvidia]
[   28.072204]  [<ffffffffc0661ef8>] ? _nv000799rm+0x278/0x380 [nvidia]
[   28.072261]  [<ffffffffc0662220>] ? _nv000717rm+0x220/0x3b0 [nvidia]
[   28.072318]  [<ffffffffc066fc8a>] ? _nv000734rm+0x2ba/0x340 [nvidia]
[   28.072375]  [<ffffffffc0663e5a>] ? rm_disable_adapter+0x6a/0x130 [nvidia]
[   28.072385]  [<ffffffffc1e08100>] ? uvm_get_mode+0x60/0x80 [nvidia_uvm]
[   28.072416]  [<ffffffffc014420e>] ? nv_uvm_notify_stop_device+0x5e/0x80 [nvidia]
[   28.072444]  [<ffffffffc01357a5>] ? nv_close_device+0x105/0x150 [nvidia]
[   28.072474]  [<ffffffffc01379a4>] ? nvidia_close+0xd4/0x2c0 [nvidia]
[   28.072503]  [<ffffffffc01353ac>] ? nvidia_frontend_close+0x2c/0x50 [nvidia]
[   28.072505]  [<ffffffff81202064>] ? __fput+0xe4/0x220
[   28.072506]  [<ffffffff812021ee>] ? ____fput+0xe/0x10
[   28.072507]  [<ffffffff8109a653>] ? task_work_run+0x73/0x90
[   28.072510]  [<ffffffff81015f09>] ? do_notify_resume+0x69/0x70
[   28.072512]  [<ffffffff817f9084>] ? int_signal+0x12/0x17
[   28.072519] Code: 00 00 55 89 f0 89 fa 48 89 e5 66 ef 5d c3 0f 1f 44 00 00 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 44 00 00 55 89 f0 89 fa 48 89 e5 ef <5d> c3 0f 1f 44 00 00 55 89 fa 48 89 e5 ec 5d c3 66 90 0f 1f 44 
[   91.958747] cgroup: new mount options do not match the existing superblock, will be ignored
[   92.073075] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   92.117834] r8169 0000:03:00.0 enp3s0: link down
[   92.117856] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   92.119318] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   92.125850] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   92.203347] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   92.806545] nvidia-modeset: Allocated GPU:0 (GPU-f526b610-c868-2104-564b-1097d88803d7) @ PCI:0000:01:00.0
```

Sorry if this wasn't formatted or done properly, as I've never used a help forum before. I think I at least got the post in the right section part down. Thanks for any help you could provide.

[B]UPDATE:
[/B]After updating to the NVIDIA 364.19 driver, I have some new outputs.

```
systemd-analyze blame:
         25.872s apparmor.service
         25.816s systemd-tmpfiles-setup.service
         25.749s [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
         25.749s [EMAIL="systemd-rfkill@rfkill0.servic"]systemd-rfkill@rfkill0.servic[/EMAIL]e
          4.970s NetworkManager-wait-online.service
           515ms [EMAIL="tor@default.servic"]tor@default.servic[/EMAIL]e
           348ms dev-sdb5.device
           259ms gpu-manager.service
           198ms systemd-localed.service
           194ms accounts-daemon.service
           176ms mnt-Storage.mount
           138ms systemd-fsck@dev-disk-by\x2duuid-c6b0be85\x2de78f\x2d465e\x2d82
           130ms NetworkManager.service
           128ms ufw.service
           126ms ModemManager.service
           106ms systemd-hostnamed.service
            88ms systemd-fsck@dev-disk-by\x2duuid-bf01ce45\x2d1960\x2d4093\x2db7
```
And an attachment of dmesg:[ATTACH]269169[/ATTACH]

---

### Post by oldfred on 2016-05-19
You can bump every twelve hours, to try to catch users in different time zones. Before it was every 24 hrs.

What hardware, cpu, which nVidia, RAM etc.

top entries with my SSD:
```
fred@Z170N:~$ systemd-analyze blame
          6.387s NetworkManager-wait-online.service
          1.760s apt-daily.service
           336ms dev-sda2.device
           244ms systemd-fsck@dev-disk-by\x2duuid-D966\x2d440A.service
           236ms ssh.service
 
```

And this is my hardware:
       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by Friendly_Hoovy on 2016-05-20
All right, I used the same program you used to get a read of my specs. Here's the output:

```
System:    Host: ubuntudomain Kernel: 4.2.0-36-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity 7.3.3 (Gtk 3.16.7-0ubuntu3)
           Distro: Ubuntu 15.10 wily

Machine:   Mobo: Gigabyte model: H81M-S2H GSM v: x.x
           Bios: American Megatrends v: F1 date: 05/20/2015

CPU:       Quad core Intel Core i5-4590 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26340
           clock speeds: max: 3700 MHz 1: 3577 MHz 2: 3599 MHz 3: 3666 MHz
           4: 3677 MHz

Graphics:  Card-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA GM204 [GeForce GTX 970] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nvidia,intel (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 970/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 364.19 Direct Rendering: Yes

Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GM204 High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-3 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.2.0-36-generic

Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
```


It doesn't seem to list RAM, but I have 2 8GB sticks at 1600 MHZ. And as I mentioned earlier, the 364.19 driver, but it has been acting up (just boot ofc) ever since I first installed Ubuntu about a month ago.

---

### Post by oldfred on 2016-05-20
These two are both network related.
> 25.728s systemd-timesyncd.service
          4.991s NetworkManager-wait-online.service


Do you have slow network, or changed from hard wired Ethernet to Wi-fi?
I do not know network or network driver issues as my systems have all works. But have seen a lot of threads on some models of Network cards like your Realtec.
If that is issue, better to post new thread with Network issues in title, model of card and more details on that.
They typically want a wireless script run, but I do not know how to interpret it. 

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Wireless script if wired working :
wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script

---

### Post by Friendly_Hoovy on 2016-05-20
> **oldfred said:**
> 
Do you have slow network, or changed from hard wired Ethernet to Wi-fi?


No, I have used purely Wi-Fi on this rig, back when I used Windows 7 as well as now with Ubuntu. I have a 50 MB/s speed, and a practical DL speed of 2.5 MB/s. Pardon if I got how the MB, Mb thing works. What about the other 25/s outputs in the update?

Another tidbit, when I fully removed my Windows partition (The Storage device for it as well as the OS itself) my boot time jumped from 40/s to the 3 Min 20/s deal we have now, if that's useful? I have moved the /boot partition, but it has literally always been slow, even before that, so I doubt that caused something. Sorry if I am not as useful as I could be.

---

### Post by oldfred on 2016-05-20
I do not use a separate /boot, and most desktop installs do not need one.

Where you mounting NTFS in fstab?

Since Gigabyte have you looked at IOMMU setting in UEFI?
I have seen that a lot on AMD versions, do not know if Intel versions have same issues.
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html) 



I know systems often have issues with ACPI. Sometimes boot parameters help.
 acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by Friendly_Hoovy on 2016-05-20
So, I don't have any NTFS filesystems since I turned them into unallocated space and fed them into my Linux partitions, making myself Windows free. I tried the first link, which resulted in zero effect, and for the second link, I don't seem to have /etc/grub.conf nor a /boot/grub/menu.lst. I did have one thing related to grub, but not like that, and not very useful. Of course, this may be me being oblivious.

As for the ACPI boot parameters, they didn't seem to have an effect, and I did indeed remember to do a sudo update-grub before rebooting. I did notice something interesting, however. The POST sound my mobo makes when booting, played while I was booting, about halfway through. It will also beep two times before fully shutting down/rebooting, which is interesting. This has happened since I installed Ubuntu, mind you. Not an effect of the ACPI boot params.

Another thing that I have mentioned before is just how it affects nothing while my system is running. Nada. No slowdown, no oddities, zilch. Very odd. Sorry for the wall of text and lack of quotes, didn't feel they were necessary.

[B]UPDATE:

[/B]After a rather worrisome mistake of me posting a dmesg with the MAC in it, I have a final version I can post. Can't wait to realize I made another mistake again. Anyhow, have another dmesg as a pastebin.
[http://pastebin.com/p4CwqbbX](http://pastebin.com/p4CwqbbX)

---

### Post by oldfred on 2016-05-20
That seems to be the nVidia 970 as the issue.
Have seen other threads with that model and issues, but do not know details.

If you use just the Intel video does system work ok?

---

### Post by Friendly_Hoovy on 2016-05-21
So, tried booting with Intel video, wouldn't even boot, got stuck on the "about to finally boot" part of the Ubuntu Splash Screen, then endlessly POSTed for some reason. Try GPU again, worked fine, try Intel again, same thing, this time when I logged in with the GPU, I got a message about Xorg dying. It seemingly brought itself back however, since I could log in and see things. Well, this is quite a conundrum.

[B]UPDATE:
[/B]My BIOS seems to have an identity crisis now, as the BIOS Splash goes by in a flash, and Grub now loads fullscreen and the old-school line by line loadup. Lovely.

---

### Post by oldfred on 2016-05-21
Intel sometimes needs a boot parameter to get settings correct.
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 

Some other 970 threads, but do not know details. My old 620Gt just works with open source driver. Usually not even installing nVidia as I do not need it.
      
 Asus z97-A with nVidia GTX 970 Maxwell Ubuntu  15.04
[URL="http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896"]http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896
[/URL]
 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210) 


Have you tried Ubuntu ppa for very newest drivers and other support software?

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by Friendly_Hoovy on 2016-05-21
I do have the latest 364 driver, 364.19. Not bleeding edge, but fairly new. As for performance, it's all fine, barring the Ubuntu splash screen bugging out with my card. Performance is what you would expect as well. I will try out those boot params, but not immediately, as I would like to use my system a bit without messing with it. Oh, and it took about 3 minutes as well before it got to the bit where it is supposed to boot, so I think the slow boot also affects my CPU Video.

---

### Post by Friendly_Hoovy on 2016-05-23
All right, I'm back. Sorry for the wait. I decided to look at the output of journalctl, and decided to parse the highlighted lines for something that dmesg may not be telling me. I may have something useful.

```
May 23 20:57:30 ubuntudomain systemd-udevd[335]: Process '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 1' failed with exit code 99.
May 23 20:57:30 ubuntudomain systemd-udevd[336]: Process '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 0' failed with exit code 99.
May 23 20:57:30 ubuntudomain nvidia-persistenced[574]: Failed to create directory /var/run/nvidia-persistenced: No such file or directory
May 23 20:57:30 ubuntudomain nvidia-persistenced[574]: Failed to change ownership of /var/run/nvidia-persistenced: No such file or directory
May 23 20:57:30 ubuntudomain nvidia-persistenced[574]: Shutdown (574)


```

And then:

```
May 23 20:57:31 ubuntudomain kernel: NVRM: Your system is not currently configured to drive a VGA console
May 23 20:57:31 ubuntudomain kernel: NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
May 23 20:57:31 ubuntudomain kernel: NVRM: requires the use of a text-mode VGA console. Use of other console
May 23 20:57:31 ubuntudomain kernel: NVRM: drivers including, but not limited to, vesafb, may result in
May 23 20:57:31 ubuntudomain kernel: NVRM: corruption and stability problems, and is not supported.
May 23 20:57:31 ubuntudomain networking[713]: ...done.
May 23 20:57:31 ubuntudomain systemd[1]: Started LSB: Raise network interfaces..
May 23 20:57:31 ubuntudomain ureadahead[610]: ureadahead:/etc/default/.grub.swp: No such file or directory
May 23 20:57:31 ubuntudomain ureadahead[610]: ureadahead:/usr/share/applications/vim.desktop: No such file or directory
May 23 20:57:31 ubuntudomain ureadahead[610]: ureadahead:/etc/init.d/hddtemp: No such file or directory
May 23 20:57:31 ubuntudomain ureadahead[610]: ureadahead:/etc/default/hddtemp: No such file or directory
May 23 20:57:57 ubuntudomain kernel: NMI watchdog: BUG: soft lockup - CPU#0 stuck for 23s! [migration/0:11]
May 23 20:57:57 ubuntudomain kernel: NMI watchdog: BUG: soft lockup - CPU#1 stuck for 23s! [migration/1:14]


```

And once more with feeling:

```
May 23 20:57:57 ubuntudomain kernel: NMI watchdog: BUG: soft lockup - CPU#2 stuck for 23s! [nvidia-smi:543]
May 23 20:57:57 ubuntudomain kernel: Modules linked in: nvidia_uvm(POE) arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw
May 23 20:57:57 ubuntudomain kernel:  ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack parport_pc iptable_filter ppdev ip_tables lp x_tables parport
May 23 20:57:57 ubuntudomain kernel: CPU: 2 PID: 543 Comm: nvidia-smi Tainted: P           OEL  4.2.0-36-generic #42-Ubuntu


```

And it just keeps coming:

```
May 23 20:57:57 ubuntudomain kernel: NMI watchdog: BUG: soft lockup - CPU#3 stuck for 23s! [migration/3:28]
May 23 20:57:57 ubuntudomain kernel: Modules linked in: nvidia_uvm(POE) arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw
May 23 20:57:57 ubuntudomain kernel:  ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack parport_pc iptable_filter ppdev ip_tables lp x_tables parport
May 23 20:57:57 ubuntudomain kernel: CPU: 3 PID: 28 Comm: migration/3 Tainted: P           OEL  4.2.0-36-generic #42-Ubuntu


```

Now even swap is joining in:

```
May 23 20:59:00 ubuntudomain systemd[1]: dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device: Job dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device/start t
May 23 20:59:00 ubuntudomain systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device.
May 23 20:59:00 ubuntudomain systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
May 23 20:59:00 ubuntudomain systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
May 23 20:59:00 ubuntudomain systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
May 23 20:59:00 ubuntudomain systemd[1]: Dependency failed for Swap.


```

Tiny bit about network:

```
May 23 20:59:00 ubuntudomain NetworkManager[824]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed


```

More network:

```
May 23 20:59:00 ubuntudomain wpa_supplicant[919]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
May 23 20:59:00 ubuntudomain wpa_supplicant[919]: dbus: Failed to construct signal
May 23 20:59:00 ubuntudomain NetworkManager[824]: <info>  (wlp5s0): supplicant interface state: starting -> ready
May 23 20:59:00 ubuntudomain NetworkManager[824]: <info>  (wlp5s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 23 20:59:00 ubuntudomain kernel: IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
May 23 20:59:00 ubuntudomain NetworkManager[824]: <info>  Device 'wlp5s0' has no connection; scheduling activate_check in 0 seconds.


```

Pam:

```
May 23 20:59:01 ubuntudomain lightdm[969]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
May 23 20:59:01 ubuntudomain lightdm[969]: PAM adding faulty module: pam_kwallet.so
May 23 20:59:01 ubuntudomain lightdm[969]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
May 23 20:59:01 ubuntudomain lightdm[969]: PAM adding faulty module: pam_kwallet5.so


```

More Pam:

```
May 23 20:59:02 ubuntudomain lightdm[1027]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
May 23 20:59:02 ubuntudomain lightdm[1027]: PAM adding faulty module: pam_kwallet.so
May 23 20:59:02 ubuntudomain lightdm[1027]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
May 23 20:59:02 ubuntudomain lightdm[1027]: PAM adding faulty module: pam_kwallet5.so


```

Network:

```
May 23 20:59:05 ubuntudomain NetworkManager[824]: <warn>  dnsmasq not available on the bus, can't update servers.
May 23 20:59:05 ubuntudomain NetworkManager[824]: <error> [1464055145.241816] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.Netwoasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name


```

Something to do with pulseaudio (some of this may not be totally related, but at this rate, I would like to see):

```
May 23 20:59:05 ubuntudomain pulseaudio[1232]: [pulseaudio] pid.c: Daemon already running.
May 23 20:59:05 ubuntudomain org.freedesktop.Notifications[985]: ** (notify-osd:1120): WARNING **: dnd_is_idle_inhibited(): got error "No such method 'IsInhibited'"


```

More stuff:

```
May 23 20:59:27 ubuntudomain dbus[808]: [system] Failed to activate service 'org.bluez': timed out
May 23 20:59:27 ubuntudomain pulseaudio[1849]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
May 23 20:59:27 ubuntudomain pulseaudio[1101]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
May 23 20:59:30 ubuntudomain gnome-session[1698]: Error preparing AM: The name org.freedesktop.Telepathy.AccountManager was not provided by any .service files


```

This again:

```
May 23 16:00:38 ubuntudomain systemd[1]: dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device: Job dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device/start t
May 23 16:00:38 ubuntudomain systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device.
May 23 16:00:38 ubuntudomain systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
May 23 16:00:38 ubuntudomain systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
May 23 16:00:38 ubuntudomain systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
May 23 16:00:38 ubuntudomain systemd[1]: dev-mapper-cryptswap1.swap: Job dev-mapper-cryptswap1.swap/start failed with result 'dependency'.
May 23 16:00:38 ubuntudomain systemd[1]: Startup finished in 1.473s (kernel) + 3min 518ms (userspace) = 3min 1.992s.
May 23 16:00:38 ubuntudomain systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
May 23 16:00:38 ubuntudomain systemd[1]: systemd-cryptsetup@cryptswap1.service: Job systemd-cryptsetup@cryptswap1.service/start failed with result 'dependency'.


```

And again:

```
May 23 16:14:41 ubuntudomain systemd[1]: dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device: Job dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device/start t
May 23 16:14:41 ubuntudomain systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2eeab7c0\x2df56c\x2d4286\x2d8475\x2d0b1c71922767.device.
May 23 16:14:41 ubuntudomain systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
May 23 16:14:41 ubuntudomain systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
May 23 16:14:41 ubuntudomain systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
May 23 16:14:41 ubuntudomain systemd[1]: dev-mapper-cryptswap1.swap: Job dev-mapper-cryptswap1.swap/start failed with result 'dependency'.
May 23 16:14:41 ubuntudomain systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
May 23 16:14:41 ubuntudomain systemd[1]: systemd-cryptsetup@cryptswap1.service: Job systemd-cryptsetup@cryptswap1.service/start failed with result 'dependency'.


```

---

### Post by Friendly_Hoovy on 2016-05-25
Bump!

---

### Post by oldfred on 2016-05-25
Did you look at the IOMMU settings as in post #6?

---

### Post by Friendly_Hoovy on 2016-05-25
Yes, and it resulted in an endless spam of this in dmesg:

```
DMAR: DRHD: handling fault status reg 2
[   20.210640] DMAR: DMAR:[DMA Read] Request device [04:00.0] fault addr ca6d5000 
               DMAR:[fault reason 01] Present bit in root entry is clear


```

Also got this fun line which seems to have killed my USB's (as in, can't use them. Will fix that now actually):

```
xhci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -110
[   20.210700] xhci_hcd: probe of 0000:04:00.0 failed with error -110


```

I mean, I had everything turned on in BIOS, edited the kernel line, updated it and it seemed to have an effect, only filling dmesg with that and increasing my boot time by 20's? Interesting though, is that times have changed. For example:

```
[   21.740706] Adding 18501628k swap on /dev/sda7.  Priority:-1 extents:1 across:18501628k FS
[   21.814818] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   21.822090] systemd-journald[283]: Received request to flush runtime journal from PID 1
[   21.945204] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   21.956837] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   21.981099] NVRM: Your system is not currently configured to drive a VGA console
[   21.981101] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   21.981102] NVRM: requires the use of a text-mode VGA console. Use of other console
[   21.981103] NVRM: drivers including, but not limited to, vesafb, may result in
[   21.981104] NVRM: corruption and stability problems, and is not supported.
[   21.996888] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input18
[   21.996973] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input19
[   21.997007] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input20
[   21.997037] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input21
[   22.064852] audit: type=1400 audit(1464242164.310:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=697 comm="apparmor_parser"
[   22.064866] audit: type=1400 audit(1464242164.310:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=697 comm="apparmor_parser"
[   22.066800] audit: type=1400 audit(1464242164.310:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=697 comm="apparmor_parser"
[   22.066802] audit: type=1400 audit(1464242164.310:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=697 comm="apparmor_parser"
[   22.066815] audit: type=1400 audit(1464242164.310:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=697 comm="apparmor_parser"
[   22.066817] audit: type=1400 audit(1464242164.310:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=697 comm="apparmor_parser"
[   22.067920] audit: type=1400 audit(1464242164.310:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=697 comm="apparmor_parser"
[   22.079065] audit: type=1400 audit(1464242164.322:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=697 comm="apparmor_parser"
[   22.079068] audit: type=1400 audit(1464242164.322:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=697 comm="apparmor_parser"
[   22.079080] audit: type=1400 audit(1464242164.322:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=697 comm="apparmor_parser"
[  111.252442] cgroup: new mount options do not match the existing superblock, will be ignored


```

The jump from reasonable to long intrigues me? Could this be from how my partitions are set up?

[B]EDIT:
[/B]One thing I forgot to mention is that reboots (the actual shutdown part), shutdowns, and loging out is now a normal speed. It seems to have just... fixed itself after an update, I think. Do you think upgrading to 16.04 with a fresh partition table could work? Or at least just a refresh partition setup now that I have more experience with them?

---

### Post by oldfred on 2016-05-25
I always have two / (root) partitions, one with my current version which now was 14.04 and another now 16.04. And on another drive I have another / or two just to experiment or try the latest version to see differences.

I would  just create a new 25GB / partition and install 16.04 and see if it works any better. I would expect it to be better, but various hardware can have regressions.

---

### Post by finny388 on 2016-09-19
^
What happened? I've been reading this thread with goosebumps thinking I might be reaching the solution.

I also have a GTX 970 and on Kubuntu 16.04, Mate 16.04 and Neon 16.04, every time I install the nvidia drivers the shutdown extends from less than 10 sec to over 2 min.

Friendly_Hoovy, did you ever come to a resolution?

Thanks!

---

### Post by oldfred on 2016-09-19
@finney388
Best to start your own thread. Boot issues are often unique.
Include brand/model system & video card/chip info. 
Perhaps also Summary Report from Boot-Repair.

---

### Post by finny388 on 2016-09-24
Thanks oldfred

[https://ubuntuforums.org/showthread.php?t=2338036&p=13549156#post13549156]("https://ubuntuforums.org/showthread.php?t=2338036&p=13549156#post13549156")

---

### Post by Bucky Ball on 2016-09-24
> **oldfred said:**
> @finney388
Best to start your own thread. Boot issues are often unique.
Include brand/model system & video card/chip info. 
Perhaps also Summary Report from Boot-Repair.

... and this is about 15.10, a dead, unsupported release, not 16.04. ;)

Thread now going for the long sleep to avoid future waking.

*Thread Closed.*

---

