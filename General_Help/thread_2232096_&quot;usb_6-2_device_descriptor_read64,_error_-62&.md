---
title: "&quot;usb 6-2: device descriptor read/64, error -62&quot; &amp; a lot more like it slow boot to a c"
date: 2014-06-29
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-06-29
The external usb drive (Western Dig., 500 Go) I was booting from was attacked & killed by a glass of milk. All my system backups, except 1 not-quite-functional Blacklabs (Remastersys fork) live-disk/installer on which the installer part doesn't work, were on another partition of the same drive, because I kept putting off shelling out for another drive, so now I have a new Toshiba external usb 1 To hard drive. I installed 14.04 from scratch with the mini.iso, trying the amd64 version this time (I've was using the 32 bit version, having had less problems with those in the past, despite 64 bit hardware). Then adding xorg, openbox, thunar, lxterminal, vim, gedit, synaptic, vlc, mirage, firefox, etc. to build pretty much the same system I had before, except in 64 bit. Except for the Nvidia driver. I can't find any Nvidia drivers in the 64 bit repositories. The Blacklabs live disk works fine as a live disk, even though ubiquity fails. So I booted from it and copied some config files over to the hard drive installation. I doubt those files are the problem, but it's concievable, so I mention it. It looks more like 14.04 (or maybe the bios) doesn't like my new Toshiba as much as it did my late WD. The system seems to work ok once booted, but it takes WAY too long to boot. Here is the part of dmesg that reflects what I see on the monitor (I changed "quiet splash" to "" in grub) when booting slows
to a snail's pace:```
[   28.533298] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   31.428846] usb 6-2: new full-speed USB device number 29 using ohci-pci
[   31.569036] usb 6-2: device descriptor read/64, error -62
[   43.292478] usb 6-2: new full-speed USB device number 34 using ohci-pci
[   43.432573] usb 6-2: device descriptor read/64, error -62
[   44.845775] usb 6-2: new full-speed USB device number 36 using ohci-pci
[   44.985899] usb 6-2: device descriptor read/64, error -62
[   45.802577] usb 6-2: new full-speed USB device number 37 using ohci-pci
[   45.942696] usb 6-2: device descriptor read/64, error -62
[   50.670615] usb 6-2: new full-speed USB device number 45 using ohci-pci
[   50.810762] usb 6-2: device descriptor read/64, error -62
[   51.564079] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:ec:1a:59:3d:dc:8e:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=50240 PROTO=2 
[   54.609933] usb 6-2: new full-speed USB device number 51 using ohci-pci
[   62.480509] usb 6-2: new full-speed USB device number 64 using ohci-pci
[   69.778603] usb 6-2: new full-speed USB device number 76 using ohci-pci
[   71.684188] usb 6-2: new full-speed USB device number 79 using ohci-pci
[   73.017312] usb 6-2: new full-speed USB device number 81 using ohci-pci
[   73.157428] usb 6-2: device descriptor read/64, error -62
[   73.401632] usb 6-2: device descriptor read/64, error -62
[   73.641834] usb 6-2: new full-speed USB device number 82 using ohci-pci
[   73.781941] usb 6-2: device descriptor read/64, error -62
[   74.026139] usb 6-2: device descriptor read/64, error -62
[   74.266335] usb 6-2: new full-speed USB device number 83 using ohci-pci
[   74.674677] usb 6-2: device not accepting address 83, error -62
[   74.810810] usb 6-2: new full-speed USB device number 84 using ohci-pci
[   75.219195] usb 6-2: device not accepting address 84, error -62
[   75.219451] hub 6-0:1.0: unable to enumerate USB device on port 2

```If anyone has any ideas on fixing this I'd appreciate a pointer. What I'm comtemplating now is:
1- Format over this & start over with the 32 bit version.
2- Reboot with my live disk version of one of my old systems and copy all of its directories that might have config files, scripts, or anything that might be salvagable TO A DATA PARTITION. 
3- Reboot into the new system and try salvaging stuff a little bit at a time, cautiously.

But I'd love to hear a better idea.

Thanks for reading.
NOTE:
I reposted a more succint version of this, with a better chosen title, in Hardware, which seemed a better place for it:
[http://ubuntuforums.org/showthread.php?t=2232381&p=13063278#post13063278](http://ubuntuforums.org/showthread.php?t=2232381&p=13063278#post13063278)
Solved. See other thread if you have a similar problem.

---

### Post by Dreamer Fithp Apprentice on 2014-07-13
A post to take this out of the "unanswered" list.

---

### Post by Dreamer Fithp Apprentice on 2014-07-13
A post to take this out of the "unanswered" list.

---

