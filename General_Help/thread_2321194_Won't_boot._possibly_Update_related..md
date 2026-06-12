---
title: "Won't boot. possibly Update related."
date: 2016-04-21
forum: General Help
---

### Post by shannon5 on 2016-04-21
I was in the middle of installing some updates on my desktop. The update crashed multiple times. I decided to reboot.  System hung while trying to reboot and I had to do a hard-reset.

GRUB comes up and no matter which option I select I end up with a black screen and a flashing cursor at the top.

I booted from a recovery USB.  Reinstalled GRUB.  No effect.
Booted from recovery USB.  Went to command line with : Ctrl-Alt-F1

Mounted my old file system like this: 

[LIST=1]
[*=left][FONT=inherit]sudo mount /dev/sda1 /mnt[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /dev /mnt/dev[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /proc /mnt/proc[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /sys /mnt/sys[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo chroot /mnt

Attempted to run apt upgrade.
Upgrades download and then the process fails with the following error:

Invalid argument: -c
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (255)
E: Failure running script /usr/sbin/dpkg-preconfigure -apt || true

Every single thing from this point involving apt-get gives me an error involving 'Invalid argument: -c' and a different script failing.

apt-get update <does update and then...>
Invalid argument: -c  
E: Problem executing scripts APT::Update::Post-Invoke-Success 'touch /var/lib/apt/periodic/update-success-stamp 2> /devnull ||true'
E: Sub-process returned an error code

Have tried removing packages, punching the wall, screaming and violence.  The first gave a similar error starting with 'Invalid argument: -c', the others all resulted in my girlfriend threatening to leave.

Please help...[/FONT]
[/LIST]

---

### Post by Cavsfan on 2016-04-21
> **shannon5 said:**
> I was in the middle of installing some updates on my desktop. The update crashed multiple times. I decided to reboot.  System hung while trying to reboot and I had to do a hard-reset.

GRUB comes up and no matter which option I select I end up with a black screen and a flashing cursor at the top.

I booted from a recovery USB.  Reinstalled GRUB.  No effect.
Booted from recovery USB.  Went to command line with : Ctrl-Alt-F1

Mounted my old file system like this: 

[LIST=1]
[*=left][FONT=inherit]sudo mount /dev/sda1 /mnt[/FONT] 
[*=left][FONT=inherit]sudo mount --bind /dev /mnt/dev[/FONT] 
[*=left][FONT=inherit]sudo mount --bind /proc /mnt/proc[/FONT] 
[*=left][FONT=inherit]sudo mount --bind /sys /mnt/sys[/FONT] 
[*=left][FONT=inherit]sudo chroot /mnt

Attempted to run apt upgrade.
Upgrades download and then the process fails with the following error:

```
Invalid argument: -c
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (255)
E: Failure running script /usr/sbin/dpkg-preconfigure -apt || true
```

Every single thing from this point involving apt-get gives me an error involving 'Invalid argument: -c' and a different script failing.

apt-get update <does update and then...>
```
Invalid argument: -c  
E: Problem executing scripts APT::Update::Post-Invoke-Success 'touch /var/lib/apt/periodic/update-success-stamp 2> /devnull ||true'
E: Sub-process returned an error code
```

Have tried removing packages, punching the wall, screaming and violence.  The first gave a similar error starting with 'Invalid argument: -c', the others all resulted in my girlfriend threatening to leave.

Please help...[/FONT] 
[/LIST]


Perhaps this might help: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

