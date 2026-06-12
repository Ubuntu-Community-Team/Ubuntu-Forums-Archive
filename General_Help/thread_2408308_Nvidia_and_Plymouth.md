---
title: "Nvidia and Plymouth"
date: 2018-12-17
forum: General Help
---

### Post by CatKiller on 2018-12-17
I've got the framebuffer to be at my monitor's native resolution by disabling the CSM in the UEFI and using nvidia-drm.modeset=1 in GRUB. Yay!

I haven't been able to get the Plymouth splash screen to show, though. I don't know if that's because it just doesn't work, since Nvidia like to do their own thing, or because of the (non-configurable in Ubuntu, as I understand it) 5 second delay before the splash screen is shown.

Has anyone managed to get this to work, or does anyone have an idea of something that I could poke?

The graphics card is a 2080 Ti, and I'm running the 415 proprietary drivers on Kubuntu 18.04.

---

### Post by CatKiller on 2018-12-17
The framebuffer's at the monitor's native resolution, and ```
sudo plymouth show-splash
``` shows that the splash screen is installed and works. It just isn't being displayed at startup or shutdown for some reason. The screen goes blank, then black, and then the monitor's just about to go into power-saving when the login screen shows up.

---

### Post by CatKiller on 2018-12-18
If I **don't** use *nvidia-drm.modeset=1*, but **do** use ```
GRUB_GFXMODE=2560x1600x32,auto
GRUB_GFXPAYLOAD_LINUX=keep
``` I get the briefest flash of the Plymouth splash screen just before the login screen comes up. Still no splash screen on shutdown. TTYs are at native resolution.

---

### Post by CatKiller on 2018-12-18
I ran *plymouth:debug*, and I think this is the relevant part.

```
[main.c:926]           plymouth_should_show_default_splash:checking if plymouth should show default splash
[main.c:954]           plymouth_should_show_default_splash:using default splash because kernel command line has option "splash"
[ply-device-manager.c:766]                 create_devices_from_terminals:checking for consoles
[ply-device-manager.c:544]                        add_consoles_from_file:opening /sys/class/tty/console/active
[ply-device-manager.c:552]                        add_consoles_from_file:reading file
[ply-device-manager.c:590]                        add_consoles_from_file:console /dev/tty1 found!
[ply-device-manager.c:378]                         watch_for_udev_events:watching for udev graphics device add and remove events
[ply-device-manager.c:282]                  create_devices_for_subsystem:creating objects for drm devices
[ply-device-manager.c:299]                  create_devices_for_subsystem:found device /sys/devices/pci0000:00/0000:00:03.1/0000:0a:00.0/drm/card0
[ply-device-manager.c:306]                  create_devices_for_subsystem:device is initialized
[ply-device-manager.c:315]                  create_devices_for_subsystem:found node /dev/dri/card0
[ply-device-manager.c:229]                create_devices_for_udev_device:device subsystem is drm
[ply-device-manager.c:232]                create_devices_for_udev_device:found DRM device /dev/dri/card0
[ply-device-manager.c:679] create_devices_for_terminal_and_renderer_type:creating devices for /dev/dri/card0 (renderer type: 1) (terminal: /dev/tty1)
[ply-renderer.c:236]                      ply_renderer_open_plugin:trying to open renderer plugin /usr/lib/x86_64-linux-gnu/plymouth/renderers/drm.so
[./plugin.c:609]                                create_backend:creating renderer backend for device /dev/dri/card0
[./plugin.c:701]                                   load_driver:Opening '/dev/dri/card0'
[ply-terminal.c:603]                             ply_terminal_open:trying to open terminal '/dev/tty1'
[ply-terminal.c:396]                 ply_terminal_refresh_geometry:looking up terminal text geometry
[ply-terminal.c:410]                 ply_terminal_refresh_geometry:terminal is now 320x100 text cells
[ply-terminal.c:447]                                 get_active_vt:Remembering that initial vt is 1
[./plugin.c:1017]                                  query_device:Could not get card resources
[ply-renderer.c:250]                      ply_renderer_open_plugin:could not query rendering device for plugin /usr/lib/x86_64-linux-gnu/plymouth/renderers/drm.so
[./plugin.c:768]                                  close_device:closing device
[./plugin.c:722]                                unload_backend:unloading backend
[./plugin.c:633]                               destroy_backend:destroying renderer backend for device /dev/dri/card0
[ply-renderer.c:287]                             ply_renderer_open:could not find suitable rendering plugin
[ply-device-manager.c:686] create_devices_for_terminal_and_renderer_type:could not open renderer for /dev/dri/card0
[ply-device-manager.c:299]                  create_devices_for_subsystem:found device /sys/devices/pci0000:00/0000:00:03.1/0000:0a:00.0/drm/renderD128
[ply-device-manager.c:306]                  create_devices_for_subsystem:device is initialized
[ply-device-manager.c:319]                  create_devices_for_subsystem:device doesn't have a devices tag
[main.c:2397]                                          main:entering event loop
[ply-boot-server.c:388]             print_connection_process_identity:connection is from pid 427 (/bin/plymouth --show-splash) with parent pid 422 (/bin/sh /scripts/init-premount/plymouth)
[ply-boot-server.c:484]                ply_boot_connection_on_request:got show splash request
[main.c:896]      plymouth_should_ignore_show_splash_calls:checking if plymouth should be running
[main.c:998]                                on_show_splash:no displays available to show splash on, waiting...
```

It seems to find things OK, but then doesn't know what to do with them, so it gives up.

---

### Post by tamer.hassan on 2019-01-06
Same boat on a Asus ROG Laptop with NVidia GTX 1060 , and running Kubuntu 18.10 (with kubuntu backports)

First I added plymouth:debug to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub
```
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash plymouth:debug"[/COLOR][/FONT]
```

then I reached the same point you are at.. as the same relevant part of your log:
```
[ply-terminal.c:447]                                 get_active_vt:Remembering that initial vt is 1
[./plugin.c:1017]                                  query_device:Could not get card resources

