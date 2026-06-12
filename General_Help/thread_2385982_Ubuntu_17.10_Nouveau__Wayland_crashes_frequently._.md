---
title: "Ubuntu 17.10: Nouveau / Wayland crashes frequently.  &quot;hw_done timed out&quot;"
date: 2018-02-27
forum: General Help
---

### Post by uigrad on 2018-02-27
My system suddenly locks up at least once per day, often more, and I have to completely reboot it to bring it back up.  Even restarting gdm3 does nothing. It doesn't seem that my actions have anything to do with when the system locks up, other than that my mouse is usually moving, or my mouswheel is moving when it locks up in most cases.

When it crashes, I cannot change ttys with ctl-alt-F2, for example, and ctrl-alt-Backspace does nothing either.  The screen freezes.  The things that stay operational are audio (if I'm on a conference call, it continues), and networking (I can ssh in).

Using ssh, I've attempted killing Wayland with SIGKILL, but it doesn't work after restarting.  I am able to restart gdm in a more friendly way using:

```
sudo /etc/init.d/gdm3 restart
```

When I do, the screen goes black and after a minute or two, dmesg output begins appearing, and every 120 seconds, it prints out stuff similar to this:

```
Feb 27 10:06:51 mysys kernel: [59742.213691] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59752.453921] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59762.694072] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] flip_done timed out
Feb 27 10:06:51 mysys kernel: [59772.934240] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59783.174352] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59793.414550] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] flip_done timed out
Feb 27 10:06:51 mysys kernel: [59803.654735] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59813.894880] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:06:51 mysys kernel: [59813.894997] INFO: task kworker/u16:2:14204 blocked for more than 120 seconds.
Feb 27 10:06:51 mysys kernel: [59813.894999]       Tainted: G        W       4.13.0-36-generic #40-Ubuntu
Feb 27 10:06:51 mysys kernel: [59813.895000] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```

Eventually, I have to use my ssh session to shutdown the system using "sudo shutdown now".  After rebooting, then gdm seems to run correctly.  I may be restarting gdm incorrectly, but I think the most likely problem is that some independent part of the graphics card itself is locked up, so gdm isn't able to start up correctly.

I used lspci -vv to get my video and audio card info:


```
01:00.0 VGA compatible controller: NVIDIA Corporation GK208GLM [Quadro K610M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company GK208GLM [Quadro K610M]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 33
    Region 0: Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at 70000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at 80000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 5000 [size=128]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Subsystem: Hewlett-Packard Company GK208 HDMI/DP Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

I briefly tried installing the official NVidia drivers, but when I did, it seemed the system froze every time gdm started, so I have removed them now.


I've put the full system log here: [https://pastebin.com/PgbjWLSe](https://pastebin.com/PgbjWLSe)

This is the irteresting part.  It seems that even though I'm using Wayland, it looks like Anacron is running something that tries starting up an X11 session, which makes no sense to me:


```
Feb 27 10:03:44 mysys systemd[1]: Started Session c3 of user gdm.
Feb 27 10:03:44 mysys gsd-rfkill[2240]: g_object_notify: object class 'CcRfkillGlib' has no property named 'kernel-noinput'
Feb 27 10:03:44 mysys kernel: [59637.278525] rfkill: input handler enabled
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: _XSERVTransMakeAllCOTSServerListeners: server already running
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (--) Log file renamed from "/var/lib/gdm3/.local/share/xorg/Xorg.pid-15548.log" to "/var/lib/gdm3/.local/share/xorg/Xorg.1.log"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: X.Org X Server 1.19.5
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Release Date: 2017-10-12
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: X Protocol Version 11, Revision 0
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Current Operating System: Linux mysys 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-36-generic root=UUID=9ca7c508-190f-4c64-9692-cca1eb64af79 ro quiet splash vt.handoff=7
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Build Date: 15 October 2017  05:51:19PM
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: xorg-server 2:1.19.5-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Current version of pixman: 0.34.0
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011Before reporting problems, check http://wiki.x.org
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011to make sure that you have the latest version.
```

The output of gdm-x-session is long, so skipping forward a few hundred lines:

```
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) LoadModule: "nvidia"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) Warning, couldn't open module nvidia
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) UnloadModule: "nvidia"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Unloading nvidia
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Failed to load module "nvidia" (module does not exist, 0)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) LoadModule: "nouveau"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) Warning, couldn't open module nouveau
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) UnloadModule: "nouveau"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Unloading nouveau
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Failed to load module "nouveau" (module does not exist, 0)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) LoadModule: "modesetting"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Module modesetting: vendor="X.Org Foundation"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011compiled for 1.19.5, module version = 1.19.5
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011Module class: X.Org Video Driver
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011ABI class: X.Org Video Driver, version 23.0
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) LoadModule: "fbdev"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) Warning, couldn't open module fbdev
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) UnloadModule: "fbdev"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Unloading fbdev
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Failed to load module "fbdev" (module does not exist, 0)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) LoadModule: "vesa"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) Warning, couldn't open module vesa
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) UnloadModule: "vesa"
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) Unloading vesa
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Failed to load module "vesa" (module does not exist, 0)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (II) modesetting: Driver for Modesetting Kernel Drivers: kms
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) xf86OpenConsole: VT_ACTIVATE failed: Operation not permitted
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Fatal server error:
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) xf86OpenConsole: Switching VT failed
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: Please consult the The X.Org Foundation support
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: #011 at http://wiki.x.org
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]:  for help.
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Please also check the log file at "/var/lib/gdm3/.local/share/xorg/Xorg.1.log" for additional information.
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE)
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) xf86CloseConsole: KDSETMODE failed: Operation not permitted
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) xf86CloseConsole: VT_SETMODE failed: Operation not permitted
Feb 27 10:03:44 mysys /usr/lib/gdm3/gdm-x-session[15546]: (WW) xf86CloseConsole: VT_ACTIVATE failed: Operation not permitted
Feb 27 10:04:09 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) systemd-logind: ReleaseControl failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Feb 27 10:04:09 mysys /usr/lib/gdm3/gdm-x-session[15546]: (EE) Server terminated with error (1). Closing log file.
Feb 27 10:04:09 mysys /usr/lib/gdm3/gdm-x-session[15546]: Unable to run X server
Feb 27 10:04:09 mysys gnome-shell[2038]: Could not release device 13,80: Timeout was reached
Feb 27 10:04:11 mysys gsd-power[2236]: Error setting property 'PowerSaveMode' on interface org.gnome.Mutter.DisplayConfig: Timeout was reached (g-io-error-quark, 24)
Feb 27 10:04:15 mysys colord[964]: failed to get session [pid 8406]: No data available
Feb 27 10:04:34 mysys gnome-shell[2038]: Could not release device 13,81: Timeout was reached
Feb 27 10:04:59 mysys gnome-shell[2038]: Could not release device 13,82: Timeout was reached
Feb 27 10:05:18 mysys kernel: [59647.492208] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59657.732256] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59667.972501] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] flip_done timed out
Feb 27 10:05:18 mysys kernel: [59670.633975] nouveau 0000:01:00.0: DRM: base-1: timeout
Feb 27 10:05:18 mysys kernel: [59680.772754] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59691.012911] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59693.060987] INFO: task kworker/u16:2:14204 blocked for more than 120 seconds.
Feb 27 10:05:18 mysys kernel: [59693.060989]       Tainted: G        W       4.13.0-36-generic #40-Ubuntu
Feb 27 10:05:18 mysys kernel: [59693.060990] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 27 10:05:18 mysys kernel: [59693.060991] kworker/u16:2   D    0 14204      2 0x00000000
Feb 27 10:05:18 mysys kernel: [59693.061054] Workqueue: events_unbound nv50_disp_atomic_commit_work [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061056] Call Trace:
Feb 27 10:05:18 mysys kernel: [59693.061062]  __schedule+0x291/0x8a0
Feb 27 10:05:18 mysys kernel: [59693.061088]  ? nvkm_client_notify_get+0x27/0x40 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061090]  schedule+0x2c/0x80
Feb 27 10:05:18 mysys kernel: [59693.061093]  schedule_timeout+0x1f4/0x360
Feb 27 10:05:18 mysys kernel: [59693.061133]  ? nvkm_client_ioctl+0x12/0x20 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061156]  ? nvif_object_ioctl+0x47/0x50 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061193]  ? nouveau_bo_rd32+0x2a/0x30 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061229]  ? nv84_fence_read+0x2e/0x30 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061234]  dma_fence_default_wait+0x1c7/0x260
Feb 27 10:05:18 mysys kernel: [59693.061237]  ? dma_fence_default_wait+0x1c7/0x260
Feb 27 10:05:18 mysys kernel: [59693.061240]  ? dma_fence_free+0x20/0x20
Feb 27 10:05:18 mysys kernel: [59693.061243]  dma_fence_wait_timeout+0x3e/0xf0
Feb 27 10:05:18 mysys kernel: [59693.061254]  drm_atomic_helper_wait_for_fences+0x62/0xb0 [drm_kms_helper]
Feb 27 10:05:18 mysys kernel: [59693.061290]  nv50_disp_atomic_commit_tail+0x55/0x3b20 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061322]  nv50_disp_atomic_commit_work+0x12/0x20 [nouveau]
Feb 27 10:05:18 mysys kernel: [59693.061326]  process_one_work+0x1ec/0x410
Feb 27 10:05:18 mysys kernel: [59693.061329]  worker_thread+0x32/0x410
Feb 27 10:05:18 mysys kernel: [59693.061332]  kthread+0x128/0x140
Feb 27 10:05:18 mysys kernel: [59693.061335]  ? process_one_work+0x410/0x410
Feb 27 10:05:18 mysys kernel: [59693.061337]  ? kthread_create_on_node+0x70/0x70
Feb 27 10:05:18 mysys kernel: [59693.061340]  ret_from_fork+0x35/0x40
```

The anacron job running and the starting of X.org may be unrelated.  I looked through some of my other system logs, and the crash doesn't always follow the starting of gdm-x-session.  

Please help!

---

### Post by uigrad on 2018-03-02
I found another user that is having some kernel errors similar to mine:

[https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10](https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10)

These lines seem familiar:

```

 kernel: [  363.484267] INFO: task kworker/u8:1:51 blocked for more than 120 seconds. 
 kernel: [  363.484281]       Tainted: G           OE   4.13.0-16-generic #19-Ubuntu

