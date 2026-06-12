---
title: "Dual Booting 2 Separate Hard Drives"
date: 2007-03-02
forum: General Help
---

### Post by v8YKxgHe on 2007-03-02
Hey,

I have Ubuntu and Windows installed of separate had drives, for now I've just been taking the power out of the hard drive I don't want to boot into, and putting it in the other. This is getting kind of annoying now so I am wondering how I would setup GRUB so I can dual-boot Windows and Ubuntu from different hard drives.

Here is the output from "sudo fdisk -l"

```
alex@alex-ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/hda5               2        9964    80027766    b  W95 FAT32

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

```

hda = 80GB FAT 32 Storage Hard drive (No Windows)
sda = Ubuntu
sdb = Windows.

Any help would be great, thanks!

---

### Post by Shatrat on 2007-03-02
What is in your /boot/grub/menu.list right now?

---

### Post by v8YKxgHe on 2007-03-02
Here it is:

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

```

---

### Post by Shatrat on 2007-03-02
Ok, add to that;
```
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```
and if that doesnt work, try again with root   (hd2,0)

---

### Post by raevin on 2007-03-02
> **Shatrat said:**
> Ok, add to that;
```
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```
and if that doesnt work, try again with root   (hd2,0)

Won't work, since Windows has to be faked into being the first hard drive (hd0).

Here's how I did it...

```

title Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

```

the two map lines essentially does a hard drive swap, which tricks Windows into thinking it's the first hard drive and everything...

Obviously change hd0 and hd1 to sda and sdb and stuff...

(Just a note of reference, the above code I gave, hd0 is my Ubuntu...with hd1 being my Windows)

---

### Post by v8YKxgHe on 2007-03-02
I see, so I replace hd0 with sda? That's what I got confused about as it's hd0 <- Number, whereas with mine is sda <- Letter. Ok, I'll try that now, hopefully it works!

---

### Post by raevin on 2007-03-02
> **AlexC_ said:**
> I see, so I replace hd0 with sda? That's what I got confused about as it's hd0 <- Number, whereas with mine is sda <- Letter. Ok, I'll try that now, hopefully it works!

*nods*

I'm not sure if SCSI drives (I'm assuming that's what they are, given the sd-part) have numbers for partitions too, I'm assuming so, I've just have extremely small experience w/ SCSI in general.

---

### Post by v8YKxgHe on 2007-03-02
Nope, that didn't work. I get 

```
Error 23 - Error while parsing number
``` Maybe it should be sd1 and sd0 etc? I'll try that now

---

### Post by v8YKxgHe on 2007-03-02
If my main Ubuntu hard drive (sda) in Grub is 

```
root		(hd0,0)
``` then ... why am I entering sda instead of hd0 :S, well actually I tried that and got the same error.

---

### Post by raevin on 2007-03-02
> **AlexC_ said:**
> If my main Ubuntu hard drive (sda) in Grub is 

```
root		(hd0,0)
``` then ... why am I entering sda instead of hd0 :S, well actually I tried that and got the same error.

You wouldn't...because if "sudo fdisk -l" lists it as a sd* drive (ex: sda, sdb, etc...) you'd do sd[something].  When you get to the OS selection screen in GRUB, hit "c" (w/o quotes), and type in "geometry" w/o quotes.  Think you'll have to have like sda or something after that though (ex: "geometry sda").  If that doesn't work, then try "gemotry sd0"

---

### Post by v8YKxgHe on 2007-03-03
Hum ... When I did "geometry" in GRUB I got something like "Error 17: Unknown Device number" (not sure if that's the correct error, forgot to write it down). I tried everything and still got the same error.

---

### Post by ellis rowell on 2007-03-03
I solved this problem by buying a "Y" link for the power connector, a couple of metres each of red and yellow cable of the same thickness and a two pole two way switch. The switch has a 6mm screw fitting so a hole has to be drilled (probably in the front panel).

Cut the two yellow and the two red cables, bare 4mm on each end and solder a suitable length of the same colour cable onto the end of the "Plug" cables and insulate with tape. Then either cut one cable of each red and yellow of the "Socket" end or solder the two (same colour) together with another suitable length of cable. Solder the two (red and yellow) cables (extended cable) to the centre connectors of the switch, then solder the red and yellow from one plug to red and yellow contacts on one end of the switch. Do the same with plug leads of the other plug. The Black leads do not require modifying.

To switch from one system to the other. Close down the one you are using, switch over and boot up the other one. Any data files which are common to both systems should be saved onto a USB  HDD which is formatted to Fat32 (so it is available to Windoze as well as GNU/Linux).

---

### Post by daniloj on 2008-04-18
> **ellis rowell said:**
> I solved this problem by buying a "Y" link for the power connector, a couple of metres each of red and yellow cable of the same thickness and a two pole two way switch. The switch has a 6mm screw fitting so a hole has to be drilled (probably in the front panel).

Cut the two yellow and the two red cables, bare 4mm on each end and solder a suitable length of the same colour cable onto the end of the "Plug" cables and insulate with tape. Then either cut one cable of each red and yellow of the "Socket" end or solder the two (same colour) together with another suitable length of cable. Solder the two (red and yellow) cables (extended cable) to the centre connectors of the switch, then solder the red and yellow from one plug to red and yellow contacts on one end of the switch. Do the same with plug leads of the other plug. The Black leads do not require modifying.

To switch from one system to the other. Close down the one you are using, switch over and boot up the other one. Any data files which are common to both systems should be saved onto a USB  HDD which is formatted to Fat32 (so it is available to Windoze as well as GNU/Linux).

so from what i'm getting from this and other threads, there's really no "elegant", all-software way to switch between OS's that are installed on separate hard drives?
bummer. i have no problem restarting and going into the Bios and switching which disk to boot but i thought that could be simplified.
had i installed Ubuntu on the same disk as my current XP, i would get the screen to choose between OS's, right?

---

### Post by raevin on 2008-04-18
> **daniloj said:**
> so from what i'm getting from this and other threads, there's really no "elegant", all-software way to switch between OS's that are installed on separate hard drives?
bummer. i have no problem restarting and going into the Bios and switching which disk to boot but i thought that could be simplified.
had i installed Ubuntu on the same disk as my current XP, i would get the screen to choose between OS's, right?

Really, I don't know why people are making this harder than it is.  Use GRUB...when you install Ubuntu on a seperate hard drive, it'll automatically detect other partitions (Linux and non) you have on your system.  If, for some reason it doesn't...then there's guides on how to configure GRUB to boot into Windows...

---

