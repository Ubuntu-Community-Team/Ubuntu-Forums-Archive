---
title: "Need diagnosis of this OOPS error"
date: 2015-06-02
forum: General Help
---

### Post by dora5 on 2015-06-02
My system is giving error messages when I log into my user account in Kubuntu.   After finding online where to find the error messages (thanks for the only person who responded to that question told me to stop monkeying with my system and reinstall instead of telling me where to find what error log, thanks so kindly for the help), I captured the error messages in the syslog below.   As the desktop is loading I get two to six Linux has experienced an internal error messages, and two of them gave me the following error message.  Then the system appears to run normally for a short time but then freezes and has to be turned off with the power button.   

Package linux-image-3.16.0-38-generic 3.16.0-38.52~14.04.1
ProblemType
    KernelOops
Title
   BUG: unable to handle kernel paging request at fb901000
Annotation
   Your system might become unstable now and might need to be restarted
ApportVersion
    2.14.1-Oubuntu3.11

Now, several things that I did that went a bit sideways before I started having this problem are install Oracle VirtualBox, have difficulties with GRUB and reinstall it, run a system update that may have actually updated either X11 or the video driver or both, and wasn't able to update gambas on account of I think trying to download the package from the wrong place, which has been problematic since I installed gambas, uninstalled VirtualBox because the boot log led me to suspect that was what was causing my system freezes.   

I also installed XScreensaver on Saturday evening.   It appeared to cause real problems.  I THINK I uninstalled it, but it somehow wasn't clear that it completely uninstalled.  The /var/crash folder contains mostly files in binary, some of them from today's crashes, and I wish I could read them.  However, two of them pertain to the installation of XScreensaver and the fact that it was causing atleast partial crashes.   If this may have generated the problems I'm having I will need to know how to fix it.  The error messages refer to obsolete packages, many having to do with mesa libraries, and suggest upgrading them to see if the problolems persist.    (XScreensaver is a popular answer to the fact that holier than thou idiots who designed Kubuntu/ KDE, knowing far better than users do how we should use our system resources, decided having a screensaver is an Environmental Crime, or something - in other words an "unecessary use of resources".   This is the ONLY screensaver solution for Kubuntu I can find anywhere - and I want a proper screensaver!)

Also, something I was doing on Saturday filled an apport log with a LOT of error messages about apport (pid 4339).  At this point, the Lord knows what was process number 4339.

Tell me if what is below looks like some kind of video driver issue (or even an audio driver issue).   I installed the nvidia drivers, reverted to the system Nouveau drivers, went back to the Nvidia drivers but for some reason it appeared to mainly use the Nouveau drivers ever since, so I'm not sure what is up with that.   I'm left with little clue what caused the crash except that both tracebacks appear to focus on the video drivers, and not a whole lot was actually running on the system at the time - except for Cairo dock, which I have noticed is acting rather weird.  There appear to be maybe multiple instances of it running at one time and there is a shadow above the dock as if a second shadow dock were running or Lord knows what.   


Failure
    oops
SourcePacakge
   linux-lts-utopic
Taggs
  kernel-oops trusty third-party-packages
Uname
  Linux 3.16.0-38-generic i686

UpgradeStatus
   No upgrade log present (probably fresh install)


Here is the relevant output from syslog - I was only able to avoid crashing by booting into another OS on the same computer with access to that hard drive and the log files.   

