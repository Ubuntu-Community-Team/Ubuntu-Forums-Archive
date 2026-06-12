---
title: "Laptop freezing for some second"
date: 2022-11-05
forum: General Help
---

### Post by paoloevan on 2022-11-05
[COLOR=#232629][FONT=-apple-system]I state that I am not an expert in linux and computer science in general, however I have already searched in the forum but I have not found a solution, or I have not been able given the above limitations.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The problem in short is this: every so much time (it can be six hours as 10 minutes) the pc freezing, mouse and keyboard locked, while music, audio, streaming continue to go on. This lasts for about 5-10 seconds, after which it unlocks and works as before.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Dell Inc. Inspiron 15 3520 Ram 16,0 GiB 12th Gen Intel® Core™ i5-1235U × 12 Mesa Intel® Graphics (ADL GT2) Disco 512,1 GB

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]to the command journalctl -b, at the exact time it occurred it gives this message. I put code of different episodes.

[/FONT][/COLOR]```

ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: kernel bug: Touch jump detected and discarded.
ott 27 15:56:20 paolo gnome-shell[1216]: See https://wayland.freedesktop.org/libinput/doc/1.21.0/touchpad-jumping-cursors.html for details
ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: kernel bug: Touch jump detected and discarded.
ott 27 15:56:20 paolo gnome-shell[1216]: See https://wayland.freedesktop.org/libinput/doc/1.21.0/touchpad-jumping-cursors.html for details
ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: kernel bug: Touch jump detected and discarded.
ott 27 15:56:20 paolo gnome-shell[1216]: See https://wayland.freedesktop.org/libinput/doc/1.21.0/touchpad-jumping-cursors.html for details
ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: kernel bug: Touch jump detected and discarded.
ott 27 15:56:20 paolo gnome-shell[1216]: See https://wayland.freedesktop.org/libinput/doc/1.21.0/touchpad-jumping-cursors.html for details
ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: kernel bug: Touch jump detected and discarded.
ott 27 15:56:20 paolo gnome-shell[1216]: See https://wayland.freedesktop.org/libinput/doc/1.21.0/touchpad-jumping-cursors.html for details
ott 27 15:56:20 paolo gnome-shell[1216]: libinput error: event13 - VEN_04F3:00 04F3:3259 Touchpad: WARNING: log rate limit exceeded (5 msgs per 24h). Discarding future mess>
ott 27 15:56:29 paolo kernel: Asynchronous wait on fence 0000:00:02.0:gnome-shell[1216]:ed890 timed out (hint:intel_atomic_commit_ready [i915])
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] HuC authenticated
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] GuC submission enabled
ott 27 15:56:33 paolo kernel: i915 0000:00:02.0: [drm] GuC SLPC enabled
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```

ott 27 16:21:24 paolo kernel: Asynchronous wait on fence 0000:00:02.0:gnome-shell[1216]:f8272 timed out (hint:intel_atomic_commit_ready [i915])
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] HuC authenticated
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] GuC submission enabled
ott 27 16:21:28 paolo kernel: i915 0000:00:02.0: [drm] GuC SLPC enabled
ott 27 16:21:28 paolo code.desktop[11799]: [11799:1027/162128.519749:ERROR:shared_context_state.cc(846)] SharedContextState context lost via ARB/EXT_robustness. Reset statu>
ott 27 16:21:28 paolo code.desktop[11799]: [11799:1027/162128.519978:ERROR:gpu_service_impl.cc(990)] Exiting GPU process because some drivers can't recover from errors. GPU>
ott 27 16:21:28 paolo code.desktop[11762]: [11762:1027/162128.543104:ERROR:gpu_process_host.cc(980)] GPU process exited unexpectedly: exit_code=8704
ott 27 16:21:28 paolo code.desktop[20522]: libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)



```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```

nov 04 10:31:57 paolo systemd[1]: Started Run anacron jobs.
nov 04 10:31:57 paolo anacron[9821]: Anacron 2.3 started on 2022-11-04
nov 04 10:31:57 paolo anacron[9821]: Normal exit (0 jobs run)
nov 04 10:31:57 paolo systemd[1]: anacron.service: Deactivated successfully.
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```

Key repeat discarded, Wayland compositor doesn't seem to be processing events fast enough!
Key repeat discarded, Wayland compositor doesn't seem to be processing events fast enough!
Key repeat discarded, Wayland compositor doesn't seem to be processing events fast enough!
Key repeat discarded, Wayland compositor doesn't seem to be processing events fast enough!
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```

nov 04 12:50:45 paolo kernel: Asynchronous wait on fence 0000:00:02.0:gnome-shell[1460]:76612 timed out (hint:intel_atomic_commit_ready [i915])
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] HuC authenticated
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] GuC submission enabled
nov 04 12:50:49 paolo kernel: i915 0000:00:02.0: [drm] GuC SLPC enabled
```[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]

---

