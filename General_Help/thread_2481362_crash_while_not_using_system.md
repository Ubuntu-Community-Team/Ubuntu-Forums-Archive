---
title: "crash while not using system"
date: 2022-11-27
forum: General Help
---

### Post by fr33z0n3r on 2022-11-27
I'm experiencing some type of lockup when using my ubuntu 20.04 system.  There is a key hardware aspect I'll mention,  which is a hardware KVM is used for access to the device.  Now, the bright idea of not using the KVM simply isn't an option.  And I'm not sure why it would cause an issue, but this behavior did not start until I had a KVM in place.   Other systems (windows) do not crash after any period, so I consider this an OS bug. Hence why I'm posting here and not on the KVM vendors support line.


----
UPDATE:  I think this is the issue that is occurring, and it requires the latest kernel to address.   I am using amdgpu as my video driver.  As I have no idea what Canonical does for backporting kernel changes, anyone know if this could find its way to the latest 20.04 kernel channel?

UPDATE 2: This time the lockup happened I did not move away from the Ubuntu system. **So it is not related to the KVM switching anything.** REISUB works to reboot the system,  but Crtl-Alt-F1-6 do nothing.  Any ideas?

syslog snippet:
Nov 28 11:10:31 hostname kernel: [ 5700.313303] [drm] perform_link_training_with_retries: Link training attempt 1 of 4 failed
Nov 28 11:10:56 hostname kernel: [ 5724.962412] watchdog: BUG: soft lockup - CPU#13 stuck for 26s! [Xorg:2432]

