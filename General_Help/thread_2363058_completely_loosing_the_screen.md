---
title: "completely loosing the screen"
date: 2017-06-05
forum: General Help
---

### Post by zozio32 on 2017-06-05
I am starting to having a weird screen issues:
I appear to randomly loose the connection to the screen.   Nothing can be done to get it back. After a while I do have to kill the computer.

It started on 16.04, I since move to Ubuntu Gnome 17.04 with a fresh install to see if that will solve the issue, but it keep happening. It seems random, I haven't yet identified a pattern.

Just a word on my config: 
Intel® Core&#8482; i5-3350P CPU @ 3.10GHz × 4 
GeForce GT 630/PCIe/SSE2
Ubuntu 17.04 64-bit
screen connected through hdmi

I am using the nvidia driver 375, everything seems fine here.

so, first:   Does anyone has an idea on what can be at play here?   faulty graphic card?
  second: as I have to kill the computer when it happen, is there a tool that can record what's happening so i could get a diagnostic?
Finally: when it will happen again, what can I do to kill the computer without having to revert to the power button?

I do not have anything else then Unbuntu installed, so I can't test the hardware with an other system.

thanks in advance

---

### Post by efflandt on 2017-06-06
It can be difficult to diagnose without another computer (or laptop) to test the display and cable with with to rule those out. Check the logs in /var/log especially syslog and syslog.1 and the Xorg logs to see if the system is aware of any issues with your graphics.

With graphics cards being solid state, you would not think they would fail, but they can. For example I had a cheap Galaxy GT 430 that shortly after its 1 year warranty expired, sometimes Windows reported something like "Graphics driver stopped responding, recovered". In Linux the symptoms were that occasionally randomly it stopped accepting keyboard input or mouse clicks, although, mouse cursor would often still move. Eventually it would get graphic glitches during boot and logs indicated that the graphics hardware was not responding. I replaced it with EVGA GTX 550 Ti with 3 year warranty that never had any problems and have also used MSI GTX 750 Ti and currently Asus GTX 1060 with no hardware issues.

The only LCD screen I ever had trouble with was an old Dell 17" 1280x1024 screen at work. At times it would not wake from standby unless I jiggled its VGA cable. Eventually it did not wake or turn on at all and its power LED was blinking green (I thould it blinked amber in standby). Apparently it was an internal problem in the monitor because same graphics card and VGA cable worked with another monitor for years until the PC was retired.

---

### Post by zozio32 on 2017-06-06
thanks for the answers.  I'll have a look at the logs you mention tonight and post back.
I can test the screen with a laptop, that should be ok. What I can't do, is testing the graphic card with an other OS. But as everything seems fine at start up, I believe it is more on the computer side.

One of the reason I upgraded to 17.04 was that I had weird graphical behavior after the computer whent to sleep, such as areas around windows with every pixel from a different color. That seems to have disapeared however with the upgrade...

---

### Post by Impavidus on 2017-06-06
Last time I had such a problem it was the monitor. It was quite obvious, as it took a few deciseconds for the image to shrink on the CRT monitor. It happened when it got hot after after an hour or so. So we replaced it by a led screen.

For your final point: you can reboot the computer with SysRq+REISUB. See [wiki]("https://en.wikipedia.org/wiki/Magic_SysRq_key"). That should prevent file system damage or worse.

---

### Post by zozio32 on 2017-06-06
I found this in syslog.1 of yesterday, just before a crash I think, is it helpful?