```

I got a little further, by doing the following:

1. Create the following file with the following line:
```
[FONT=monospace][COLOR=#000000]$ cat /etc/modprobe.d/nvidia_drm.conf  [/COLOR]
options nvidia_drm modeset=1
[/FONT]
```

2. Add the following lines to /etc/initramfs-tools/modules
[FONT=monospace][COLOR=#000000]$ cat /etc/initramfs-tools/modules  [/COLOR]
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod

nvidia
nvidia_modeset
nvidia_uvm
drm_kms_helper
drm
nvidia_drm modeset=1

```[/FONT]

3. run:
```
sudo update-grub2 && sudo update-initramfs -u[FONT=monospace]
```[/FONT]

4. reboot, and note in plymouth debug log, the message is now:
```
[ply-terminal.c:447]                                 get_active_vt:Remembering that initial vt is 1
[./plugin.c:1013]                                  query_device:Could not initialize heads

```

I researched and googled but could not find any further clues regarding the "Could not initialize heads" issue.

---

### Post by CatKiller on 2019-01-07
Yeah, I gave up for now. I've got native-resolution TTYs and a blip of the splash screen at the right resolution, and everything else works.

It would be nice to have GRUB use something better than *redraw*, too.

---

### Post by tamer.hassan on 2019-01-08
the *redraw* of grub is caused by your configuration (which you showed previously):

```
[COLOR=#000000]GRUB_GFXMODE=2560x1600x32,auto
[/COLOR][COLOR=#000000]GRUB_GFXPAYLOAD_LINUX=keep[/COLOR]
```

change to:

```
[FONT=monospace][COLOR=#000000]GRUB_GFXPAYLOAD_LINUX="2560x1600"[/COLOR]
GRUB_TERMINAL_OUTPUT="console"
[/FONT]
```

As to the delay before you see the splash, there's a active discussion on plymouth about the 5-second delay and its proposed removal (updated last month):

[https://gitlab.freedesktop.org/plymouth/plymouth/issues/64](https://gitlab.freedesktop.org/plymouth/plymouth/issues/64)

---

### Post by CatKiller on 2019-01-08
As far as I've been able to tell, efifb doesn't have any scrolling option other than redraw. The older BIOS framebuffer consoles had yscroll and ywrap options, but I don't think the efifb does. I'll try your config options when I muster up some interest, though, to see.

By poking config files I did manage to get Plymouth to say that it hadn't used a delay, but it didn't change the behaviour of only getting a blip of splash screen.

I'm sure it's all simply Nvidia doing things in their own *unique* way.

---

### Post by tamer.hassan on 2019-01-08
Hmm. You never actually mentioned if you're on laptop/desktop or what, but to make sure we're on the same page, regarding "[efifb]("https://github.com/torvalds/linux/blob/master/Documentation/fb/efifb.txt")":
"efifb is only for EFI booted Intel Macs."

As far as I know, there exists two known options as far as the (U)EFI Framebuffer video support for grub is concerned.

Can be configured in **/etc/default/grub**

[FONT=monospace][COLOR=#000000]```
GRUB_VIDEO_BACKEND="efi_gop"

```

or

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]GRUB_VIDEO_BACKEND="efi_uga"[/COLOR]
[/FONT]
```[FONT=monospace]

You can find out which implementation you are using by executing "videoinfo" at the grub console.
Make sure you have installed (via APT) the "v86d" package.

BIOS mode framebuffer video backend in grub is "vbe". (In which case you'd have run "vbeinfo" instead of "videoinfo")


N.B.:

It took me less than less than 2 minutes and some guts to make the switch to rEFInd (bootmanager & bootloader) and I love it!
[/FONT]http://www.rodsbooks.com/refind/

I was especially convinced after clearing some doubts, all here:
[https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub](https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub)

Simply installed via official cosmic repo (quite recent version already): `**[FONT=courier new]sudo apt install refind[/FONT]**[FONT=courier new]`[/FONT]
Answered the 1 obvious question and it setup *everything* properly.

Even after I rebooted and went into EFI setup (just run `**[FONT=courier new]sudo systemctl reboot --firmware[/FONT]**`), I found it had properly set itself as the first EFI boot entry, before my pre-existing Ubuntu (Grub) & Win10 EFI boot entries.

Just did some minor customizations like:
1. downloaded memtest86 image, extracted from the EFI partition within the mounted image and coped to /boot/efi/EFI/tools/memtest86 where rEFInd can detect it automagically.
2. hid some of the auto-detected boot entries by editing **/boot/efi/EFI/refind/refind.conf** , example:
[FONT=monospace]
```
[COLOR=#000000]
[FONT=courier new]# My spinner storage HDD which is secondary drive in the laptop
dont_scan_volumes "DATA"[/FONT][/COLOR][FONT=courier new]

# Dont list anything in Boot/* (from windows 10) nor ubuntu/* (from grub)
dont_scan_dirs EFI/Boot,EFI/ubuntu[/FONT]
```

that way, I'm conveniently left with top row showing only Windows 10 & Ubuntu auto-detected Linux kernel(s)
and second row starting with memtest86 :)

the default auto-generated (during apt install refind) [/FONT][FONT=monospace][COLOR=#000000][FONT=courier new]**/boot/refind_linux.conf**[/FONT] worked well (it even automatically copied my custom kernel params line from [FONT=courier new]**/etc/default/grub**[/FONT] which was '[FONT=courier new]quite loglevel=0 splash[/FONT]').

---------------


[/COLOR]Still, the main topic here should be about making plymouth & nvidia proprietary drivers play KMS nice together!

I suspect the late kick-in of plymouth in your case is caused by trying the old fallback FRAMEBUFFER trick, which involves creating a file with following contents:
[/FONT][FONT=monospace][COLOR=#000000]```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

```followed by:
```
sudo update-initramfs -u

```
[/COLOR]in which case, this is a really old method that is not needed anymore because:
[/FONT][COLOR=#545454][FONT=arial]The proprietary [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**NVIDIA**[/FONT][/COLOR][COLOR=#545454][FONT=arial] driver supports [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**KMS**[/FONT][/COLOR][COLOR=#545454][FONT=arial] (since 364.12)

[/FONT][/COLOR]

---

### Post by CatKiller on 2019-01-09
> **tamer.hassan said:**
> Hmm. You never actually mentioned if you're on laptop/desktop or what, but to make sure we're on the same page, regarding "[efifb]("https://github.com/torvalds/linux/blob/master/Documentation/fb/efifb.txt")":
"efifb is only for EFI booted Intel Macs."

No, it isn't. It's the default framebuffer for EFI systems. It's likely that when EFI was introduced that description was just Macs, but that is no longer the case. Efifb supports either GOP and UGA as required.

I did create the splash conf file, which let me remove the configured delay. The one report I'd found of successfully getting a splash screen with Nvidia's KMS also used that file. Removing it has no effect. 

The machine I'm running doesn't matter, particularly, unless someone else has managed to get it to work & we can compare and contrast. But, since you asked, it's not a Mac. It's a desktop with an RTX 2080 Ti. I think I said that in the first post. It's using UEFI.

I don't think the splash screen actually gets displayed, as such, for the final blip. I think the splash screen gets copied into video memory in preparation for showing it, but it never actually gets shown. Then, when Plymouth quits, it happens to show the contents of video memory to cover its own cleanup.

---

### Post by CatKiller on 2019-01-09
I just checked, and using console for GRUB's output has the GRUB menu on the BIOS splash screen, which is neat, but also means that the TTYs are at 1024×768, which is less neat.

EDIT: getting rid of keep does give the native TTY, though, as you also suggested, so that's OK.

Still no splash screen, though.

---

### Post by tamer.hassan on 2019-01-09
1. when you said you removed **[COLOR=#000000][FONT=&amp]/etc/initramfs-tools/conf.d/splash[/FONT][/COLOR]** , did you also run **[COLOR=#000000][FONT=&amp]sudo update-initramfs -u[/FONT][/COLOR]** after that change and before rebooting?


2. While further trying to debug the problem, and even after having removed "plymouth:debug" from the kernel command line, I noticed I'm still seeing this in my dmesg, when nvidia KMS is enabled via kernel command line:

```
[FONT=monospace][COLOR=#000000][   14.423015] ------------[ cut here ]------------[/COLOR]
[   14.423018] Bad or missing usercopy whitelist? Kernel memory exposure attempt detected from SLUB object 'nvidia_stack_cache' (offset 11440, size 3)!
[   14.423026] WARNING: CPU: 0 PID: 1765 at mm/usercopy.c:81 usercopy_warn+0x81/0xa0
[   14.423026] Modules linked in: aufs overlay cmac bnep binfmt_misc nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd
_seq_midi snd_seq_midi_event intel_rapl x86_pkg_temp_thermal snd_rawmidi intel_powerclamp snd_seq arc4 coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd
_seq_device joydev pcbc snd_timer iwlmvm uvcvideo mac80211 aesni_intel aes_x86_64 videobuf2_vmalloc crypto_simd videobuf2_memops cryptd videobuf2_v4l2 glue_helper videobuf2_common snd btusb
 intel_cstate iwlwifi videodev btrtl media intel_rapl_perf btbcm btintel cfg80211 input_leds asus_nb_wmi bluetooth soundcore serio_raw asus_wmi hid_multitouch ecdh_generic intel_wmi_thunder
bolt sparse_keymap int3403_thermal processor_thermal_device
[   14.423059]  acpi_pad int340x_thermal_zone intel_soc_dts_iosf mei_me asus_wireless intel_pch_thermal int3400_thermal acpi_thermal_rel mei idma64 virt_dma mac_hid sch_fq_codel parport_pc  
ppdev lp parport ip_tables x_tables autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear
 dm_mirror dm_region_hash dm_log nvidia_uvm(POE) hid_asus usbhid hid_generic nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm
 ahci ipmi_devintf i2c_hid r8169 i2c_i801 mii libahci ipmi_msghandler intel_lpss_pci intel_lpss wmi hid video
[   14.423091] CPU: 0 PID: 1765 Comm: Xorg Tainted: P           OE     4.18.0-13-generic #14-Ubuntu
[   14.423092] Hardware name: ASUSTeK COMPUTER INC. GL702VM/GL702VM, BIOS GL702VM.306 06/29/2017
[   14.423094] RIP: 0010:usercopy_warn+0x81/0xa0
[   14.423094] Code: b0 97 41 51 4d 89 d8 48 c7 c0 69 91 af 97 49 89 f1 48 89 f9 48 0f 45 c2 48 c7 c7 d0 a5 b0 97 4c 89 d2 48 89 c6 e8 61 cb df ff <0f> 0b 48 83 c4 18 c9 c3 48 c7 c6 92 8e b
2 97 49 89 f1 49 89 f3 eb  
[   14.423117] RSP: 0018:ffffb9b943443b08 EFLAGS: 00010286
[   14.423118] RAX: 0000000000000000 RBX: ffff9a04247eacb0 RCX: 0000000000000006
[   14.423119] RDX: 0000000000000007 RSI: 0000000000000096 RDI: ffff9a04464164b0
[   14.423120] RBP: ffffb9b943443b20 R08: 0000000000000001 R09: 00000000000003be
[   14.423120] R10: 0000000000000004 R11: 0000000000000000 R12: 0000000000000003
[   14.423121] R13: 0000000000000001 R14: ffff9a04247eacb3 R15: ffff9a04247eacf8
[   14.423122] FS:  00007f3e30d48a80(0000) GS:ffff9a0446400000(0000) knlGS:0000000000000000
[   14.423123] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   14.423124] CR2: 00007f3e2d3e0110 CR3: 00000004a737c004 CR4: 00000000003606f0
[   14.423125] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   14.423126] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[   14.423126] Call Trace:
[   14.423130]  __check_heap_object+0xc2/0x110
[   14.423132]  __check_object_size+0x14c/0x178
[   14.423243]  os_memcpy_to_user+0x26/0x50 [nvidia]
[   14.423395]  _nv009384rm+0xbf/0xe0 [nvidia]
[   14.423396] WARNING: kernel stack frame pointer at 00000000e9a4c65e in Xorg:1765 has bad value 000000000bcf95c3
[/FONT][..snip..]
```

From reading: [https://devtalk.nvidia.com/default/topic/1031067/linux/-linux416-nvidia-390-48-nvidia_stack_cache-rip-0010-usercopy_warn-0x7e-0xa0/](https://devtalk.nvidia.com/default/topic/1031067/linux/-linux416-nvidia-390-48-nvidia_stack_cache-rip-0010-usercopy_warn-0x7e-0xa0/)

This seems to affect nvidia 390.xx with kernels 4.16.xx - 4.18.xx

From the same thread above, someone linked to [a proposed patch]("https://bugzilla.redhat.com/attachment.cgi?id=1425704") on [redhat bug]("https://bugzilla.redhat.com/show_bug.cgi?id=1570493") alleviating the warning & stack trace in dmesg.

Debian caught up last July and merged the said redhat patch for fixing the warn with kernels >= 4.16
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=901919](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=901919)

But apparently still affects kubuntu 18.10 with:
4.18.0-13-generic
nvidia-driver-390                         390.87-0ubuntu1

UPDATE:
I updated a pre-existing bugreport about exact same issue, with the findings above
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1802050](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1802050)

---

### Post by CatKiller on 2019-01-10
> **tamer.hassan said:**
> 1. when you said you removed /etc/initramfs-tools/conf.d/splash, did you also run sudo update-initramfs -u after that change and before rebooting?

I did. Not my first rodeo :p

> This seems to affect nvidia 390.xx with kernels 4.16.xx - 4.18.xx

My graphics card isn't supported by any driver version before 410, so I can't help you with that one.

---

### Post by tamer.hassan on 2019-01-11
As a workaround, adding **[COLOR=#000000]plymouth.ignore-udev[/COLOR]** to your kernel command line options makes plymouth avoid the udev detection of drm nvidia in the first place, and works immediately after grub, and on shutdown, in high resolution text mode.

---

### Post by CatKiller on 2019-01-11
Interesting. Thank you.

---

### Post by tamer.hassan on 2019-03-23
still on kubuntu 18.10
upgraded to kernel 5.0 and nvidia-driver-418 (and also plymouth) from kernel-ppa & graphics-drivers ppa

[http://ubuntuhandbook.org/index.php/tag/nvidia-418-ubuntu/](http://ubuntuhandbook.org/index.php/tag/nvidia-418-ubuntu/)

[http://ubuntuhandbook.org/index.php/2019/03/linux-kernel-5-0-released-how-install-ubuntu/](http://ubuntuhandbook.org/index.php/2019/03/linux-kernel-5-0-released-how-install-ubuntu/)

however still same problem with plymouth. debugging shows same difficulties

```
[FONT=monospace][COLOR=#000000][./plugin.c:600]                                create_backend:creating renderer backend for device /dev/dri/card0[/COLOR]
[./plugin.c:692]                                   load_driver:Opening '/dev/dri/card0'
[ply-terminal.c:603]                             ply_terminal_open:trying to open terminal '/dev/tty1'
[ply-terminal.c:396]                 ply_terminal_refresh_geometry:looking up terminal text geometry
[ply-terminal.c:410]                 ply_terminal_refresh_geometry:terminal is now 240x67 text cells
[ply-terminal.c:447]                                 get_active_vt:Remembering that initial vt is 1
[./plugin.c:1013]                                  query_device:Could not initialize heads
[ply-renderer.c:250]                      ply_renderer_open_plugin:could not query rendering device for plugin /usr/lib/x86_64-linux-gnu/plymouth/renderers/drm.so
[./plugin.c:759]                                  close_device:closing device
[./plugin.c:713]                                unload_backend:unloading backend
[./plugin.c:624]                               destroy_backend:destroying renderer backend for device /dev/dri/card0
[ply-renderer.c:287]                             ply_renderer_open:could not find suitable rendering plugin
[ply-device-manager.c:734] create_devices_for_terminal_and_renderer_type:could not open renderer for /dev/dri/card0
[/FONT]
```

so still need workaround for at least text mode plymouth to work, with kernel parameter: **[COLOR=#000000]plymouth.ignore-udev[/COLOR]**

---

### Post by sultan-ssh on 2019-05-18
I'm wondering , I have on external hard drive Ubuntu 18.10 installed. and plymouth is working well when i boot up on my laptop via usb , but the main OS which installed on internal hard disk is Kubuntu 19.04  but no splash plymouth at all 
also I tried everything  here and other posts but no luck :(   is there different between KDE and Gnome related with plymouth ???


G-force 9600m 
Driver nvidia-340
OS : Kubuntu 19.04 + kernel  5.0.0.16-generic


Edit May26:
it's works  with latest  system update and I don't know what was ,, so below lines are already into "/etc/[FONT=monospace][COLOR=#000000]/initramfs-tools/modules" since before 

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]drm[/COLOR]
drm_kms_helper
nvidia modeset=1
[/FONT]
```


and "[FONT=monospace][COLOR=#000000]/etc/default/grub[/COLOR][/FONT]" has  changed on only  this


```
[FONT=monospace][COLOR=#000000]GRUB_GFXMODE="1280x720x32"[/COLOR]

[/FONT]
``` 



 thanks

---

### Post by tamer.hassan on 2019-05-24
> **sultan-ssh said:**
> I'm wondering , I have on external hard drive Ubuntu 18.10 installed. and plymouth is working well when i boot up on my laptop via usb , but the main OS which installed on internal hard disk is Kubuntu 19.04  but no splash plymouth at all 
also I tried everything  here and other posts but no luck :(   is there different between KDE and Gnome related with plymouth ???


G-force 9600m 
Driver nvidia-340
OS : Kubuntu 19.04 + kernel  5.0.0.16-generic



thanks

If the external (HDD) 18.10 is vanilla install or live iso, plymouth works out of the box.
And I assume the internal 19.04, you installed the nvidia driver, hence the loss of the plymouth boot splash. As the title of the post says, it only happens when the proprietary nvidia driver is installed.

---

### Post by sultan-ssh on 2019-05-25
> **tamer.hassan said:**
> If the external (HDD) 18.10 is vanilla install or live iso, plymouth works out of the box.
And I assume the internal 19.04, you installed the nvidia driver, hence the loss of the plymouth boot splash. As the title of the post says, it only happens when the proprietary nvidia driver is installed.


thanks dear, please see my edit   :)

---

### Post by faubuntu on 2019-07-18
> **CatKiller said:**
> 

I haven't been able to get the Plymouth splash screen to show, though. I don't know if that's because it just doesn't work, since Nvidia like to do their own thing, or because of the (non-configurable in Ubuntu, as I understand it) 5 second delay before the splash screen is shown.

Has anyone managed to get this to work, or does anyone have an idea of something that I could poke?



I have a similar issue with Plymouth, which I am documenting [here]("http://ubuntuforums.org/showthread.php?t=2422741"). I don't have a NVIDIA card, though.[URL="https://ubuntuforums.org/showthread.php?t=2422741"]
[/URL]

---

### Post by awl29 on 2020-01-10
When trying to run plymouth (0.9.3-1ubuntu7.18.04.2) with nvidia (435.21-0ubuntu0.18.04.02) on a current Ubuntu Mate 18.04.3, I still get the message

[FONT=Courier New][./plugin.c:1022]                                  query_device:Could not initialize heads[/FONT]

as described above, and no plymouth splash screen at all. :(

Any news regarding this issue in the meantime?

Many thanks & best regards
awl29

---