```

Things that are similar:
 
[LIST]
[*]kworker blocked 
[*]"tainted" kernel 
[*]kernel version 4.13.0-16 
[/LIST]
 
Things that are different:
[LIST]
[*]My crash happens randomly, their crash happens on shutdown
[/LIST]

Since I don't need my wireless card most of the time, I just turned off wi-fi.  I've gone for 3 days without a crash, so it seems that is the source of my crashes!

I haven't attempted to downgrade the kernel yet, but I may eventually do it, so that I can use my wireless card without crashes.

---

### Post by uigrad on 2018-03-09
So, it turns out that it was not related to my wifi card, at least not directly.  Disabling wifi prevented crashes for about 3 days, but now it's crashed 5 times in the last 3 days, even with wifi off.

This Nouveau bug appears to be related:

[https://bugs.freedesktop.org/show_bug.cgi?id=93629](https://bugs.freedesktop.org/show_bug.cgi?id=93629)

In nearly all of my crashes, I see this in dmesg output at the time of the crash:

```
Feb 27 10:05:18 mysys kernel: [59705.559510] nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Feb 27 10:05:18 mysys kernel: [59705.559526] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Feb 27 10:05:18 mysys kernel: [59705.559573] nouveau 0000:01:00.0: fifo: channel 13: killed
Feb 27 10:05:18 mysys kernel: [59705.559587] nouveau 0000:01:00.0: fifo: engine 6: scheduled for recovery
Feb 27 10:05:18 mysys kernel: [59705.559596] nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Feb 27 10:05:18 mysys kernel: [59705.559785] nouveau 0000:01:00.0: systemd-logind[901]: channel 13 killed!
Feb 27 10:05:18 mysys kernel: [59711.493241] [drm:drm_atomic_helper_swap_state [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59721.733410] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] hw_done timed out
Feb 27 10:05:18 mysys kernel: [59731.973563] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:head-1] flip_done timed out

