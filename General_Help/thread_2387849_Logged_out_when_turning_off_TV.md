---
title: "Logged out when turning off TV"
date: 2018-03-24
forum: General Help
---

### Post by Rushed on 2018-03-24
Hello,

I am trying to understand why is my Ubuntu being logged out when I close my monitor. I went in privacy settings and turned off the screen lock, it still happens. I turned off automatic suspend and blank screen off in the power settings. I even use caffeine to prevent anything from logging me out. When I turn off my TV, it still happens.

I am running Ubuntu 17.10 on a freshly built PC. It is an i5-8400 coffee lake, 4gb RAM, asrock 370m MB, only running an integrated gpu since it's for videos only (htpc) and want to consume less power as possible.

Here is the log, maybe something causes a crash (as read somewhere else on ubuntu forums). 

```
Mar 24 10:02:52 joe-htpc kernel: [   11.767299] ip6_tables: (C) 2000-2006 Netfilter Core Team
Mar 24 10:21:14 joe-htpc kernel: [ 1113.027561] perf: interrupt took too long (2552 > 2500), lowering kernel.perf_event_max_sample_rate to 78250
Mar 24 10:25:53 joe-htpc kernel: [ 1392.126443] perf: interrupt took too long (3192 > 3190), lowering kernel.perf_event_max_sample_rate to 62500
Mar 24 10:33:52 joe-htpc kernel: [ 1870.411661] perf: interrupt took too long (4029 > 3990), lowering kernel.perf_event_max_sample_rate to 49500
Mar 24 10:38:55 joe-htpc kernel: [ 2173.602436] perf: interrupt took too long (5065 > 5036), lowering kernel.perf_event_max_sample_rate to 39250
Mar 24 10:46:31 joe-htpc kernel: [ 2630.112344] perf: interrupt took too long (6344 > 6331), lowering kernel.perf_event_max_sample_rate to 31500
Mar 24 10:59:12 joe-htpc kernel: [ 3391.098739] perf: interrupt took too long (7940 > 7930), lowering kernel.perf_event_max_sample_rate to 25000
Mar 24 11:09:45 joe-htpc kernel: [ 4023.790507] perf: interrupt took too long (9994 > 9925), lowering kernel.perf_event_max_sample_rate to 20000
Mar 24 14:02:49 joe-htpc kernel: [14407.490847] [drm:drm_scdc_set_high_tmds_clock_ratio [drm_kms_helper]] *ERROR* Failed to read tmds config, err=-6
Mar 24 14:02:49 joe-htpc kernel: [14407.490932] [drm:intel_hdmi_handle_sink_scrambling [i915]] *ERROR* Set TMDS ratio failed
Mar 24 14:02:49 joe-htpc kernel: [14407.654313] show_signal_msg: 22 callbacks suppressed
Mar 24 14:02:49 joe-htpc kernel: [14407.654320] gnome-shell[1132]: segfault at 400000006 ip 0000000400000006 sp 00007ffdb6d27808 error 14
Mar 24 14:02:49 joe-htpc kernel: [14407.802982] [drm:drm_scdc_set_high_tmds_clock_ratio [drm_kms_helper]] *ERROR* Failed to read tmds config, err=-6
Mar 24 14:02:49 joe-htpc kernel: [14407.803023] [drm:intel_hdmi_handle_sink_scrambling [i915]] *ERROR* Set TMDS ratio failed
Mar 24 14:02:49 joe-htpc kernel: [14407.811422] rfkill: input handler enabled
Mar 24 14:02:49 joe-htpc kernel: [14407.864965] [drm:drm_scdc_set_high_tmds_clock_ratio [drm_kms_helper]] *ERROR* Failed to read tmds config, err=-6
Mar 24 14:02:49 joe-htpc kernel: [14407.865001] [drm:intel_hdmi_handle_sink_scrambling [i915]] *ERROR* Set TMDS ratio failed
Mar 24 14:03:02 joe-htpc kernel: [14420.978276] rfkill: input handler disabled
Mar 24 14:05:00 joe-htpc kernel: [14539.141142] [drm:drm_scdc_set_high_tmds_clock_ratio [drm_kms_helper]] *ERROR* Failed to read tmds config, err=-6
Mar 24 14:05:00 joe-htpc kernel: [14539.141227] [drm:intel_hdmi_handle_sink_scrambling [i915]] *ERROR* Set TMDS ratio failed
Mar 24 14:05:01 joe-htpc kernel: [14539.308356] gnome-shell[2994]: segfault at 18 ip 00007f90ebe9f2d4 sp 00007ffc7dd17978 error 4 in libmutter-1.so.0.0.0[7f90ebe00000+142000]
Mar 24 14:05:01 joe-htpc kernel: [14539.804744] rfkill: input handler enabled
Mar 24 14:05:13 joe-htpc kernel: [14551.557178] rfkill: input handler disabled
Mar 24 14:06:11 joe-htpc kernel: [14609.583412] [drm:drm_scdc_set_high_tmds_clock_ratio [drm_kms_helper]] *ERROR* Failed to read tmds config, err=-6
Mar 24 14:06:11 joe-htpc kernel: [14609.583505] [drm:intel_hdmi_handle_sink_scrambling [i915]] *ERROR* Set TMDS ratio failed
Mar 24 14:06:11 joe-htpc kernel: [14609.669634] gnome-shell[4295]: segfault at 18 ip 00007f03a4c082d4 sp 00007ffe2eccdae8 error 4 in libmutter-1.so.0.0.0[7f03a4b69000+142000]
Mar 24 14:06:11 joe-htpc kernel: [14609.780453] rfkill: input handler enabled
Mar 24 14:06:24 joe-htpc kernel: [14623.069762] rfkill: input handler disabled
```

