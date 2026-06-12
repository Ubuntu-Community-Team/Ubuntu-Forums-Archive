---
title: "Honestly don't know where to start."
date: 2019-11-17
forum: General Help
---

### Post by Kehlan_Rutan on 2019-11-17
My computer was working fine earlier today. Then all of a sudden one of my monitors went out. I tried to open settings and it failed to open.  So I ran it through the terminal and got this:
```
sudo gnome-control-center
error: XDG_RUNTIME_DIR not set in the environment.
**
ERROR:../shell/cc-shell-model.c:458:cc_shell_model_set_panel_visibility: assertion failed: (valid)
Bail out! ERROR:../shell/cc-shell-model.c:458:cc_shell_model_set_panel_visibility: assertion failed: (valid)

Aborted


```

So then I just restarted my computer.  When I did that it booted but just sat on the Ubuntu loading screen and spun forever.  So I restarted again with Advanced Options and went into recovery mode.  And selected to restore damaged packages.  And seemed to work.  Was able to boot into Ubuntu, but Settings still won't launch. 
I have tried to uninstall and reinstall gnome-control-center and it leads to the same error.  And also, when I reboot again, it is the same recycle of spinning, then needing to restore damaged packages in order for me to boot in.  

Please help. This is on Ubuntu 19.10

---

### Post by Kehlan_Rutan on 2019-11-18
Haven't figured this out yet.  Or even what the problem is.  Since it is  affecting start up, Gnome Control Center and possible a monitor.  Just  restarted now and downloaded the log files.  Maybe this will be some  insight to someone. I'll start working through these and trying to  resolve them one by one, skipping the plex error, because I was able to  manually start it.  But I will take it off start up apps so it doesn't  get error anymore. 

16:15:56 systemd: Failed to start Plex Media Server.
16:15:35 avahi-daemon: chroot.c: open() failed: No such file or directory
16:15:35 (sd-executor): /usr/lib/systemd/system-generators/friendly-recovery failed with exit status 1.
16:15:27 kernel: hdaudio hdaudioC0D3: Unable to bind the codec
16:14:26 systemd: Failed to start NVIDIA Persistence Daemon.

---

### Post by 0x656b694d on 2019-11-27
All of a sudden? Corrupted file system? I'd try to boot from a live image to check the hardware. But first of all I'd backup all the important data, of course.
Then I'd reinstall the system over, taking care of not overriding /home.

---