```

The CTXSW_TIMEOUT is indicative of it being bug 93629.

```

$ lspci -d 10de:
01:00.0 VGA compatible controller: NVIDIA Corporation GK208GLM [Quadro K610M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)

```

So, if it is this bug 93629 that is causing the problem, what can I do about it?

I see that [comment 19]("https://bugs.freedesktop.org/show_bug.cgi?id=93629#c19") includes a patch as an attachment and says:

> For anyone who experiences random hangs using the nouveau firmware and have spotted "SCHED_ERROR [ CTXSW_TIMEOUT ]" in the logs, 
please build a kernel with the attached patch and run using the nouveau firmware. Minimum kernel required is 4.6.

But, that comment is from May 2016 and for version 4.6 of the kernel, which is quite old now.  Should I be doing this?  I have always relied on "apt dist-upgrade" to keep me up to date, so is patching the kernel manually going to affect that?  

I'm really hoping someone with more experience can give me advice here.  I can't afford for my machine to keep crashing twice per day.

---

### Post by uigrad on 2018-03-15
Today I had a crash while typing "mail.google.com" into the location bar of firefox.  The screen just froze like usual.

I used ssh to connect again, and typed "sudo init 4", but the command couldn't complete.  I eventually had to interrupt it with ctrl-c.  I eventually had to "sudo shutdown now" to get out.

When I logged in again and opened Firefox, It restored its saved state.  In the saved state, my location bar contained:

maiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii

There were hundreds, if not thousands of the letter i.  So, it seems that when it crashed, it took down the keyboard driver, and whatever signal it was receiving from the keyboard just continued. 

I noticed that when I find "CTXSW_TIMEOUT" in the dmesg log, the time stamp for it is always 5-15 seconds after the time that is frozen on my system tray clock.   

I'm still looking for help, and hoping that someone out there with more knowledge than me will see this and give me some assistance.  It's really hard getting work done when my system freezes so frequently.

---

### Post by TheFu on 2018-03-21
[https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts](https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts)  says there is a memory leak in Gnome3.  Memory leaks mean that pointers are not pointing where the programmer needs them and that often leads to program/data corruption.  

I'm concerned that the Gnome project doesn't use memory validation tools [http://valgrind.org/](http://valgrind.org/) and continuous integration testing to minimize these sorts of issues early in the development cycle.  Very concerning.

---

