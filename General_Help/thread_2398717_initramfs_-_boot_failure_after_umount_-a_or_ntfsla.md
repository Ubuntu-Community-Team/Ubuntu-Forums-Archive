---
title: "initramfs - boot failure after umount -a or ntfslabel?"
date: 2018-08-16
forum: General Help
---

### Post by thecowbell on 2018-08-16
[COLOR=#242729][FONT=Arial]Hi,

I connected a USB drive to my xbmc/ubuntu system and as it was named "New Volume" I tried to change the label using ntfslabel. As I'm a newbie when it comes to linux and hardware I stumbled around a bit, ran 'umount -a' and also tried to format the new disk with "mkdosfs -F 32 -I /dev/sdc3"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]At some point I was getting strange results so did a reboot and now I'm staring at:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Gave up waiting for root device. etc etc. (initramfs)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Obviously I hosed something, but I thought since I was only messing with an empty USB drive I would be ok. I removed the USB drive, rebooted, and I'm still seeing this message.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any help would be greatly appreciated, I'm hoping there's a simple way to get back in business.[/FONT][/COLOR]

---

### Post by thecowbell on 2018-08-16
Quick update - turns out my actions were a total red herring.

One of my 4 Western Digital drives has apparently gone bad. If I unplug it the system boots fine.  With it plugged in I go right to initramfs shell.

Seems odd....

Anyways - I connected the problem drive to a separate windows machine and it shows up in disk management as 'healthy' with uninitialized space. Has anyone had anything like this happen? I'd like to use the linux machine to scan the disk but I apparently can't boot with it plugged in ... 

My guess is I need to edit that drive in fstab, then I can boot with it plugged in, is that accurate? Any other hints or tips on how to deal with this poison pill drive before chucking it in the trash for good?

---

