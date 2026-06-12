---
title: "unable to see devices in Nautilus and unable to mount external drives"
date: 2013-04-24
forum: General Help
---

### Post by rvboutin on 2013-04-24
Hi,
Until recently my install of Ubuntu 12.04LTS was working fine but I ran into trouble with my Windows partitions and restored it from a disk image I had. To be able to boot I had to restore grub by using Boot Repair from a Ubuntu USB.
I am not sure, but after that restore I think everything was still ok, then Ubuntu run automatic updates.
Problems started after that. When eve I connect a USB stick or my eSATA drive they do not mount automatically as before. The devices sections in Nautilus has also disappeared. I have tried to use the command mount /dev/<name of the partition> but it fails giving me a message <partition> is not in fstab.
This is extremely annoying as I used several USB drive and an eSATA drive frequently. Having to mount them manually everytime I plug/unplug is not a workable option, even if I managed to do it...
I have tried pretty much all solutions suggested in various forum (uninstall/purge nautilus, deleting ./nautilus folder, uninstall/reinstall[FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace] [/FONT]gvfs).
The command: sudo ps -e | grep gvfs-gdu-volume returns nothing on that computer.
I have even tried to restore an old image of my Ubuntu partition... and to my surprise the problem was still there!!! My only logic conclusions is that something is messed up at boot/MBR level that triggers something odd!
Any help or comment welcome...
Thanks
Rv

---

### Post by rvboutin on 2013-04-25
**update:** I have now restore the whole Hard Drive image with both Windows and Ubuntu partition from Sept. 2012, and strangely when I log in Ubuntu the problem is there!!! While it was not there when I made the hard drive image, nor few weeks ago!! I really don't understand!! I also noticed that Ubuntu on the USB drive installer is fine on firs load (I can see devices in Nautilus side bar), on further start it disappears too on the USB drive!! Could it be a hardware issue causing the problem in Ubuntu?
I am reinstalling the whole system (dual boot), I won't install any extra hardware, and see...
Cheers,
Rv

---

### Post by rvboutin on 2013-04-29
update:
I have reinstalled both Win7 and Ubuntu 12.04LTS. All problem gone... hope they won't happen again!! So annoying!

---