[https://gitlab.freedesktop.org/drm/amd/-/issues/2029#note_1599579](https://gitlab.freedesktop.org/drm/amd/-/issues/2029#note_1599579)
----


Now,  when I'm on another computer on the KVM and try to return to ubuntu, it fails to re-connect to the ubuntu system.  There is a "re-connect" feature that fixed a similar issue, but it has oddly "returned".

I have 2 monitors connected, one on DP, and one on a USB-C (to DP) port. (again they both go to my kvm)

I was able to previously use a USB switch and change my monitor input to gain access to my ubuntu system.  But now with a new DP KVM,  it occasionally lockups and I hear the CPU whining.   Does this log tell the story?

I have an AMD Ryzen 7 5700U with Radeon Graphics

Here is a dump from journalctl


```

journalctl -b -1 -e

 Nov 27 12:52:00 hostname kernel:  ? wait_for_completion_timeout+0x1d/0x30Nov 27 12:52:00 hostname kernel:  ? commit_tail+0xc5/0x180 [drm_kms_helper]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_swap_state+0x20f/0x370>
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_commit+0x12b/0x150 [dr>
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_commit+0x4a/0x60 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_set_config+0x80/0xc0 [>
Nov 27 12:52:00 hostname kernel:  ? drm_mode_setcrtc+0x1ff/0x7d0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_mode_getcrtc+0x1e0/0x1e0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_ioctl_kernel+0xb2/0x100 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_ioctl+0x275/0x4a0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_mode_getcrtc+0x1e0/0x1e0 [drm]
Nov 27 12:52:00 hostname kernel:  ? amdgpu_drm_ioctl+0x4e/0x90 [amdgpu]
Nov 27 12:52:00 hostname kernel:  ? __x64_sys_ioctl+0x95/0xd0
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x5c/0xc0
Nov 27 12:52:00 hostname kernel:  ? syscall_exit_to_user_mode+0x27/0x50
Nov 27 12:52:00 hostname kernel:  ? __x64_sys_recvmsg+0x1f/0x30
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? syscall_exit_to_user_mode+0x27/0x50
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? entry_SYSCALL_64_after_hwframe+0x61/0xcb
Nov 27 12:52:00 hostname kernel:  </TASK>
Nov 27 12:52:00 hostname kernel: watchdog: BUG: soft lockup - CPU#10 stuck f>
lines 979-1001/1001 (END)
Nov 27 12:52:00 hostname kernel:  ? wait_for_completion_timeout+0x1d/0x30
Nov 27 12:52:00 hostname kernel:  ? commit_tail+0xc5/0x180 [drm_kms_helper]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_swap_state+0x20f/0x370 [drm_kms_helper]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_commit+0x12b/0x150 [drm_kms_helper]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_commit+0x4a/0x60 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_atomic_helper_set_config+0x80/0xc0 [drm_kms_helper]
Nov 27 12:52:00 hostname kernel:  ? drm_mode_setcrtc+0x1ff/0x7d0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_mode_getcrtc+0x1e0/0x1e0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_ioctl_kernel+0xb2/0x100 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_ioctl+0x275/0x4a0 [drm]
Nov 27 12:52:00 hostname kernel:  ? drm_mode_getcrtc+0x1e0/0x1e0 [drm]
Nov 27 12:52:00 hostname kernel:  ? amdgpu_drm_ioctl+0x4e/0x90 [amdgpu]
Nov 27 12:52:00 hostname kernel:  ? __x64_sys_ioctl+0x95/0xd0
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x5c/0xc0
Nov 27 12:52:00 hostname kernel:  ? syscall_exit_to_user_mode+0x27/0x50
Nov 27 12:52:00 hostname kernel:  ? __x64_sys_recvmsg+0x1f/0x30
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? syscall_exit_to_user_mode+0x27/0x50
Nov 27 12:52:00 hostname kernel:  ? do_syscall_64+0x69/0xc0
Nov 27 12:52:00 hostname kernel:  ? entry_SYSCALL_64_after_hwframe+0x61/0xcb
Nov 27 12:52:00 hostname kernel:  </TASK>
Nov 27 12:52:00 hostname kernel: watchdog: BUG: soft lockup - CPU#10 stuck for 1338s! [Xorg:2355]
~

```

---

### Post by TheFu on 2022-11-28
So, it appears the GPU-to-Monitor DRM code doesn't like losing connectivity.  If it were me, I'd blacklist the DRM code (assuming that's possible) and see if it doesn't help.
KVMs can be a wrench in the works, especially the more we ask them to do and if we use new-fangled connections.  I'd definitely unplug the USBc video connection too as part of testing.

---

### Post by fr33z0n3r on 2022-11-29
I have disabled the "Blank Screen" function in Ubuntu for now, which has stopped the hangs.  So it has nothing to do with the monitors changing or USB-C in use.  Just the Ubuntu functionality.

UPDATE: I'm testing without the USB-C cable in,  and so far it hasn't crashed.  8|

UPDATE 2: Was wrong, it still crashes.  So, only disabling the feature I mentioned fixes the issue. As a workaround.  So if anyone know how to connect to a system that falls into this state it is appreciated.  I'll look into setting up SSH access.  But this seems like an amdgpu kernel level issue.

---

### Post by fr33z0n3r on 2022-12-07
Can anyone give me direction on how to capture a bug report when the CPU is maxed due to Xorg process and a CPU softlock occurring?

---

### Post by TheFu on 2022-12-07
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
and
[https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en](https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en)
and
[https://ubuntu.com/blog/the-keys-to-successful-bug-reporting](https://ubuntu.com/blog/the-keys-to-successful-bug-reporting)
if you haven't seen those already.

---

### Post by fr33z0n3r on 2022-12-08
Yeah, it seems like my only choice is to copy paste log data I can find after the system reboots.

---

### Post by TheFu on 2022-12-08
> **fr33z0n3r said:**
> Yeah, it seems like my only choice is to copy paste log data I can find after the system reboots.

While I don't actually "know", I'd be surprised of the CLI bug reporting tool doesn't do that.

---

### Post by fr33z0n3r on 2022-12-08
I was able to use apport to update a bug I manually created.  so thats ok.  But there is likely some crash data I cannot get while it is happening.

---

### Post by TheFu on 2022-12-08
> **fr33z0n3r said:**
> I was able to use apport to update a bug I manually created.  so thats ok.  But there is likely some crash data I cannot get while it is happening.

journalctl will let you request issues from the prior boot.

```
$ journalctl -b 1
```

Also, for other errors, if you know the approximate time, journalctl can filter output to just those periods.

---

### Post by fr33z0n3r on 2022-12-09
Interestingly,  that doesn't come close to working, and says the last time I started my PC was back in February.  I reboot my pc numerous times a month.

update: Figured out the issue.  The correct command to look at last boot is:


```
$ journalctl -b -1
```

---

### Post by TheFu on 2022-12-09
Oops. Sorry.  

When I'm troubleshooting issues, I'll create a little script that looks for those issues over the last 10 reboots.  It has been over a year since I needed to do that - my systems have been very stable.  Of course, that doesn't help you get the correct command options.

---