I left my htpc at around 11 and came back around 2pm. I reproduced the same problem again around 14:05 .

I see a couple of errors there but I still need help figuring out what is the main problem.

I think something happens when I turn back the screen on because when I leave it on for video encoding, the job gets done in the end... It only stops working when I turn the screen back.

Help would be really appreciated ! Thanks in advance :)

---

### Post by kerry_s on 2018-03-24
run this in term:
gsettings set org.gnome.desktop.lockdown disable-lock-screen true

---

### Post by Rushed on 2018-03-24
I tried that, nothing happened :/ with sudo added before the command line , i got:

```
(process:2641): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line &#8220;dbus-launch --autolaunch=3aa5abc98149428c82ae9075e683acd1 --binary-syntax --close-stderr&#8221;: Child process exited with code 1

```

---

### Post by kerry_s on 2018-03-24
no sudo, run it just like it is. you won't see nothing happening. the lock should be gone from the session menu.

don't use sudo/root if your not told to, you can break stuff.

---

### Post by Rushed on 2018-03-24
Okay. The problem still occurs, even after running the command you told me to. I upgraded my kernel from 4.13 to 4.15 thinking that would fix the problem, still no success. 
I tried logging in directly to KODI and when i turned off my screen there, it didn't log me out. When I use wayland or XORG, it's when this occurs. If that can help :o

---

### Post by Rushed on 2018-03-26
*bump*

---

### Post by kerry_s on 2018-03-26
what i think is happing is when you turn off the tv, it loses monitor & can't find, like a headless server.
1: are you logged in to the xorg session? the 1 that says **gnome on xorg**
2: i think there is a package: **xserver-xorg-video-dummy**
i'm pretty sure that's what's used on servers, perhaps installing that might help you.

---

### Post by Rushed on 2018-03-29
It does it on both wayland and xorg. I'll check the package and see if it works !

---

### Post by Rushed on 2018-03-29
It does it on both wayland and xorg. 
unable to install video dummy
```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by kerry_s on 2018-03-29
> **Rushed said:**
> It does it on both wayland and xorg. 
unable to install video dummy
```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

make sure you don't have any app store or synaptic open, when trying to use terminal.

---

### Post by Rushed on 2018-03-31
I ran the command, restarted. Tried both in wayland and xorg and the pc still does it. I think i'll need to give up on wayland and xorg.

---

