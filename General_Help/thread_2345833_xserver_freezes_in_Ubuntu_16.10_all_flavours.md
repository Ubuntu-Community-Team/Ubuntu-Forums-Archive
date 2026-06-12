---
title: "xserver freezes in Ubuntu 16.10 all flavours"
date: 2016-12-08
forum: General Help
---

### Post by kecalcze on 2016-12-08
Hello my desktops freezes always in random time in **different** **ubuntu flawours** (currently using ubuntu gnone, it freezes in longer time). I only get it working with newest Fedora and wayland (but i dont want to use it), and then get crash after two days after instaling xwayland stuff. I still can login through ssh and most of the sevices like webserver etc. is still working.

I tracked down that **xorg process stuck in D state** so i cant kill him. In "/var/log/" i dont see any xorg logfile, which is bad. 

In syslog there is something like this n times:

> Dec  8 15:54:28 bivojPC kernel: [ 3263.854565] INFO: task Xorg:1705 blocked for more than 120 seconds.
Dec  8 15:54:28 bivojPC kernel: [ 3263.854573]       Not tainted 4.8.0-30-generic #32-Ubuntu
Dec  8 15:54:28 bivojPC kernel: [ 3263.854576] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec  8 15:54:28 bivojPC kernel: [ 3263.854580] Xorg            D ffff9bed65d9b958     0  1705   1703 0x00000004
Dec  8 15:54:28 bivojPC kernel: [ 3263.854587]  ffff9bed65d9b958 00ff9bed65025958 ffff9bed6d1e1c80 ffff9bed6af44740
Dec  8 15:54:28 bivojPC kernel: [ 3263.854592]  ffff9bed679d1510 ffff9bed65d9c000 ffff9bed65d9ba68 ffff9bed679d14f0
Dec  8 15:54:28 bivojPC kernel: [ 3263.854597]  0000000000000001 ffff9bed65025958 ffff9bed65d9b970 ffffffffa0495865
Dec  8 15:54:28 bivojPC kernel: [ 3263.854601] Call Trace:
Dec  8 15:54:28 bivojPC kernel: [ 3263.854610]  [<ffffffffa0495865>] schedule+0x35/0x80
Dec  8 15:54:28 bivojPC kernel: [ 3263.854670]  [<ffffffffc03beac4>] amd_sched_entity_push_job+0x74/0x110 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854675]  [<ffffffff9fcc7150>] ? wake_atomic_t_function+0x60/0x60
Dec  8 15:54:28 bivojPC kernel: [ 3263.854724]  [<ffffffffc03bf578>] amdgpu_job_submit+0x88/0xd0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854764]  [<ffffffffc038140a>] amdgpu_vm_bo_update_mapping+0x3ca/0x550 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854805]  [<ffffffffc0381714>] amdgpu_vm_bo_split_mapping+0x184/0x1d0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854846]  [<ffffffffc0382d23>] amdgpu_vm_clear_freed+0x83/0xc0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854884]  [<ffffffffc0371393>] amdgpu_gem_va_update_vm+0x193/0x1d0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854922]  [<ffffffffc03724f6>] amdgpu_gem_va_ioctl+0x236/0x2f0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854956]  [<ffffffffc0221da0>] drm_ioctl+0x200/0x4f0 [drm]
Dec  8 15:54:28 bivojPC kernel: [ 3263.854994]  [<ffffffffc03722c0>] ? amdgpu_gem_metadata_ioctl+0x1d0/0x1d0 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.855026]  [<ffffffffc035a04f>] amdgpu_drm_ioctl+0x4f/0x90 [amdgpu]
Dec  8 15:54:28 bivojPC kernel: [ 3263.855031]  [<ffffffff9fe47953>] do_vfs_ioctl+0xa3/0x610
Dec  8 15:54:28 bivojPC kernel: [ 3263.855034]  [<ffffffffa03611d0>] ? __sys_recvmsg+0x80/0x90
Dec  8 15:54:28 bivojPC kernel: [ 3263.855038]  [<ffffffff9fe47f39>] SyS_ioctl+0x79/0x90
Dec  8 15:54:28 bivojPC kernel: [ 3263.855042]  [<ffffffffa049a076>] entry_SYSCALL_64_fastpath+0x1e/0xa8


Temperature of the gpu is around 40 - 50 °C and i dont see any connection with the freezes.

My rig is:

FX-6100
8B RAM
Sapphire Radeon RX480 NITRO+
2 displays connected via HDMI

Had anyone an idea how to sort it out?

---

### Post by Jeroen_Mathon on 2016-12-08
Hey [**[COLOR=#000000]kecalcze[/COLOR]**]("https://ubuntuforums.org/member.php?u=1874623"),

For what i have heard, 16.10 is not as stable as 16.04 yet.
Ubuntu has only recently started to adopt Wayland, So bugs and problems like these are bound to happen.

My recommendation is to jump to the latest LTS release abd report this bug in launchpad.

---

### Post by kecalcze on 2016-12-08
I tried bare ubuntu 16.04 before and it freezes too. I can try to install ubuntu gnome LTS and install amd-gpupro. Maybe it helps.

---

### Post by kecalcze on 2016-12-08
Ok, still the same problem with ubuntu gnome 16.04 w/wo amd-gpupro drivers. I am going to report a bug and if anyone khow how to fix it let me know. Thx :)

---

### Post by Jeroen_Mathon on 2016-12-09
What GPU and drivers do you have?

---

### Post by kecalcze on 2016-12-09
GPU is SAPPHIRE NITRO+ RADEON RX 480 8G GDDR5 
and now i am using amdgpu-pro drivers [http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx)

On ubuntu gnome 16.10 with amdgpu driver (its already built in new kernels) system hangs too

---