Jun  2 19:20:52 dora-OptiPlex-755 colord: Profile added: Samsung_M2070_Series-Gray..  
 Jun  2 19:20:52 dora-OptiPlex-755 colord: Device added: cups-Samsung_M2070_Series  
 Jun  2 19:21:02 dora-OptiPlex-755 dbus[653]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)  
 Jun  2 19:21:03 dora-OptiPlex-755 udisksd[2157]: udisks daemon version 2.1.3 starting  
 Jun  2 19:21:03 dora-OptiPlex-755 dbus[653]: [system] Successfully activated service 'org.freedesktop.UDisks2'  
 Jun  2 19:21:03 dora-OptiPlex-755 udisksd[2157]: Acquired the name org.freedesktop.UDisks2 on the system message bus  
 Jun  2 19:21:07 dora-OptiPlex-755 dhclient: XMT: Info-Request on eth0, interval 33100ms.  
 Jun  2 19:21:09 dora-OptiPlex-755 colord: Profile added: icc-91c9c5ca7627e1f02a03ff63f4ccda32  
 Jun  2 19:21:10 dora-OptiPlex-755 colord: Device added: xrandr-Dell Inc.-Dell E193FP-G656656PL5K3  
 Jun  2 19:21:10 dora-OptiPlex-755 dbus[653]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)  
 Jun  2 19:21:10 dora-OptiPlex-755 org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.  
 Jun  2 19:21:10 dora-OptiPlex-755 dbus[653]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'  
 Jun  2 19:21:10 dora-OptiPlex-755 dbus[653]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)  
 Jun  2 19:21:10 dora-OptiPlex-755 dbus[653]: [system] Successfully activated service 'org.freedesktop.systemd1'  
 Jun  2 19:21:19 dora-OptiPlex-755 kernel: [   82.816908] audit: type=1400 audit(1433290879.920:76): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/home/dora/.config/dconf/user" pid=2294 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0  
 Jun  2 19:21:20 dora-OptiPlex-755 NetworkManager[908]: <warn> (eth0): DHCPv6 request timed out.  
 Jun  2 19:21:20 dora-OptiPlex-755 NetworkManager[908]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1387  
 Jun  2 19:21:20 dora-OptiPlex-755 NetworkManager[908]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...  
 Jun  2 19:21:20 dora-OptiPlex-755 NetworkManager[908]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...  
 Jun  2 19:21:20 dora-OptiPlex-755 NetworkManager[908]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.  
 Jun  2 19:21:23 dora-OptiPlex-755 dbus[653]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)  
 Jun  2 19:21:23 dora-OptiPlex-755 dbus[653]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully called chroot.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully dropped privileges.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully limited resources.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Running.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Canary thread running.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Watchdog thread running.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2324 of process 2324 (n/a) owned by '1000' high priority at nice level -11.  
 Jun  2 19:21:23 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 1 threads of 1 processes of 1 users.  
 Jun  2 19:21:29 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2381 of process 2324 (n/a) owned by '1000' RT at priority 5.  
 Jun  2 19:21:29 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 2 threads of 1 processes of 1 users.  
 Jun  2 19:21:30 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2390 of process 2324 (n/a) owned by '1000' RT at priority 5.  
 Jun  2 19:21:30 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 3 threads of 1 processes of 1 users.  
 Jun  2 19:21:31 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2392 of process 2324 (n/a) owned by '1000' RT at priority 5.  
 Jun  2 19:21:31 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 4 threads of 1 processes of 1 users.  
 Jun  2 19:21:31 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2393 of process 2324 (n/a) owned by '1000' RT at priority 5.  
 Jun  2 19:21:31 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 5 threads of 1 processes of 1 users.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2395 of process 2395 (n/a) owned by '1000' high priority at nice level -11.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 6 threads of 2 processes of 1 users.  
 Jun  2 19:21:32 dora-OptiPlex-755 pulseaudio[2395]: [pulseaudio] pid.c: Daemon already running.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2397 of process 2397 (n/a) owned by '1000' high priority at nice level -11.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 6 threads of 2 processes of 1 users.  
 Jun  2 19:21:32 dora-OptiPlex-755 pulseaudio[2397]: [pulseaudio] pid.c: Daemon already running.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2399 of process 2399 (n/a) owned by '1000' high priority at nice level -11.  
 Jun  2 19:21:32 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 6 threads of 2 processes of 1 users.  
 Jun  2 19:21:32 dora-OptiPlex-755 pulseaudio[2399]: [pulseaudio] pid.c: Daemon already running.  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217366] BUG: unable to handle kernel paging request at fb900000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217382] IP: [<c1326450>] iowrite32+0x30/0x40  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217394] *pdpt = 0000000001af7001 *pde = 00000000360f3067 *pte = 0000000000000000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217403] Oops: 0002 [#1] SMP  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217408] Modules linked in: snd_hrtimer rfcomm bnep bluetooth 6lowpan_iphc binfmt_misc snd_usb_audio snd_usbmidi_lib pwc videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev snd_hda_codec_analog media snd_hda_codec_hdmi snd_hda_codec_generic coretemp kvm snd_hda_intel snd_seq_midi snd_hda_controller snd_seq_midi_event snd_hda_codec dcdbas snd_hwdep snd_rawmidi snd_pcm snd_seq serio_raw snd_seq_device eeprom snd_timer i2c_i801 snd lpc_ich soundcore shpchp mei_me mei ppdev parport_pc lp mac_hid parport hid_generic usbhid hid nouveau mxm_wmi wmi video i2c_algo_bit ttm e1000e psmouse drm_kms_helper ptp drm pps_core pata_acpi  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217509] CPU: 1 PID: 2422 Comm: cairo-dock Not tainted 3.16.0-38-generic #52~14.04.1-Ubuntu  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217515] Hardware name: Dell Inc. OptiPlex 755                 /0GM819, BIOS A10 04/30/2008  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217522] task: f0eeab50 ti: f0266000 task.ti: f0266000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217527] EIP: 0060:[<c1326450>] EFLAGS: 00210292 CPU: 1  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217532] EIP is at iowrite32+0x30/0x40  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217536] EAX: 00000000 EBX: e7ea78c0 ECX: fb900000 EDX: fb900000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217541] ESI: f86511a0 EDI: f86511c0 EBP: f0267c58 ESP: f0267c54  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217546]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217551] CR0: 80050033 CR2: fb900000 CR3: 30792000 CR4: 000007f0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217556] Stack:  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217559]  f858adb3 f0267c74 f8587f37 00000000 f86511c0 e7cbff60 0000f004 f86510c0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217571]  f0267cb0 f85881db 00000000 00000044 f0267cd4 3ded4000 00000000 f2744a80  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217583]  f0267ca0 f86510a8 f2744300 00000000 00000000 00010000 f2744300 f0267ce0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217595] Call Trace:  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217629]  [<f858adb3>] ? nouveau_barobj_wr32+0x13/0x20 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217650]  [<f8587f37>] _nouveau_gpuobj_wr32+0x37/0x40 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217670]  [<f85881db>] nouveau_gpuobj_create_+0x1bb/0x280 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217690]  [<f85882e6>] _nouveau_gpuobj_ctor+0x46/0x60 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217711]  [<f85897e4>] nouveau_object_ctor+0x34/0xe0 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217731]  [<f8588e12>] ? region_head.isra.1.part.2+0x22/0x70 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217750]  [<f8588358>] nouveau_gpuobj_new+0x58/0x60 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217777]  [<f85c50a9>] nouveau_vm_get+0x189/0x250 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217785]  [<c117935a>] ? kmem_cache_alloc_trace+0x17a/0x190  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217819]  [<f8608176>] nouveau_bo_vma_add+0x36/0x90 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217850]  [<f8608844>] nouveau_gem_object_open+0xe4/0x110 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217869]  [<f8358108>] drm_gem_handle_create_tail+0xb8/0x160 [drm]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217883]  [<f83581d9>] drm_gem_handle_create+0x29/0x30 [drm]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217915]  [<f8608b92>] nouveau_gem_ioctl_new+0xb2/0x1b0 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217946]  [<f8608ae0>] ? nouveau_gem_new+0x110/0x110 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217959]  [<f83564ef>] drm_ioctl+0x1cf/0x530 [drm]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217990]  [<f8608ae0>] ? nouveau_gem_new+0x110/0x110 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.217999]  [<c115dbd0>] ? __vma_link_file+0x40/0x70  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218007]  [<c1439441>] ? __pm_runtime_resume+0x51/0x70  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218037]  [<f8601071>] nouveau_drm_ioctl+0x51/0x80 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218067]  [<f8601020>] ? nouveau_pmops_thaw+0x20/0x20 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218075]  [<c119f852>] do_vfs_ioctl+0x2f2/0x4f0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218080]  [<c1160bec>] ? do_mmap_pgoff+0x29c/0x350  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218086]  [<c114c16b>] ? vm_mmap_pgoff+0x7b/0xa0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218091]  [<c119fab0>] SyS_ioctl+0x60/0x90  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218104]  [<c169515f>] sysenter_do_call+0x12/0x12 
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218108] Code: 00 89 d1 77 26 81 fa 00 00 01 00 76 06 0f b7 d2 ef c3 90 55 ba 85 d9 8b c1 89 e5 89 c8 e8 49 fe ff ff 5d c3 8d b4 26 00 00 00 00 <89> 02 c3 8d b6 00 00 00 00 8d bc 27 00 00 00 00 3d ff ff 03 00  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218176] EIP: [<c1326450>] iowrite32+0x30/0x40 SS:ESP 0068:f0267c54  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.218185] CR2: 00000000fb900000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.220003] ---[ end trace 17f328ac40bfd38e ]---  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.224680] BUG: unable to handle kernel paging request at fb901000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.224695] IP: [<c1326450>] iowrite32+0x30/0x40  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.224704] *pdpt = 0000000001af7001 *pde = 00000000360f3067 *pte = 0000000000000000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.224712] Oops: 0002 [#2] SMP  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.225182] Modules linked in: snd_hrtimer rfcomm bnep bluetooth 6lowpan_iphc binfmt_misc snd_usb_audio snd_usbmidi_lib pwc videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev snd_hda_codec_analog media snd_hda_codec_hdmi snd_hda_codec_generic coretemp kvm snd_hda_intel snd_seq_midi snd_hda_controller snd_seq_midi_event snd_hda_codec dcdbas snd_hwdep snd_rawmidi snd_pcm snd_seq serio_raw snd_seq_device eeprom snd_timer i2c_i801 snd lpc_ich soundcore shpchp mei_me mei ppdev parport_pc lp mac_hid parport hid_generic usbhid hid nouveau mxm_wmi wmi video i2c_algo_bit ttm e1000e psmouse drm_kms_helper ptp drm pps_core pata_acpi  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] CPU: 1 PID: 2423 Comm: cairo-dock Tainted: G      D       3.16.0-38-generic #52~14.04.1-Ubuntu  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] Hardware name: Dell Inc. OptiPlex 755                 /0GM819, BIOS A10 04/30/2008  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] task: f0460c60 ti: f0272000 task.ti: f0272000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] EIP: 0060:[<c1326450>] EFLAGS: 00210292 CPU: 1  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] EIP is at iowrite32+0x30/0x40  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] EAX: 00000000 EBX: e7ea7b40 ECX: fb901000 EDX: fb901000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.228002] ESI: f86511a0 EDI: f86511c0 EBP: f0273bf8 ESP: f0273bf4  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] CR0: 80050033 CR2: fb901000 CR3: 30808000 CR4: 000007f0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] Stack:  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  f858adb3 f0273c14 f8587f37 00000000 f86511c0 e7ea9000 00000000 f865eb20  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  f0273c30 f8587f37 00000000 f865eb20 e7ea9060 00000004 f86510c0 f0273c6c  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  f85881db 00000000 00000001 e7ea9078 3dec4000 00000000 f2744a80 f0273c5c  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] Call Trace:  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f858adb3>] ? nouveau_barobj_wr32+0x13/0x20 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8587f37>] _nouveau_gpuobj_wr32+0x37/0x40 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8587f37>] _nouveau_gpuobj_wr32+0x37/0x40 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f85881db>] nouveau_gpuobj_create_+0x1bb/0x280 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f85882e6>] _nouveau_gpuobj_ctor+0x46/0x60 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f85897e4>] nouveau_object_ctor+0x34/0xe0 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8588358>] nouveau_gpuobj_new+0x58/0x60 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f85da6e4>] nv84_fifo_context_ctor+0x84/0x140 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f85897e4>] nouveau_object_ctor+0x34/0xe0 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8589db8>] ? nouveau_object_inc+0x38/0x180 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8589fcd>] nouveau_object_new+0xcd/0x1f0 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8602a8d>] nouveau_channel_new+0xad/0x640 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f860a8dc>] nouveau_abi16_ioctl_channel_alloc+0x13c/0x360 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f860a7a0>] ? nouveau_abi16_ioctl_setparam+0x10/0x10 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f83564ef>] drm_ioctl+0x1cf/0x530 [drm]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f860a7a0>] ? nouveau_abi16_ioctl_setparam+0x10/0x10 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<c1439441>] ? __pm_runtime_resume+0x51/0x70  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8601071>] nouveau_drm_ioctl+0x51/0x80 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<f8601020>] ? nouveau_pmops_thaw+0x20/0x20 [nouveau]  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<c119f852>] do_vfs_ioctl+0x2f2/0x4f0  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<c11a8847>] ? __alloc_fd+0x87/0x100  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<c119fab0>] SyS_ioctl+0x60/0x90  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362]  [<c169515f>] sysenter_do_call+0x12/0x12 
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] Code: 00 89 d1 77 26 81 fa 00 00 01 00 76 06 0f b7 d2 ef c3 90 55 ba 85 d9 8b c1 89 e5 89 c8 e8 49 fe ff ff 5d c3 8d b4 26 00 00 00 00 <89> 02 c3 8d b6 00 00 00 00 8d bc 27 00 00 00 00 3d ff ff 03 00  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] EIP: [<c1326450>] iowrite32+0x30/0x40 SS:ESP 0068:f0273bf4  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] CR2: 00000000fb901000  
 Jun  2 19:21:36 dora-OptiPlex-755 kernel: [   99.235362] ---[ end trace 17f328ac40bfd38f ]---  
 Jun  2 19:21:42 dora-OptiPlex-755 pulseaudio[2627]: [pulseaudio] main.c: User-configured server at {bb62463f1e3cdafcfc9c38c75558af93}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.  
 Jun  2 19:21:43 dora-OptiPlex-755 rtkit-daemon[2326]: Successfully made thread 2676 of process 2676 (n/a) owned by '1000' high priority at nice level -11.  
 Jun  2 19:21:43 dora-OptiPlex-755 rtkit-daemon[2326]: Supervising 6 threads of 2 processes of 1 users.  
 Jun  2 19:21:43 dora-OptiPlex-755 pulseaudio[2676]: [pulseaudio] pid.c: Daemon already running.  
 Jun  2 19:24:29 dora-OptiPlex-755 whoopsie[1047]: message repeated 4 times: [ online]  
 Jun  2 19:26:00 dora-OptiPlex-755 whoopsie[1047]: Parsing /var/crash/linux-image-3.16.0-38-generic.240106.crash.  
 Jun  2 19:26:00 dora-OptiPlex-755 whoopsie[1047]: Uploading /var/crash/linux-image-3.16.0-38-generic.240106.crash.  
 Jun  2 19:26:01 dora-OptiPlex-755 whoopsie[1047]: Sent; server replied with: No error  
 Jun  2 19:26:01 dora-OptiPlex-755 whoopsie[1047]: Response code: 200  
 Jun  2 19:26:01 dora-OptiPlex-755 whoopsie[1047]: Got command: OOPSID  
 Jun  2 19:26:10 dora-OptiPlex-755 whoopsie[1047]: Parsing /var/crash/linux-image-3.16.0-38-generic.244218.crash.  
 Jun  2 19:26:10 dora-OptiPlex-755 whoopsie[1047]: Uploading /var/crash/linux-image-3.16.0-38-generic.244218.crash.  
 Jun  2 19:26:11 dora-OptiPlex-755 whoopsie[1047]: Sent; server replied with: No error  
 Jun  2 19:26:11 dora-OptiPlex-755 whoopsie[1047]: Response code: 200  
 Jun  2 19:26:11 dora-OptiPlex-755 whoopsie[1047]: Got command: OOPSID  
 Jun  2 19:26:58 dora-OptiPlex-755 kernel: [  421.339685] perf interrupt took too long (2615 > 2500), lowering kernel.perf_event_max_sample_rate to 50000  
 Jun  2 19:39:01 dora-OptiPlex-755 CRON[4656]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))  

 Jun  2 20:09:01 dora-OptiPlex-755 CRON[5081]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))  
 Jun  2 20:17:01 dora-OptiPlex-755 CRON[5203]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by tgalati4 on 2015-06-02
How old is this system? It might be a motherboard problem.  Try reseating the RAM, perhaps changing the order of the chips.  Run memtest for 30 complete cycles--it will take several hours.  If it passes without error, then boot again and open a terminal and page through:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.

Post any error messages that you see.

---

### Post by dino99 on 2015-06-03
with one of my system, i've experienced such issue many times, until i had the idea to check the ram voltage into the bios: it was using the default 'auto' mode; so i tested the manual way to set the required voltage for those ram sticks; and then no more oops with that system.

---

