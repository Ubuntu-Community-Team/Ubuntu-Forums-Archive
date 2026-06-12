---
title: "Failed to unmount /oldroot"
date: 2021-07-12
forum: General Help
---

### Post by klundermann on 2021-07-12
Every time I shut my 20.04 LTS installation down, I see the error messages like the following:

```
sd-unmoun[10790]: Failed to unmount /oldroot: Device or resource busy
sd-unmoun[10791]: Failed to unmount /oldroot/dev/pts: Device or resource busy
sd-unmoun[10792]: Failed to unmount /oldroot/dev: Device or resource busy
shutdown[1]: Failed to finalize  file systems, ignoring
```

Until recently, I simply did not worry about this.  Then a boot-up failed one day, with a message telling me to run [FONT=system]fsck[/FONT].  Doing so seems to have solved the problem, but some threads I read suggest that the problem arose in the first place because of an improper shutdown.  Therefore, I have decided to worry to about the error messages above.

I boot from an SSD, in case that's relevant.  My directory structure does *not* have an [FONT=system]/oldroot[/FONT] directory.

Would anybody be able to help me figure out what's going on here and how to avoid the errors?

---

### Post by TheFu on 2021-07-13
Well, /oldroot is somewhere in your configs, so find that and remove it.  I'd look in /etc/fstab first.

---

### Post by klundermann on 2021-07-13
Thank you, TheFu.

Searching first /etc and then its subdirectories, I found oldroot in the middle of the following code snippet from /etc/apparmor.d/usr.lib.snapd.snap-confine.real:

```

    # pivot_root mediation in AppArmor is not complete. See LP: #1791711.
    # However, we can mediate the new_root and put_old to be what we expect,
    # and then deny directory creation within old_root to prevent trivial
    # pivoting into a whitelisted path.
    pivot_root oldroot=/tmp/snap.rootfs_*/var/lib/snapd/hostfs/ /tmp/snap.rootfs_*/,
    # Explicitly deny creating the old_root directory in case it is
    # inadvertently added somewhere else. While this doesn't resolve
    # LP: #1791711, it provides some hardening.
    audit deny /tmp/snap.rootfs_*/{var/,var/lib/,var/lib/snapd/,var/lib/snapd/hostfs/} w,
```

[FONT=system][FONT=arial][FONT=system][FONT=arial]Unfortunately, now that I've found oldroot, I'm at a bit of a loss as to what to do about it.
[/FONT][/FONT][/FONT][/FONT]
If anyone has a suggestion, I'm all ears...!

---

### Post by TheFu on 2021-07-13
Why not just delete all the snap packages? They are not mandatory, just convenient for a few programs.

---

### Post by gerry-q on 2021-10-01
I have the same issue and your code is also found on my PC.  Sorry I can't offer advice but I post this so that I will hopefully receive notification if anyone else suggests how to resolve the issue.

---

### Post by daniel-marynicz on 2021-12-23
I resolved this
 i created
 file
```
/etc/systemd/system/kill-plymouthd.service
```
with
```

[Unit]Description=kill plymouthd
After=umount.target
DefaultDependencies=false


[Service]
Type=oneshot
ExecStart=/usr/bin/pkill plymouthd


[Install]
WantedBy=final.target



```
file (can be omitted if you do not have nvidia drivers)
```
/etc/systemd/system/rm-nvidia.service
```
```

[Unit]
Description=rm nvidia modules
After=umount.target
DefaultDependencies=false


[Service]
Type=oneshot
ExecStart=/usr/sbin/rmmod nvidia_uvm
ExecStart=/usr/sbin/rmmod nvidia_drm
ExecStart=/usr/sbin/rmmod nvidia_modeset
ExecStart=/usr/sbin/rmmod nvidia
ExecStart=/usr/sbin/rmmod i2c_nvidia_gpu


[Install]
WantedBy=final.target

```

Execute:
```

[COLOR=#333333][FONT=monospace]sudo systemctl daemon-reload[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo systemctl enable rm-nvidia.service[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo systemctl enable kill-plymouthd.service[/FONT][/COLOR]

```

i you need debug this you can install finalrd. 
and create executable

```
/etc/finalrd/sleep.finalrd
```
```
#!/bin/sh

set -x


if [ "$1" = "setup" ]
then
    . /usr/share/initramfs-tools/hook-functions


    copy_exec /usr/bin/sleep
       copy_exec /usr/bin/mount    


    exit 0
fi    

# your debug script
mount
sleep 30



``` 

I have one ubuntu system without nvidia drivers and for this system I just needed to create kill-plymouthd.service for the system with nvidia drivers I needed
rm-nvidia.service, kill-plymouthd.service

---

