---
title: "Ubuntu won't boot anymore"
date: 2007-07-30
forum: General Help
---

### Post by Mark Phelps on 2007-07-30
Turned on my machine tonight and suddenly, Ubuntu 7.04 won't boot into the desktop anymore.

Get the splash screen, the progress bar, then the screen clears and I get the following messages:

*checking root file system
fsck 1.40-WIP (14-Nov-2006)
/dev/hdc1: clean

* checking file system
fsck 1.40-WIP (14-Nov-2006)

AT this point, I get a flashing cursor and the machine just sits. Nothing happens after that.

Have had fscks forced on me several times, the progress line proceeds quickly to 100%, screen clears, and desktop appears.  But this time, after 10 minutes, still nothing.  Did a ctl-alt-delete, started X, got a desktop, but my wallpaper was gone, as were my theme settings, and the partitions seem to have vanished!

Suspecting the worst, booted into Windows (this is a triple-boot machine), but that works OK.  No forced chkdsks from Windows.

I then tried rebooting Ubuntu using recovery mode, got lots more messages, but eventually ended up in the same situation.

So, anything I can do using the live CD? Or am I stuck having to reinstall Ubuntu from scratch?

---

### Post by phidia on 2007-07-30
> **Mark Phelps said:**
> 
                              -snip-
I then tried rebooting Ubuntu using recovery mode, got lots more messages, but eventually ended up in the same situation.

So, anything I can do using the live CD? Or am I stuck having to reinstall Ubuntu from scratch?


It may be helpful to the community here to know what those messages are.

Have you tried to run fsck on the root file system using the live cd?

You probably need to look at /var/log/syslog too.

Post  any relevant messages.

---

### Post by Mark Phelps on 2007-07-30
I'm new to this, so I have no idea how to capture those messages

... but what I have done is the following:

Rebooted using the System Recovery CD, started Gparted, saw it hang on scanning devices

Rebooted using the Live CD, started Gparted, saw it hang as well on scanning devices.

Opened terminal window, ran sudo disk fdisk -l, got the following:
Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1216     9767488+  83  Linux
/dev/hdc2            9722        9964     1951897+  82  Linux swap / Solaris
/dev/hdc3            1217        5471    34178287+  83  Linux
/dev/hdc4            5472        9721    34138125    b  W95 FAT32

Ran fsck -ry on /hdc1 -- got the reply it was clean
Ran rscf -ry on /hdc3 -- got the reply it was clean

Rebooted into Windows, ran chkdsk on the shared FAT32 volume -- found no errors

Rebooted into Ubuntu -- booted all the way up this time!!

So, my guess is that the fsck at boot time was getting hung up on hdc4 and the Windows chkdsk fixed that.

Question is, given that hdc4 is a fat32 volume, could I have fixed that using fsck?

---

