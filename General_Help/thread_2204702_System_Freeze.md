---
title: "System Freeze"
date: 2014-02-09
forum: General Help
---

### Post by Brandon_MacEachern on 2014-02-09
My Ubuntu running laptop generally doesn't crash and has worked just fine.  But for some reason, twice today it has completely frozen.  I can't click anything, windows don't move, etc.  Mouse cursor moves though.

I was able to find in the system logs where it froze.

```
Feb  9 19:28:54 brandon-MacBookPro udisksd[2256]: Mounted /dev/mmcblk0p1 at /media/brandon/CANOO on behalf of uid 1000Feb  9 19:28:54 brandon-MacBookPro dbus[838]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb  9 19:28:54 brandon-MacBookPro dbus[838]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb  9 19:29:18 brandon-MacBookPro whoopsie[1272]: online
Feb  9 19:29:19 brandon-MacBookPro whoopsie[1272]: online
Feb  9 19:29:52 brandon-MacBookPro kernel: [10182.623501] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  9 19:30:27 brandon-MacBookPro whoopsie[1272]: online
Feb  9 19:31:42  whoopsie[1272]: last message repeated 2 times
Feb  9 19:31:52 brandon-MacBookPro kernel: [10303.060014] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  9 19:33:53 brandon-MacBookPro kernel: [10423.509455] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  9 19:35:52 brandon-MacBookPro kernel: [10542.841327] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  9 19:37:52 brandon-MacBookPro kernel: [10662.622553] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  9 19:37:55 brandon-MacBookPro whoopsie[1272]: online
Feb  9 19:39:13  whoopsie[1272]: last message repeated 2 times
Feb  9 19:39:15 brandon-MacBookPro dbus[838]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb  9 19:39:15 brandon-MacBookPro dbus[838]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb  9 19:39:29 brandon-MacBookPro udisksd[2256]: Cleaning up mount point /media/brandon/CANOO (device 179:1 is not mounted)
Feb  9 19:39:29 brandon-MacBookPro udisksd[2256]: Unmounted /dev/mmcblk0p1 on behalf of uid 1000
Feb  9 19:39:39 brandon-MacBookPro kernel: [10769.995314] show_signal_msg: 144 callbacks suppressed
Feb  9 19:39:39 brandon-MacBookPro kernel: [10769.995320] nautilus[2237]: segfault at 8 ip 00007f0c690452d9 sp 00007fffdb9c1f60 error 4 in libglib-2.0.so.0.3800.1[7f0c68fe2000+fe000]

```

---

### Post by Brandon_MacEachern on 2014-02-10
I'm beginning to feel that I ask too hard of questions.

Everything I have asked here so far has yielded zero responses whatsoever, except a couple things in which I was grateful for.

I'm going to take a stab at this and say it was probably the SD card reader that froze Ubuntu.

---

