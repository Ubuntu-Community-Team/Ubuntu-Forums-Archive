---
title: "Crash Lockup Chrome Firefox Bluetooth Video Audio Memory Issue"
date: 2016-11-11
forum: General Help
---

### Post by tortugatorben on 2016-11-11
I have a recurring issue with Ubuntu 16.04LTS

If I open up Chrome ([COLOR=#303942][FONT=Ubuntu]54.0.2840.100 (64-bit)[/FONT][/COLOR]) and Firefox (49.0.2) simultaneously and have, say, five tabs open each, over time I'll get grayscreened and my laptop will lock up. I have to do a hard restart (hold down power button) or it never recovers. It doesn't usually crash by itself (but sometimes, where it resets to the login screen), but it always locks up. This happens several times a day. Often it seems associated with a tab that gets open and has video or audio associated with it. Additionally, and I believe it's related, when I use the laptop to stream audio to a Bluetooth speaker and video is associated (Youtube or similar) it starts to lag after a few minutes so the video and audio are offset by several seconds, then it locks up. And I have to, yet again, do a hard reset.

It's somewhat annoying that I have an old Android phone that will stream audio and video perfectly to my Bluetooth speakers, and that I can run two different browsers simultaneously on it as well, with no crashing or locking up. I'm doing it right now actually, as I type this.

I feel like, perhaps, this is a memory issue. I installed Gnome task manager to see what was going on and it looks like Ubuntu has a difficult time dealing with memory and cache. I currently have only Firefox, Chrome and Task Manager open and TM reports 65% memory usage (no video, 5 tabs each). CPU usage is fluctuating between 3 and 12%. If I hit up a video or turn on VLC, in a matter of ten to fifteen minutes this machine will lock up. When I recreate this on Windows or Mac machines, no crashing. Bluetooth works like a champ. This is using similar hardware of course, not the exact same however.

What I'm running:
3.5 GiB Memory
Intel Core i7-3667U CPU @ 2.00GHz x 4
Intel Ivybridge Moble (Graphics)
OS type 64-Bit
Disk 122 GB

It's a First Generation Lenovo X1 Carbon

It originally came with Windows 7 pre-installed. I had installed Ubuntu 14.04 (dual install or ran it from a flash drive to play with it) and had a few issues, but nothing major. Windows worked fine, no issues as described above.

Any thoughts on how to get Ubuntu to use memory more efficiently and possibly the cache as well? Not sure why the system reports 3.5 GiB memory...Terminal reports the following:

```
sudo lshw -class memory
  *-cache:0               
       description: L1 cache
       physical id: 3
       slot: L1-Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: internal write-through instruction
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 4
       slot: L2-Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: internal write-through unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 5
       slot: L3-Cache
       size: 4MiB
       capacity: 4MiB
       capabilities: internal write-back unified
       configuration: level=3
  *-cache
       description: L1 cache
       physical id: 2
       slot: L1-Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: internal write-through data
       configuration: level=1
  *-memory
       description: System Memory
       physical id: 7
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: Chip DDR3 Synchronous 1333 MHz (0.8 ns)
          product: HMT42556MFR6A-G7
          vendor: Hynix/Hyundai
          physical id: 0
          serial: None
          slot: ChannelA
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: Chip DDR3 Synchronous 1333 MHz (0.8 ns)
          product: HMT42556MFR6A-G7
          vendor: Hynix/Hyundai
          physical id: 1
          serial: None
          slot: ChannelB
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
  *-firmware
       description: BIOS
       vendor: LENOVO
       physical id: c
       version: G6ETA7WW (2.67 )
       date: 06/12/2014
       size: 128KiB
       capacity: 11MiB
       capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification uefi
```

Thanks in advance for any help.

---