```
Jun  5 22:36:09 zozio32-p6-2487ea dbus-daemon[1537]: Successfully activated service 'org.gnome.ChromeGnomeShell'
Jun  5 22:36:11 zozio32-p6-2487ea firefox.desktop[5248]: 1496698571491#011FirefoxAccounts#011ERROR#011Background refresh of profile failed, bumping _cachedAt: {"name":"FxAccountsProfileClientError","code":304,"errno":997,"error":"PARSE_ERROR","message":null}
Jun  5 22:36:13 zozio32-p6-2487ea firefox.desktop[5248]: console.warn: SDK worker-child started as frozen on unexpected initial document.readyState {"initialDocumentReadyState":"uninitialized","windowLocation":"about:blank"}
Jun  5 22:36:30 zozio32-p6-2487ea kernel: [ 4543.352532] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:31 zozio32-p6-2487ea kernel: [ 4544.136506] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:31 zozio32-p6-2487ea kernel: [ 4544.648490] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:32 zozio32-p6-2487ea kernel: [ 4545.140482] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:32 zozio32-p6-2487ea kernel: [ 4545.632460] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:33 zozio32-p6-2487ea kernel: [ 4546.124463] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:33 zozio32-p6-2487ea kernel: [ 4546.636429] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:34 zozio32-p6-2487ea kernel: [ 4547.148430] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:34 zozio32-p6-2487ea kernel: [ 4547.660396] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:35 zozio32-p6-2487ea kernel: [ 4548.172394] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:35 zozio32-p6-2487ea kernel: [ 4548.684382] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303882] NVRM: GPU at PCI:0000:01:00: GPU-435cb66f-d89f-a234-9414-70b032521666
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303884] NVRM: Xid (PCI:0000:01:00): 79, GPU has fallen off the bus.
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303884] 
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303887] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303894] NVRM: A GPU crash dump has been created. If possible, please run
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303894] NVRM: nvidia-bug-report.sh as root to collect this data before
Jun  5 22:36:51 zozio32-p6-2487ea kernel: [ 4564.303894] NVRM: the NVIDIA kernel module is unloaded.
Jun  5 22:38:30 zozio32-p6-2487ea kernel: [ 4663.348779] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:38:31 zozio32-p6-2487ea kernel: [ 4664.136753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:38:32 zozio32-p6-2487ea kernel: [ 4664.940723] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:38:32 zozio32-p6-2487ea kernel: [ 4665.452700] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:38:33 zozio32-p6-2487ea kernel: [ 4665.964676] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:38:34 zozio32-p6-2487ea kernel: [ 4667.060661] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:41:06 zozio32-p6-2487ea kernel: [ 4819.375861] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:41:07 zozio32-p6-2487ea kernel: [ 4820.259815] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:41:24 zozio32-p6-2487ea kernel: [ 4837.097739] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jun  5 22:41:24 zozio32-p6-2487ea kernel: [ 4837.097742] sd 6:0:0:0: [sdc] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jun  5 22:41:24 zozio32-p6-2487ea kernel: [ 4837.097743] sd 6:0:0:0: [sdc] tag#0 Add. Sense: No additional sense information
Jun  5 22:41:24 zozio32-p6-2487ea kernel: [ 4837.097745] sd 6:0:0:0: [sdc] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Jun  5 22:42:30 zozio32-p6-2487ea kernel: [ 4903.341194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:42:31 zozio32-p6-2487ea kernel: [ 4904.437173] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:42:32 zozio32-p6-2487ea kernel: [ 4905.241151] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  5 22:51:24 zozio32-p6-2487ea kernel: [ 5437.070278] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jun  5 22:51:24 zozio32-p6-2487ea kernel: [ 5437.070280] sd 6:0:0:0: [sdc] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jun  5 22:51:24 zozio32-p6-2487ea kernel: [ 5437.070281] sd 6:0:0:0: [sdc] tag#0 Add. Sense: No additional sense information
Jun  5 22:51:24 zozio32-p6-2487ea kernel: [ 5437.070283] sd 6:0:0:0: [sdc] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Jun  5 22:53:11 zozio32-p6-2487ea wpa_supplicant[1109]: wlp3s0: WPA: Group rekeying completed with 54:b8:0a:1e:1d:d0 [GTK=TKIP]
```

---

