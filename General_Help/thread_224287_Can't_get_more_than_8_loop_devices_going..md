---
title: "Can't get more than 8 loop devices going."
date: 2006-07-27
forum: General Help
---

### Post by tommyrot on 2006-07-27
Hi folks,

I'm scratching my head a bit here, 'cos I've tried everything with my Ubuntu 5.10 distro to enable 64 loop devices to be available each time I boot.

I've tried adding options max_loop=64 in the /etc/modules file, but that doesn't make any difference, nor does it when I made the following change to the Kernel line in grub's menu.lst:

/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro max_loop=64 quiet splash

I also made the change in /dev/MAKEDEV so that it reads:

loop)
for part in `seq 0 63`
do
        makedev loop$part b 7 $part b 7 $part $disk
done
;;


Then I ran "MAKEDEV loop", which populated the /dev/loop directory with my 64 devices.

The problem is that when I reboot, I only have 8 devices again.

I've looked at this from a couple of different angles, but I can't figure it out - I thought my (relatively) new kernel should have supported loop devices as loadable modules, but even when I try to change the kernel as per above it still doesn't stick.

Any help would be greatly appreciated.

Cheers,

Tom

---

