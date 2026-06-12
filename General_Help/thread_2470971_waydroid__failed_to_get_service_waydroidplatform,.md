---
title: "waydroid : failed to get service waydroidplatform,"
date: 2022-01-18
forum: General Help
---

### Post by tymop on 2022-01-18
Hello,
I'm trying to install and use  waydroid.

I think the installation was good, but now, it does not work. This is what I see:

[LIST=1]
[*]waydroid show-full-ui give me :  [18:46:11] Starting waydroid session but nothing appear on screen (I expected something)
but I can see some errors in /var/lib/waydroid/waydroid.log:  ```
(008316) [18:46:11] Starting waydroid session
(008316) [18:46:11] Save session config: /var/lib/waydroid/session.cfg
(008316) [18:46:11] UserMonitor service is not even started
(008316) [18:46:11] Clipboard service is not even started
(005677) [18:46:11] % /usr/lib/waydroid/data/scripts/waydroid-net.sh start
waydroid-net is already running
(005677) [18:46:11] % umount /var/lib/waydroid/rootfs/vendor/waydroid.prop
(005677) [18:46:11] % umount /var/lib/waydroid/rootfs/vendor
(005677) [18:46:11] % umount /var/lib/waydroid/rootfs
(005677) [18:46:11] % mount /var/lib/waydroid/images/system.img /var/lib/waydroid/rootfs
(005677) [18:46:11] % mount -o remount,ro /var/lib/waydroid/images/system.img /var/lib/waydroid/rootfs
(005677) [18:46:11] % mount /var/lib/waydroid/images/vendor.img /var/lib/waydroid/rootfs/vendor
(005677) [18:46:11] % mount -o remount,ro /var/lib/waydroid/images/vendor.img /var/lib/waydroid/rootfs/vendor
(005677) [18:46:11] % mount -o bind /var/lib/waydroid/waydroid.prop /var/lib/waydroid/rootfs/vendor/waydroid.prop
(005677) [18:46:11] % umount -l /sys/fs/cgroup/schedtune
umount: /sys/fs/cgroup/schedtune: Aucun point de montage indiqué.
(005677) [18:46:11] % chmod 777 -R /dev/ashmem
(005677) [18:46:11] % chmod 777 -R /sys/kernel/debug/sync/sw_sync
(005677) [18:46:11] % chmod 777 -R /dev/dri
(005677) [18:46:11] % chmod 777 -R /dev/fb0
(005677) [18:46:11] % lxc-start -P /var/lib/waydroid/lxc -F -n waydroid -- /init
(005677) [18:46:11] New background process: pid=8351, output=background
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
(005677) [18:46:12] Save session config: /var/lib/waydroid/session.cfg
lxc-start: waydroid: conf.c: run_buffer: 314 Script exited with status 126
lxc-start: waydroid: start.c: lxc_end: 958 Failed to run lxc.hook.post-stop for container "waydroid"

``` 
[*]then in a second terminal :  waydroid app list ```
Failed to get service waydroidplatform, trying again...
``` 
[/LIST]


then, I close all, and in a terminal, I start "waydroid session start". then in a second terminal :  waydroid app list ```
Failed to get service waydroidplatform, trying again...
```
"waydroid status" give ```
Session:    RUNNING
Container:    RUNNING
Vendor type:    MAINLINE
Session user:    tymop(1000)
Wayland display:    wayland-0

```
I am not sure I use it correctly, but I think there is something wgong (due to error messages in waydroid.log).

NB : I use Ubuntu 21.04
echo $XDG_SESSION_TYPE = wayland


Can somebody help me please.

---

### Post by tymop on 2022-01-19
I removed all, and I followed [https://github.com/aditya24raj/darth_waydr](https://github.com/aditya24raj/darth_waydr)
 I think nothing change.
 this is the log when i launch waydroid-start-full
 ```
(027238) [18:00:23] WayDroid session is not started
(027240) [18:00:23] WayDroid container is STOPPED
(027245) [18:00:23] Starting waydroid session
(027245) [18:00:23] Save session config: /var/lib/waydroid/session.cfg
(027245) [18:00:23] UserMonitor service is not even started
(027245) [18:00:23] Clipboard service is not even started
(004893) [18:00:24] % /usr/lib/waydroid/data/scripts/waydroid-net.sh start
waydroid-net is already running
(004893) [18:00:24] % umount /var/lib/waydroid/rootfs/vendor/waydroid.prop
(004893) [18:00:24] % umount /var/lib/waydroid/rootfs/vendor
(004893) [18:00:24] % umount /var/lib/waydroid/rootfs
(004893) [18:00:24] % mount /var/lib/waydroid/images/system.img /var/lib/waydroid/rootfs
(004893) [18:00:24] % mount -o remount,ro /var/lib/waydroid/images/system.img /var/lib/waydroid/rootfs
(004893) [18:00:24] % mount /var/lib/waydroid/images/vendor.img /var/lib/waydroid/rootfs/vendor
(004893) [18:00:24] % mount -o remount,ro /var/lib/waydroid/images/vendor.img /var/lib/waydroid/rootfs/vendor
(004893) [18:00:24] % mount -o bind /var/lib/waydroid/waydroid.prop /var/lib/waydroid/rootfs/vendor/waydroid.prop
(004893) [18:00:24] % umount -l /sys/fs/cgroup/schedtune
umount: /sys/fs/cgroup/schedtune: Aucun point de montage indiqué.
(004893) [18:00:24] % chmod 777 -R /dev/ashmem
(004893) [18:00:24] % chmod 777 -R /sys/kernel/debug/sync/sw_sync
(004893) [18:00:24] % chmod 777 -R /dev/dri
(004893) [18:00:24] % chmod 777 -R /dev/fb0
(004893) [18:00:24] % lxc-start -P /var/lib/waydroid/lxc -F -n waydroid -- /init
(004893) [18:00:24] New background process: pid=27283, output=background
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
tail: impossible de surveiller '/var/lib/waydroid/waydroid.log': Permission non accordée
(004893) [18:00:24] Save session config: /var/lib/waydroid/session.cfg
lxc-start: waydroid: conf.c: run_buffer: 314 Script exited with status 126
lxc-start: waydroid: start.c: lxc_end: 958 Failed to run lxc.hook.post-stop for container "waydroid"

```                          

 I am wondering what is the meaning of the 2 last lines, and if this may be the cause ..?

also, the command "sudo waydroid logcat"
[19:10:01] WayDroid container is STOPPED

but I see that in systemctl
waydroid-container.service                                                                loaded active running 

 "waydroid status" give this result
 Session:    RUNNING
Container:    RUNNING
Vendor type:    MAINLINE
Session user:    tymop(1000)
Wayland display:    wayland-0

---