### Post by zozio32 on 2017-06-06
actually, I managed to recreate the bug.   It is when i heavily load the GPU: videos for example, or batch processing of raw photos with darktable (OpenGl activated).
The log gave me the same type of entries:
```
Jun  6 22:56:48 zozio32-p6-2487ea dbus[850]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jun  6 22:56:48 zozio32-p6-2487ea systemd[1]: Starting Hostname Service...
Jun  6 22:56:48 zozio32-p6-2487ea gvfsd[1638]: mkdir failed on directory /var/cache/samba: Permission denied
Jun  6 22:56:48 zozio32-p6-2487ea gvfsd[1638]: mkdir failed on directory /var/cache/samba: Permission denied
Jun  6 22:56:48 zozio32-p6-2487ea dbus[850]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun  6 22:56:48 zozio32-p6-2487ea systemd[1]: Started Hostname Service.
Jun  6 22:56:49 zozio32-p6-2487ea gvfsd[1638]: mkdir failed on directory /var/cache/samba: Permission denied
Jun  6 22:56:50 zozio32-p6-2487ea gvfsd[1638]: message repeated 3 times: [ mkdir failed on directory /var/cache/samba: Permission denied]
Jun  6 22:56:52 zozio32-p6-2487ea gvfsd[1638]: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jun  6 22:56:52 zozio32-p6-2487ea gvfsd-network[3383]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jun  6 22:58:39 zozio32-p6-2487ea kernel: [ 2135.438200] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955785] NVRM: GPU at PCI:0000:01:00: GPU-435cb66f-d89f-a234-9414-70b032521666
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955788] NVRM: Xid (PCI:0000:01:00): 79, GPU has fallen off the bus.
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955788] 
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955792] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955799] NVRM: A GPU crash dump has been created. If possible, please run
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955799] NVRM: nvidia-bug-report.sh as root to collect this data before
Jun  6 22:59:42 zozio32-p6-2487ea kernel: [ 2197.955799] NVRM: the NVIDIA kernel module is unloaded.
Jun  6 23:00:13 zozio32-p6-2487ea kernel: [ 2228.476928] nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000917c:0:0:0x0000000f
Jun  6 23:00:13 zozio32-p6-2487ea kernel: [ 2228.477698] nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000917c:0:0:0x0000000f
Jun  6 23:00:13 zozio32-p6-2487ea kernel: [ 2228.478081] nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000917c:0:0:0x0000000f
Jun  6 23:00:16 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059c, 0x0000aff4, 0x0000b0a0)
Jun  6 23:00:23 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (1-S, 17, 0x059c, 0x0000aff4, 0x0000b0a0)
Jun  6 23:00:26 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059a, 0x0000aff4, 0x0000b0a0)
Jun  6 23:00:33 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (1-S, 17, 0x059a, 0x0000aff4, 0x0000b0a0)
Jun  6 23:00:36 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059d, 0x0000aff4, 0x0000b14c)
Jun  6 23:00:43 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (1-S, 17, 0x059d, 0x0000aff4, 0x0000b14c)
Jun  6 23:00:46 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059b, 0x0000aff4, 0x0000b17c)
Jun  6 23:00:53 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (1-S, 17, 0x059b, 0x0000aff4, 0x0000b17c)
Jun  6 23:00:56 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059e, 0x0000aff4, 0x0000b1b4)
Jun  6 23:01:03 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (1-S, 17, 0x059e, 0x0000aff4, 0x0000b1b4)
Jun  6 23:01:06 zozio32-p6-2487ea /usr/lib/gdm3/gdm-x-session[1520]: (WW) NVIDIA(0): WAIT (2-S, 17, 0x059c, 0x0000aff4, 0x0000b1b4)

```

it definitely look like an issue with the graphic card. i could give it a good clean again, or I could change it...

btw, thanks for the tip about how to reboot the computer!   very handy

---

### Post by zozio32 on 2017-06-08
Well, i did a proper cleanup: I have extracted the graphic card and the processor fan to properly remove the dust from all the elements. Magic, it works, at least for now. The computer is more silent, quicker, and I have batch process quite a lot of photos + watch a documentary yesterday night without issues.   No more reason to get an uneeded new graphic card!

thanks for the suggestions, and I did learn something useful

---

