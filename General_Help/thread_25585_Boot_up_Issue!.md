---
title: "Boot up Issue!"
date: 2005-04-10
forum: General Help
---

### Post by radl33t on 2005-04-10
Despite my searches, I've been unable to fix the following problems which have only occured with Ubuntu's lilo:

Upon booting the kernel from Lilo I get the boot dots for 2.5 lines (2+ minutes of boot time) before I get the "Bios Data Check Successful" and the kernel actually begins to load.

Loading Linux................................(x2.5 lines)... Bios Data Check Successful.

I've tried to use a nobd command line option, but it has no effect.

Addtionally I have the first 2 partitions dedicated to windows. hda1 boots XP and hda2 holds a FAT32 drive that should be visible to both OS. Lilo hides hda2 from WinXP.

lilo.conf reads something like:

other=/dev/hda1
label=Windows
table = /dev/hda

What's there to it? I'm somewhat certain a default lilo.conf worked fine with lilo + fedora/mandrake.

P.S. Don't even talk about grub, heh.

Thanks,

Josh

---

### Post by erkki70 on 2005-04-11
Hi,
If you could post your lilo.conf people might know where the prob comes from and could help better...

Cheers,
Erkki

---

### Post by arctic on 2005-04-11
yupp... no help without a lilo.conf.

---

### Post by radl33t on 2005-04-11
By Popular Demand! Pretty generic?


[FONT=Courier New]# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
boot=/dev/hda

root=/dev/hda3

bitmap=/boot/debianlilo.bmp
bmp-colors=1,,0;9,,0
bmp-table=106p,144p,2,9,144p
bmp-timer=514p,144p,6,8,0
install=bmp

map=/boot/map
	prompt
	timeout=100

vga=normal

default=Linux

image=/vmlinuz
	label=Linux
	read-only
	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
	initrd=/initrd.img.old

other=/dev/hda1
	label=Windows
	table = /dev/hda
[/FONT]

---

### Post by erkki70 on 2005-04-11
If passing the argument nobd at boot time doesn't work you could try setting the global flag ```
suppress-boot-time-BIOS-data
``` in lilo.conf, see 'man lilo.conf' for more info > **suppress-boot-time-BIOS-data**This global option suppresses the boot-time real mode collection of BIOS data on systems which hang on certain BIOS calls. It is equivalent to using the boot-time switch 'nobd'.This option defeats the disk volume recognition and BIOS device code detection features of LILO on systems with more than one disk. Thus the use of this option will produce a strong cautionary message, which cannot be suppressed.  but I guess adding this to your lilo.conf should do the trick.

Hope this helps.

Cheers,
Erkki

---

### Post by radl33t on 2005-04-17
Thanks, that did the trick. Any insight into my issue of windows not finding hda1 (FAT32) Partition Magic sees it as 'hidden', but can't fix this because LILO sets the hidden status on boot.

---

