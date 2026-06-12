---
title: "Random Crashing"
date: 2004-11-09
forum: General Help
---

### Post by Enygma on 2004-11-09
Hey, 

I've had ubuntu running fairly smoothly now for a few weeks. Lately, however it's started crashing randomly. i.e. I'll be browsing a website and BAM, Firefox is just gone, or X restarts.
This can happen at any time. 

I thought this may have been because I was running the inotify patched kernel so I switched back to the default ubuntu kernel and I'm still getting them.

Where should I look for clues as to what's happening?
I noticed in /var/log/messages that something is receiving a 'signal 15' (posting from memory, in work atm) I can post the contents of that later. 

Thanks

---

### Post by rrijkse on 2004-11-09
I am having the exact same problem and I haven't changed the kernel or anything, except for adding some programs, but now Firefox keeps crashing when I do anything outside of looking at websites.

I have had this problem before and solved it by re-installing and then restoring my settings, but I don't want to keep doing this.

If anyone has any ideas please post them.

- Robbert

---

### Post by Enygma on 2004-11-09
Just wondering what chip you've got?
I've got a P4 with HT but I'm not running an SMP kernel. 
Would this make any difference?

---

### Post by Enygma on 2004-11-09
It just happened me there now again, 
here's the output from /var/log/messages

```

Nov  9 19:38:19 localhost -- MARK --
Nov  9 19:58:19 localhost -- MARK --
Nov  9 19:58:31 localhost gconfd (psb-4202): Received signal 15, shutting down cleanly
Nov  9 19:58:31 localhost gconfd (psb-4202): Exiting
Nov  9 19:58:33 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Nov  9 19:58:33 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 16x mode
Nov  9 19:58:33 localhost kernel: agpgart: SiS delay workaround: giving bridge time to recover.
Nov  9 19:58:33 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 16x mode
Nov  9 19:58:33 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Nov  9 19:58:33 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 16x mode
Nov  9 19:58:33 localhost kernel: agpgart: SiS delay workaround: giving bridge time to recover.
Nov  9 19:58:33 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 16x mode
Nov  9 19:58:41 localhost gconfd (psb-5918): starting (version 2.8.1), pid 5918 user 'psb'
Nov  9 19:58:41 localhost gconfd (psb-5918): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  9 19:58:41 localhost gconfd (psb-5918): Resolved address "xml:readwrite:/home/psb/.gconf" to a writable configuration source at position 1
Nov  9 19:58:41 localhost gconfd (psb-5918): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

```

---

### Post by Enygma on 2004-11-09
I looked around a few forums and it seems this is the way to fix it. In /boot/grub/menu.lst change this line:
```

kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash

```

to this:

```

kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash noapic noacpi

```

I haven't had any crashes since the last post anyway which is good going compared to earlier. Hope this is of some help to you.

---

### Post by sb73542 on 2004-11-09
[QUOTE=Enygma]Just wondering what chip you've got?
I've got a P4 with HT but I'm not running an SMP kernel. 
Would this make any difference?[/QUOTE]

I don't think so.  I have noticed this same problem with virtually all Linux distros with 2.4.x and 2.6.x kernels, some using KDE, and I have an AMD K6-II 300 MHz CPU.  I don't use apic or acpi either, so I don't think that's causing the crashes.  X is just plain unstable.  I wish it was predictable when it would crash, but as mentioned, it appears to be totally random.

---

### Post by Enygma on 2004-11-10
I've never had this problem before and I've been using X for about 6 years now.
Also I was running Ubuntu for about two weeks before these crashes started to occur.

Since I've added those parameters to the kernel it seems to be much more stable than before, I still haven't had a 'Signal 15' crash.

---

### Post by sb73542 on 2004-11-10
Must be a crummy video driver for my card, SiS 6326.  I've been using Linux for two years (all on the same computer), and I've found that almost all distros I've tried crash too often to be used for anything production.  PCLOS seems quite free of random crashes, though.

---

### Post by Enygma on 2004-11-15
Sorry for dragging up this old thread but I think I've traced the root of the problem down to a dodgy hard drive.  Thought it was my new 160G so I installed on the old 20G by itself and planned to add the 160 later but it was crashing more often than ever. Tried to install onto the 160G with both drives in but I couldn't format. 

Working fine on the new drive now.

---

### Post by FLeiXiuS on 2004-11-15
Lets see what X has to say about this...

tail -f /var/logs/XFree*

---

